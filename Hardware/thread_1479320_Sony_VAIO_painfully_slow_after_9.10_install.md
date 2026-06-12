---
title: "Sony VAIO painfully slow after 9.10 install"
date: 2010-05-10
forum: Hardware
---

### Post by radguy2001 on 2010-05-10
SONY VAIO tower, PENTIUM III, 10GIG HD (clean), 256 RAM

Sony Vaio has two hard drives; 30G contains WinXP Home; other is empty 10G.  Loaded 9.10 CD into drive, changed BIOS to look first at the CD to boot then to 10G (future home of Ubuntu) to boot.  Rebooted Vaio.  Install asked if I wanted to use the entire drive for the Ubuntu partition; I replied Yes.  Install took awhile but started and completed without issue.  Removed CD and rebooted.  When Ubuntu started, it brought up a menu of five start options; the first being Ubuntu and the last was Windows XP Home (???).  Under XP Home, the response time of the tower was respectable; under Ubuntu it is painfully slow, none of my video formats (MPEG, AVI, WMV, etc.) will play and I cannot get my display to function under 1024x768 resolution.  I think I found a fix in this forum for the display.

Any thoughts at all about the rest?  I am a newbie and appreciate any and all help.  I am looking forward to a Windows-free computing existence.

Thanks !!!

---

### Post by khelben1979 on 2010-05-10
```
lspci
``` will reveal your hardware. Then we know if it's possible to install a faster graphics driver.

---

