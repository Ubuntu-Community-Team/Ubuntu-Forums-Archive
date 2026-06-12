---
title: "install Brother MFC-J430W Printer"
date: 2012-06-07
forum: Hardware
---

### Post by Richard McDonald on 2012-06-07
Hello,
2 1/2 months ago I bought a new Brother MFC-J430W printer because my other printer (a Cannon) did not work with Ubuntu.
I am using Ubuntu 12.04, but have not successfully set up the printer. The computer recognizes the printer, but I have been too confused about what to install or how to do it to install the drivers.
I have written to Brother, Ubuntu Forum and friends who have brother printers- no one answers my questions.
Has any one out there installed this printer?  I am sure it is rather simple, but the Brother Driver pages on their web site are grossly confusing to me.
Any help would be greatly appreciated
Thank you,
Richard McDonald

---

### Post by krolita on 2012-08-03
I have the same problem.  Any help?

---

### Post by gifford on 2012-08-03
Are you going to use it as a wireless networked printer or attached to your pc?

The first thing is to download appropriate drivers, again this will depend on how you want to set it up. Are you using Ubuntu 12.04 64 or 32 bit?

---

### Post by kurt18947 on 2012-08-03
I find installing the printer portion quite easy.  Brother makes this script available which takes care of the 32 bit/64 bit concern:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)
  I'll attach the installer script from Brother's web site.  Just extract it somewhere you can find it again and run it as instructed in the above link. [ATTACH]222220[/ATTACH].  

Installing the scanner is a little bit more of a pain.  There are two issues with the scanner.

[LIST]
[*]It requires editing a file for normal users (not sudo users) to be able to scan
[*]The installer puts some files where they don't belong
[/LIST]
Also, to use the scanner over a network requires making the scanner known to the system via a command line command.

Why does Brother use command line installation instead of a nice GUI?  I had the same question.  I asked here and the reply made perfect sense.  CLI works the same in all distros and all versions.

---

### Post by izquierdista on 2012-08-09
Ok I got the printer to work using these instructions on the brother official website:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

I installed the drivers using Gdebi 

now printing works great :)

now how do I get the scanner to work?

---

### Post by pdc on 2012-08-11
> now how do I get the scanner to work? 

kurt, god bless his soul, did give you instructions in the post above yours;

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

there is Download scanner driver; 

then further down are instructions

You can see: Instructions; and Scanner

and a button for Driver install;

click on this and you get screenshot 2 (also called brother_scanner_2)

they appear to recommend 

> sudo gedit /lib/udev/rules.d/40-libsane.rules

and that will open the file /lib/udev/rules.d/40-libsane.rules for you to edit;

Brother recommend you paste

> # Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

into this file: they say:

> Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


SAVE your additions; Close; re-start the computer;

---

### Post by izquierdista on 2012-08-11
Thanks everyone those instructions.

I managed to install the Brother DCP-7065ND printer and scanner for USB connection and its working perfectly now using some of the instructions above here is the link to the thread the whole setup is the last post:

[http://ubuntuforums.org/showthread.php?t=2039840](http://ubuntuforums.org/showthread.php?t=2039840)

---

### Post by Klasanov on 2012-09-29
I removed a bunch of CUPS drivers in synaptic. but sudo dpkg -l | grep Brother is still telling me that I have

rc  brscan                                   0.2.4                                      Brother CUPS Printer Definitions


How do I remove that?

---

### Post by pdc on 2012-09-29
I guess if you tell folks a little more of your story..

.......as to what you are doing.........

...not sure that 

> brscan 0.2.4 Brother CUPS Printer Definitions

is enough of a monster that it needs removing........

.some would use the SEARCH function to find where the file is;

then either use the GUI or CLI to delete it.......

---

### Post by Craigubunt on 2012-10-31
I have tried downloading printer drivers but am confused about what to do with the (linux-brprinter-installer-1.0.4-1.gz, ver.1.0.4-1, 14 KB) download now. I opened the terminal window and pasted the correct comands but nothing happens.
What am i doing wrong.
I am new using ubuntu 12.04 

Any help would be nice.
Thanks

---

### Post by pdc on 2012-10-31
Craig from Western Washington;

you would be best to start a new thread:

....... easier to focus on you then;

tell us the model number of your printer; 

............but perhaps look at this

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr)

Brother provide an installer that [COLOR="Red"]**should do everything for you**[/COLOR] ...

........try it..................

---

### Post by jimbop99 on 2012-12-03
I just wanted to thank kurt18947 for posting the link to install brother printers with a script. Man that was a lot easier than the first time I did it.

---

