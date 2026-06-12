---
title: "HP Scanjet 5000 SANE setup"
date: 2011-10-05
forum: Hardware
---

### Post by y2pk001 on 2011-10-05
Hi All

Has anybody had any experience with a HP Scanjet 5000 (auto feeder scanner)
SANE doesn't seem to recognize it, can I manually set it up?


the is my sane-find-scanner


found USB scanner (vendor=0x03f0 [Language Error], product=0x2e05 [Language Error]) at libusb:001:014


Please?? Any ideas??

Cheers

---

### Post by nomko on 2011-10-05
According to the site of SANE, your device is not supported: [http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD). It is not mentioned in the list. What you migth need is a ppscsi driver. 
 
Which version of Ubuntu you're using now?

---

### Post by y2pk001 on 2011-10-05
Hi Nomko

Thanks for the reply, I am running Ubuntu 10.04. I removed the SANE .deb and compiled the newest version from the SANE website still no joy. Here is my lsusb

Bus 002 Device 004: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 003: ID 04f2:0111 Chicony Electronics Co., Ltd KU-9908 Keyboard
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 017: ID 18d1:4e21  
Bus 001 Device 014: ID 03f0:2e05 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I can see it sitting there at Device 014

ppscsi?? what do I need to do? can you refer me to a link?

Cheers
__

---

### Post by nomko on 2011-10-06
> **y2pk001 said:**
> Hi Nomko
 
Thanks for the reply, I am running Ubuntu 10.04. I removed the SANE .deb and compiled the newest version from the SANE website still no joy. 
As long SANE doesn't support your device, you can compile all the latest SANE drivers, it won't help. Not supported means not supported
 
 
 
> 
I can see it sitting there at Device 014

Yes, Ubuntu sees your printer, but doesn't recognizes it as such.
 
> 
ppscsi?? what do I need to do? can you refer me to a link?

 
There has been a topic on this forum already, but this was for the Scanjet 5100. The link: [http://ubuntuforums.org/showthread.php?t=1588417](http://ubuntuforums.org/showthread.php?t=1588417) but i can be very helpfull to you. And this link can help you: [http://ubuntuforums.org/showthread.php?t=782242&page=7](http://ubuntuforums.org/showthread.php?t=782242&page=7) . In the last link there's a link to some blog. But read carefully all the topics. Another link: [http://ubuntuforums.org/showthread.php?t=1588417&highlight=ppscsi](http://ubuntuforums.org/showthread.php?t=1588417&highlight=ppscsi)
 
And if you google on ppscsi you get this: [http://www.google.nl/search?q=ppscsi+ubuntu&hl=nl&prmd=ivns&ei=oT6NTvHQCM2z8QPs87Qp&start=0&sa=N](http://www.google.nl/search?q=ppscsi+ubuntu&hl=nl&prmd=ivns&ei=oT6NTvHQCM2z8QPs87Qp&start=0&sa=N)  I know it's a lot to read and to go through, but you will find the solution here.

---

### Post by y2pk001 on 2011-10-06
Thanks Nomko

The problem is the Scanjet 5100 and Scanjet 5000 are two very different scanners. I have been fighting with the problem all day .....time to give up. I was hoping to make this office a Microsoft Free Zone but it looks like that dream is going to have to wait. :(

I have set the scanner up on an XP machine

Thanks for the help

---

