===========================================
-------

SourceCode:

    using System;
    using Ntreev.Library;
	using System.Collections.Generic;

    namespace Example
    {
        class Program
        {
            static void Main()
            {
                Options options = new Options();
                CommandLineParser parser = new CommandLineParser();

                if (parser.TryParse(Environment.CommandLine, options) == false)
                {
                    parser.PrintUsage();
                    Environment.Exit(1);
                }
                Environment.Exit(0);
            }

            class Options
            {
                public bool Toggle { get; set; }
                [Switch("i")]
                public int Index { get; set; }
                public string Text { get; set; }
				public List<int> Numbers { get; set; }
            }
        }
    }

You can call like this:

    C:\>Example.exe /Toggle /Index 3 /Text "this is text" /Numbers "1,2,3,4,5"
    or
    C:\>Example.exe /i 3