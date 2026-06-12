---
title: "To Reinstall or What?"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by c5vetter on 2009-09-22
okay, relative newb to Ubuntu - installed 9.0.4 using Wubi - from the get-go, I had problems with sound - tried all of the suggested changes and still no sound

have been told some of the files did not install properly - have been advised to do a "reload" from a LiveCD - just received a CD from Canonical today

so, ready to do the install, but had a question or two - will using Synaptics Save Markings save everything?

by everything, will it save PROFILE SETTINGS, the CUPS settings for printers; wireless settings; Thunderbird settings, such as Address Book

bottom line - I need to be able to save all of my current settings - is this possible? know that for instance within XP, I can reinstall certain parts of the OS, without affecting anything else - so, is that possible in Ubuntu?

---

### Post by mikewhatever on 2009-09-22
Reinstalling Ubuntu will format the system partition and wipe all your settings and files, unless you have a dedicated home partition.
I'd strongly advise backing up all you need.

---

### Post by raymondh on 2009-09-22
+1 on backing up.

Another option is to migrate to a real partition using the [wubiguide]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?") as a reference.

Good luck.

EDIT : I still prefer a fresh install ... as it give me the option to create/separate the /home (for future saves)

---

### Post by c5vetter on 2009-09-22
otay - again, relative newb here to Ubuntu, so need some step-by-step process - how do I back up everything in Ubuntu???? WubiGuide - what is that?

understand about "fresh install", but I don't want to lose all my BOOKMARKS in Firefox and my ADDRESS BOOK in Thunderbird - everything else, I guess I could recreate, such as my wireless setup; my CUPS setup for my multiple printers, etc.

---

### Post by raymondh on 2009-09-22
> **c5vetter said:**
> otay - again, relative newb here to Ubuntu, so need some step-by-step process - how do I back up everything in Ubuntu???? WubiGuide - what is that?


Re : wubiguide

On my previous post, the word "wubiguide" (underlined) is a link to the actual Ubuntu Wubi Guide.  In it, it shows the possibility of migrating your WUBI-installed Ubuntu to a real partition.  Also, here is a how-to from the forum:

[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

Re : Back-up

To back up your files, you can either

1.  Copy & paste or drag your files from its' location to an external HD or flash drive 
2.  Use a program called rsync + grsync  (grsync is the GUI  or graphical interface).  These programs can be found in synaptic (system > administration)
3.  Use the terminal

These are the options I can think of ... migrating or re-install.  Of course, when you re-install, you will have to (somewhere along) also remove the wubi-installed Ubuntu.  Again, the steps to do so are in the wubi-guide.

- Back-up your personal files someplace else
- Read the How-to and decide from there.

---

### Post by c5vetter on 2009-09-22
otay - am going to throw a real newb question from left-field out - since WUBI installed Ubuntu as a virtual drive within Windows and I can then delete that within ADD/REMOVE programs.............then is the following possible

Just leave the virtual drive within Windows alone - run LiveCD and let it do it's thing by doing a dual-boot on the hard drive - assume partition will be set up when I select install - then I can move, transfer or whatever all the files within the virtual drive under Windows

does this question and thought process make sense??????

---

### Post by kh1116 on 2009-09-22
I think I get what you're saying, I'm not sure if Wubi installs the same way as a fresh install, but if the files are laid out the same way as a fresh install of Ubuntu (/home/) when viewing the hdd on the livecd, I dont think it would be a problem.

Edit: you would probably want to move files from windows using ubuntu, windows isnt capable of viewing ext3 out of the box

---

