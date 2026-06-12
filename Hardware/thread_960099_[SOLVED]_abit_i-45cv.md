---
title: "[SOLVED] abit i-45cv"
date: 2008-10-27
forum: Hardware
---

### Post by michelepolo on 2008-10-27
hello, i own a motherboard abit i-45cv and cannot install any linux at all! i am a pretty experienced one, started from red hat 6.0.
i tried with ubuntu 8.04, knoppix 5.1, opensuse 11 either live or alternate installation and they all hang at the very beginning of installation: udev probing for knoppix, more or less same stage for ubuntu, i have to cold reboot.

this is what happens with knoppix 
[IMG][[IMG]http://img522.imageshack.us/img522/5575/koppix51bb0.th.jpg[/IMG]](http://img522.imageshack.us/my.php?image=koppix51bb0.jpg)[/IMG]

what with ubuntu 
[IMG][[IMG]http://img84.imageshack.us/img84/9315/ubuntu804uz2.th.jpg[/IMG]](http://img84.imageshack.us/my.php?image=ubuntu804uz2.jpg)[[IMG]http://img84.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)[/IMG]

and this is with dynebolic (great jaromil!) 2.4.2:
[IMG][[IMG]http://img143.imageshack.us/img143/5027/dynebolic242rv4.th.jpg[/IMG]](http://img143.imageshack.us/my.php?image=dynebolic242rv4.jpg)[[IMG]http://img143.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)[/IMG]


i searched for my motherboard and nobody seems have my problems, and i know abit is (or was) almost linux compatible. any help please?
:confused:
very :confused:

---

### Post by michelepolo on 2008-11-11
SOLVED! i'm actually writing from my gOS - ubuntu with everything going smoothly, except for xp! what i did:
in the bios
-i changed from sata 1 to sata 4
-i excluded internal video card
-i used a normal -non usb - keyboard (actually the system booted the same)
and every flavour of linux finally started to boot, thanks for every answer you gave me.
as a user told me xp now refuses to start, even if i put back sata and bios, just for test, but at the moment i don't care

---

