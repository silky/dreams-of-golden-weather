$LOAD_PATH << __dir__ + "/lib"

require "dreams_of_golden_weather"

task :generate do
  book = Book.new
  book.generate
end

task :plan do
  narrative = Narrative.new
  p narrative.plan
end

task :action do
  context = StoryEntities.map
  puts NarrativeActions.generate(:print_spool_mayhem, context).text
end

task :dither do
  img = DitheredImage.new("./content/images/900px-Auckland_Medical_School_Brutalist_II.png")
  img.dither
end

namespace :corpora do
  task :extract do
    extractor = ExtractCorpora.new
    extractor.extract
  end

  task :clean do
    cleaner = CleanCorpora.new
    cleaner.clean
  end

  task :process do
    Dir["./data/clean/*.txt"].each do |file|
      sh "python bin/ner.py #{file}"
    end
  end

  task :counts do
    counter = CountEntities.new
    counter.count
  end
end
