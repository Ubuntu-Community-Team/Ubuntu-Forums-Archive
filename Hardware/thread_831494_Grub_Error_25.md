---
title: "Grub Error 25"
date: 2008-06-16
forum: Hardware
---

### Post by carlolovearianne on 2008-06-16
My laptop just ceased to boot into Hardy. Grub shows Error 25. Tried booting from the Hardy live cd (I tried both the ..."without changing your computer" and "Install Ubuntu" options) and got a "Buffer I/O error on boot device sda1, logical block 11..."  Same thing with the Gutsy  live cd.


I also tried using the old Edubuntu 7.10 which has the "Rescue A Broken System" feature but after "detecting hardware" I got stuck with a blue screen.


Everything was working fine prior to this. Just played a Frozen Bubble LAN game with my wife, got bored and was listening to The Rolling Stones' Sticky Fingers in Rhythmbox when Hardy just froze.   Mouse clicks and Ctrl + Alt + F1 was not responding so I did a hard reset and as mentioned above Grub shows Error 25.

Anyway I can still boot back into the system? Could this be a hardrive problem? Or did my hardrive just died?

---

### Post by phidia on 2008-06-17
> 25 : Disk read error
    This error is returned if there is a disk read error when trying to probe or read data from a particular disk.

From [this site]("http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html"), and yes that could mean hard drive failure. You might want to get a copy of [System Rescue CD]("http://www.sysresccd.org/Main_Page") and try with that.

---

