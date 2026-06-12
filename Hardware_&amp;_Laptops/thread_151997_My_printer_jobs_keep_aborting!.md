---
title: "My printer jobs keep aborting!"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by Cyorxamp on 2006-03-29
Lo,

I own a new Lexmark I3 and I have followed the following guide for how to use lexmark printers on linux...
[http://users.netwit.net.au/~pursang/lex.html](http://users.netwit.net.au/~pursang/lex.html)

The only things I did differently with this guide was make symlinks from libtcl and libtk version 8.0 instead of the ones mentioned.  I also had to use alien to convert the rpm files to deb to use on Ubuntu.

I then went on the CUPS web page at port 613 and could see it detected my lexmark I3 on the USB port and also I could see the Z600 driver I just installed.

The only thing is, when I send a job to the printer (i have tried from many programs including the 'lp' command) it stays as 'processing' for a few seconds then goes to 'aborted' - When I click the 'reprint' button I get the 'client-error-not-possible' error.

I did notice there is a page about this error on the cups.org site but I followed the things mentioned and it did not seem to help.

I have set my LogLevel to debug2 and the output from the error_log can be found at [http://cyorxamp.info/error_log.txt](http://cyorxamp.info/error_log.txt) if it will help anyone in understanding what could be wrong with my set-up.

Unfortunately if I can not get my new printer working on this system (which acts as my server) then my 2 months hard work in understanding linux will have gone to waste as I will be forced to go back to Windows :(

I hope someone can help me!

Steven Maddox
[email]s.maddox@cyorxamp.info[/email]

---

### Post by mpvano on 2006-03-29
According to your log files, you have installed software to drive your printer that is not compatible with the Ubuntu system you are using.

You cannot take software from one unix/linux system and assume that installing it on one that is constructed using different parts will work.

Specifically, all modern operating systems use components (like your printer driver) that assume the presence of compatible "libraries" of common code that do much of the low level work of the component. These are so common that they are NOT included in the programs when they are are created - the developer assumes that the "system libraries" are correct for the version of the software that they are creating.

Unfortunately, there are "generations" of system libraries. They are usually delineated by the version of the Language compilers (typically the C compiler) used to generate the object files from the source code. Typically a new major release of an operating system is done when the C compiler changes enough to mean that the "system shared libraries" are now incompatible with existing programs. This means that nearly ALL the component pieces need to be rebuilt to be compatible with the new libraries.

Most OS releases make arrangements to support older programs by allowing the use of obsolete libraries and provide a way to install programs so that they will use the OLDER libraries instead of the current ones. The mechanism that makes this work is the "package" system that is used to install programs. Packaging systems like RPM and DPKG contain the information to match the requirements with the available parts and see that they are all there.

Unfortunately, you are trying to install parts with a different packaging system (RPM) into  an ubuntu system which uses the Debian packaging system.

If you really know what you are doing, you can typically use special tools (as you say you did) to make one package type into another, but unfortunately this process often fails to account for pieces that are missing in one system or the other.

That's what happened here. Some portion of your printing package uses older (version 5) libraries, instead of the current version 6 libraries. The error message describes a program failing to start because one such library is not present. It's probably just the tip of the iceberg - if you fix this missing library, you'll probably find you are now failing on another, until you catch them all.

In some cases, all you need to do is manually install the missing old libraries (which are normally automatically installed when the debian package indicates that they are needed - information that may be missing in an RPM file for another distribution).

You can try installing "libc5" using apt-get or synaptics. That MAY fix the problem shown in your log file if the program in question knows how to find the correct library - conventions for doing this sometimes vary betwen linux systems.

Unfortunately, it's very possible that the missing "libc5" is itself being used elsewhere by another missing library, etc. These chains of libraries and components that rely on each other are called "dependencies" and many of them may be involved in a complex package like one supporting a printer.

Try examining the details of what's been installed by your alien-converted package (I presume that's how you installed it) by using the synaptics "properties"  menu that pops up from the right mouse button when you point to a package. That will get you started tracing the missing dependencies....

Sorry, it's more than you probably wanted to know, and there may not be a simple answer to your problem if you couldn't troubleshoot it yourself from the log error message explaining that the version 5 library was missing. Installing libc5 probably wouldn't hurt however.

In my opinion, the correct answer is to toss the problem back into the lap of the people you got the package from and ask them what you need to make it work on a different linux distribution.

Mario

---

### Post by Cyorxamp on 2006-03-29
The day linux can use non-crucial Windows Drivers using some sort of wrapper similar to ndiswrapper for things like printers I will come back.

Until then... I have to leave, sorry.

I will monitor this thread but I have spent too many long nights working on silly hardware issues such as these, it's 8am now :S

Back to Windows...

---

### Post by Cyorxamp on 2006-03-29
Every time I choose to give up Linux, no matter what I do within hours I have also given up on giving up and I go back to the problem... suffice to say I have gotten a few more results this time...

Basically, I did the following things...

a) Installed these packages... gs, gs-esp, cupsys, printconf, alien, and libstdc++5
b) Obtained the Linux drivers from Lexmark (again) and extracted them
c) Ran 'tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz' and extracted 'install.tar.gz'
d) Ran 'alien *.rpm' and ran 'dpkg -i' on the resultant files
e) Ran 'ldconfig'
f) Ran '/usr/lib/cups/backend/z600'
g) Set up CUPS using the interface as I did before

This time I get different results!
Basically if I do a 'test page' or print using 'lp' the job shows as 'processing' and after about a minute the printers head moves a bit (basically my printer decides to twitch :S) then CUPS thinks the job has completed.

However when printing from GQView (a picture viewer) it seems to class it as 'aborted' like before after a while.

I got the material for 'what to do' from this link - [http://72.14.203.104/search?q=cache:B9rQlJy-SjIJ:blog.dingletec.com/%3Fp%3D13+debian+lexmark+z600&hl=en&gl=uk&ct=clnk&cd=1](http://72.14.203.104/search?q=cache:B9rQlJy-SjIJ:blog.dingletec.com/%3Fp%3D13+debian+lexmark+z600&hl=en&gl=uk&ct=clnk&cd=1)

Please note that when I did f) on my list of things I did... the command did not return anything (dispite what that link saying it should)

I believe I am getting closer, if anyone can point me in the right direction I would be eternally grateful!

---

### Post by mpvano on 2006-03-29
That's the spirit!

(But I do agree that the binary drivers issue is definitely turning into a show-stopper...)

Please supply your latest log file excerpts from this round of experiments. I don't have that kind of printer, but I'll look at the files for something else obvious and maybe somebody else can jump in here as well...

Mario

---

### Post by Cyorxamp on 2006-03-29
[http://cyorxamp.info/error_log](http://cyorxamp.info/error_log)
[http://cyorxamp.info/cupsd.conf](http://cyorxamp.info/cupsd.conf)
[http://cyorxamp.info/printers.conf](http://cyorxamp.info/printers.conf)

---

### Post by mpvano on 2006-03-29
Sorry, I can't help at this point - there are no longer any errors being reported in the log file.

Have you tried shutting everything down and then powering things back up and trying it now? 

Perhaps someone else can help at this point.

Mario

---

### Post by Smakfull on 2006-04-02
[QUOTE=mpvano]According to your log files, you have installed software to drive your printer that is not compatible with the Ubuntu system you are using... [etc][/QUOTE]
Oooh! Thank you! Thankyouthankyouthankyou! You've given me the solution to a problem I've been sitting with for weeks! Oh, is this pure love I feel?! The Bliss! The Happiness! What to do!?

*jumping around in circles*

I LOVE YOU! :D 

*hug hug hug*

Are you available? ;)

---

### Post by Cyorxamp on 2006-04-02
Thats absolutely wonderful, at least this page is not relegated to the 7th or 8th page now.  Come on folks... if you know anything that can help me please tell me!

---

