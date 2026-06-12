---
title: "HP scanjet 3770 - strange problem with gutsy"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by yonixw on 2007-10-21
~Yeah my grammar sucks.
_________________________
Hi .

Just yesterday i installed Ubuntu 7.10 (gutsy)
Let just leave the part when i say this OS is ***** amazing.

So ... ubuntu detected my HP LaserJet printer and everything was fine.

But with my scanner i had little less luck, i searched this forum and found [this Guide]("http://ubuntuforums.org/showthread.php?t=416136")
from SmileOne

I followed the instruction and in the end when Xsane was supposed to detect my Scanner i got an error "No devices available".

I tried couple of times and gave up. (Wait ! this is not the end of the story !)

Because i'm new in linux i wanted a memory of Windows, therefor i installed VMware Player
on my system and made a virtual machine for my Windows XP Professional.
Well ... everything went good but suddenly i see in the device list that i can "transfer" to the virtual windows -> "HP ScanJet 3770"

So! i enabled it and installed my driver on the Virtual Windows and Walla~ The scanner
Works !!!

Now, the logic says that Linux "transfering" the Scanner to the virtual Machine, wich mean that linux recognize the scanner , so why Xsane doesnt work ???

_____________________
This may help ... when i type "sane-find-scanner" i get :
```

found USB scanner (vendor=0x03f0 [hewlett packard], product=0x2505 [hp scanjet]) at libusb:003:003
```
_____________________

Help ?:confused:

---

### Post by smileone on 2007-12-10
Hi,
this problem is well-know, because hp3770 driver doesn't work with the latest version of libsane package.
I think If you downgrade libsane and block its upgrade, you will work with your scanner.
If you want block package follow[URL="http://ubuntuforums.org/showthread.php?t=534734"] this 
http://ubuntuforums.org/showthread.php?t=534734[/URL]
:)

---

### Post by NeoNIG on 2008-06-30
> **smileone said:**
> Hi,
this problem is well-know, because hp3770 driver doesn't work with the latest version of libsane package.
I think If you downgrade libsane and block its upgrade, you will work with your scanner.
If you want block package follow[URL="http://ubuntuforums.org/showthread.php?t=534734"] this 
http://ubuntuforums.org/showthread.php?t=534734[/URL]
:)
This explanation is wrong. I use hp3770 under SUSE 11.0 and version of libsane 1.0.19 is the same as in Ubuntu 8.04.

---

