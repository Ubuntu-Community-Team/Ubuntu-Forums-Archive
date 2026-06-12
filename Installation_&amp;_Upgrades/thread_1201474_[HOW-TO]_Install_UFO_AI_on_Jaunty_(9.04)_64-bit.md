---
title: "[HOW-TO] Install UFO AI on Jaunty (9.04) 64-bit"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by arch0njw on 2009-07-01
I'm new at this how-to thing.  The basic process is simple.  If found that the "run" file from sourceforge was the best approach.  This doesn't install it as a package manager managed software, but it does let you put it somewhere convenient (like your home dir, or other location where you have space).

_**Download the installer**_.  At the time of writing this the installer was [FONT=Courier New]ufoai-2.2.1-linux.run[/FONT].

To install this, simply type "sh ufoai-2.2.1-linux.run" on the command line and it will launch the installer.  That part is very self descriptive.

Now for the hard part.  You need to get the game running!  This part is likely to vary system to system, so I am going to share the steps I used, but not the specific files.

_**Install "apt-file"**_, you will need it.  ([FONT=Courier New]sudo apt-get install apt-file[/FONT])

_**Run the [FONT=Courier New]ufoai[/FONT] command from the command line****.**_  Go to where you installed UFO AI and try to run the "ufoai" command.  If the game starts, you are having more luck than I did.  If you get what I got, it tells you that there is a missing library.  No fear, you can now look it up!

_**Lookup any missing libraries with apt-file.**_  Look up the library by typing the following:  [FONT=Courier New]sudo apt-file search *library-name*[/FONT]

You will be told to rebuild the cache.  Follow the instructions and then try searching for the file again.

_**Install packages to get missing libraries.**_  Now you know the packages in which this file is delivered.  Install them right here at the command line with [FONT=Courier New]sudo apt-get install *package-name-from-apt-file*[/FONT].

_**Wash, rinse, repeat.**_  Try running ufoai again.  Use apt-file to find any libraries that are missing and install the package that contains them.  Repeat that until ufoai runs.


That worked for me.  I look forward to other people's results.

---

