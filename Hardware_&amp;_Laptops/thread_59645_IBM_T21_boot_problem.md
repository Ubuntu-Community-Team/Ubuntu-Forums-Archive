---
title: "IBM T21 boot problem"
date: 2005-08-24
forum: Hardware &amp; Laptops
---

### Post by olZ on 2005-08-24
Hi! everyone ( : 

I have a IBM Think Pad T21 800 Mhz, 256 MB memory and so on... and running Win XP right now, but tried to install ubuntu 5.04, downloaded "Intel x86 install CD" from [www.ubuntulinux.org/](www.ubuntulinux.org/). Burned it to a cd and then configurated bios so it should boot up from the cd, but it don't ! and I have no clue why. I have tried to upgrade to bios version to 1.16 but it don't work. and there are no new bios upgrade on IBM.com. I don't know whats the problem, does linux have problem with laptops or ? 

If anyone have a anwser to my question please send me a mejl with the anwser.

and excuse me for my bad english.... peace !

---

### Post by Lambert on 2005-08-25
When you burned the cd did you do an image burn? Does it seem to take longer before HD starts to boot since you switched to boot from cd first? Just a guess but it sounds like it's looking for a boot image on the cd first, not finding one and moving to the secondary boot device which is probably your HD.

Linux is actually one of the better distros on laptops that I've found. Currently using on a TP A31.

---

### Post by wabble on 2005-08-27
[QUOTE=olZ]Hi! everyone ( : 

I have a IBM Think Pad T21 800 Mhz, 256 MB memory and so on... and running Win XP right now, but tried to install ubuntu 5.04, downloaded "Intel x86 install CD" from [www.ubuntulinux.org/](www.ubuntulinux.org/). Burned it to a cd and then configurated bios so it should boot up from the cd, but it don't ! and I have no clue why. I have tried to upgrade to bios version to 1.16 but it don't work. and there are no new bios upgrade on IBM.com. I don't know whats the problem, does linux have problem with laptops or ? 

If anyone have a anwser to my question please send me a mejl with the anwser.

and excuse me for my bad english.... peace ![/QUOTE]
 On my thinkpad x31i have to go to the boot list by pressing F12 on boot and select boot device usb. Maybe it's the same on your machine :)

---

