---
title: "[SOLVED] Several Issues- new install"
date: 2008-11-08
forum: General Help
---

### Post by Rubicon421 on 2008-11-08
First let me quickly say that I am a complete nOObie when it comes to anything not Windows. I know quite a bit about computers though so please don't let my lack of Linux knowledge lead you to believe that I am retarded. 
So I just installed Ubuntu (64 bit) from a live CD on a home built machine running Vista Ultimate 64 Bit. So far I am really impressed with it and wish I would have tried it sooner. However, these are the problems I am running into:

The install process was a little rough. It took several attempts and I ended up having to create the partition in Windows because the Ubuntu install program kept encountering an error. Now, when rebooting I get the expected menu to choose which OS (couple modes of Ubuntu then Windows) followed by another menu when I choose windows. The next time it has Windows as the defualt choice followed by Ubuntu twice. I know this has something to do with the failed install prior to partition that left something on the C: drive and the good install on E:, but why the second menu anyway? I already picked Windows the first time.

Second, my logitech keyboard and mouse have several extra programmable buttons that I can not assign actions to in the mouse settings of Ubuntu. Where can I get a program/driver so I can use them?

Third, I've installed Compiz and now have the Compiz config program in the system drop-down menu. I have all the options for the cool 3D effects I want selected but I don't see any of them working. I still get the ripple effect when dragging windows but I had that before Compiz.

Thank you in advance to all that take the time to read this and help out a noob. And one more thing: What would you say is the coolest thing you learned you could do in Linux and not Windows when you first switched? I know about all the stability and virus stuff- but that's more along the lines of doing the same thing better, not doing something new. Just curious as to what all this OS can do.

Thanks again to all you Ubuntu gurus and good luck to my fellow noobs!

---

### Post by spiderbatdad on 2008-11-08
don't fully understand the nature of your installation. Does this mean you did a wubi install?
What errors did you encounter while trying to install? Did you try any boot options from the startup screen by selecting F6 and replacing "quiet splash" with say, "all_generic_ide"?

---

### Post by Rubicon421 on 2008-11-08
I know at least one of the attempts was a wubi install (sorry I'm really new to this). I downloaded the install file that installs Ubuntu while in Windows and also downloaded and burned a live CD. I finally got it to work off the CD. 
I had a exit code 10 error when trying to configure the timezone. I don't remember the other errors but they were when the install was attempting to partition the C: drive.  And, no I didn't try any boot options. 
Anyway, what I'm trying to figure out is why after choosing Windows from the first boot menu do I get another menu with Windows and two instances of Ubuntu. I don't even need the second menu and I really don't need the option to try to boot the failed install on the C: drive. I deleted the Ubuntu folder on the C: drive but some boot file still has a record of it and thinks I have two Ubuntu OSs installed and Windows.

---

### Post by mdurham on 2008-11-08
It sounds like the first attempted installs were wubi followed by a 'proper' install to it's own partition. I think you can edit the Windows boot menu from within Windows and remove the two references to Ubuntu, then it should boot straight into Windows from Grub. But you might also have a large file or two in Windows from the attempted wubi installs.
I've never done a wubi so don't know what to look for.
Cheers, Mike

---

### Post by Rubicon421 on 2008-11-08
I've never messed with editing the boot menu before but I thought it was something like that. Whatever file stores all the boot settings has new entries that need to be restored.

---

