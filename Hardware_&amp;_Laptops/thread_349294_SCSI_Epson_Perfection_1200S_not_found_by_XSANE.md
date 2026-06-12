---
title: "SCSI Epson Perfection 1200S not found by XSANE"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by rphelps on 2007-01-30
I have a SCSI Epson Perfection 1200S that at one time worked with SUSE 9.1. XSANE is not able to detect it with Ubuntu 6.06. This scanner is completly supported by XSANE. 

With Suse 9.1 the scanner slowly quit working and got to the point it quit working all together.  I suspect a hardware problem. 

Has anyone else had trouble with this type of scanner with Ubuntu 6.06?

Should I invest in a new SCSI card on the off chance the card is bad?

---

### Post by RocketRog on 2007-03-16
I just set up the same scanner. There were no problems but I had to read a little about xsane.

First problem was that the scanner was not found in user mode. I had to run sane-find-scanner as root:> sudo sane-find-scanner
That showed that the scanner was on /dev/sg0. Per [this page]("http://www.halley.cc/ed/linux/howto/sane.html") I gave myself permissions to use the device > sudo chmod a+rw /dev/sg0Reading on the page instructs you to check /etc/sane.d/dll.conf and epson.conf. Both of mine were fine and I did not change anything.

Second problem was this stupid permissions file problem on quitting xsane. Lots of posts about it, but no real solution. I finally made the preferences file world-writable which solved the problem, but not very elegantly. From my home> sudo chmod 777 .sane/xsane/*

This assumes you have the bits and pieces loaded: sane, xsane, the gimp plug-in... you probably do, because your post implies that you know what you are doing.

I also read this thread> [http://www.ubuntuforums.org/showthread.php?t=316961](http://www.ubuntuforums.org/showthread.php?t=316961)

---

