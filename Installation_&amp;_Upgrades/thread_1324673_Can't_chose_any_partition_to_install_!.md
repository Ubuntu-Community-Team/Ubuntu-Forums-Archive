---
title: "Can't chose any partition to install !"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by redbear on 2009-11-12
Linux kernel 2.6.31 conflict with chipset P43 (Asus P5QL PRO) ?

I used ubuntu from 7.04 - 9.04, installed very easily and had no problem.

Yesterday, I tried installing ubuntu 9.10 but installer could not find any partition even though liveCD still mounted well.

I try to install with other distro use kernel 2.6.31 as mandriva 2010, opensuse 11.2 ... and have the same problem ! installer could not find any partition !

[IMG]http://i405.photobucket.com/albums/pp135/rubymask/Screenshot.png[/IMG]

[IMG]http://i405.photobucket.com/albums/pp135/rubymask/Screenshot-1.png[/IMG]

Plz help me ! Thank you !

---

### Post by Ginsu543 on 2009-11-12
I'm not sure if this will help but you could try it:

1) Boot into live session using the live CD (without installing)
2) Open Terminal and run "sudo apt-get remove dmraid" (without quotes)
3) Close Terminal and run the installer by double-clicking on its icon

I too initially had trouble installing Karmic because the installer would not recognize my SATA drives. In my case the problem was that the installer refused to recognize drives that had previously been in a RAID array (even though RAID was not even turned on in BIOS). Doing the above allowed the installer to bring up all my drives.

---

