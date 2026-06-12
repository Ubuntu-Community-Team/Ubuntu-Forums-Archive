---
title: "Newbie has question regarding UBUNTU installation…"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by bhanja_Trinanjan on 2009-07-07
Hi,
	My PC runs Vista 32 Bit on the primary HDD. My motherboard offers an option to select the boot drive at startup.

Can I install UBUNTU on a second hard drive without GRUB and use the motherboard BIOS menu to choose the boot disk?

Will UBUNTU harm the partitions on the primary Vista HDD in anyway if I choose NOT to install GRUB/any boot loader and fall back on the motherboard BIOS to choose which OS/HDD to boot?

---

### Post by jerrrys on 2009-07-07
good morning b_T...

if you wish to boot from bios, you can. ubuntu will still install grub to second hdd and will try to install mbr if it see's the primary hdd. most fool proof way to stop anything from going wrong is to disconnect primary hdd durning install (i have hot swap hdd and this is what i did). if your using the entire disk just use guided install in this configuration and it will install fine.  also do a test run without install to see if it going to work on your system first. anything else?

also here's a video for manual install

[http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)

---

### Post by bhanja_Trinanjan on 2009-07-07
> **jerrrys said:**
> good morning b_T...

if you wish to boot from bios, you can. ubuntu will still install grub to second hdd and will try to install mbr if it see's the primary hdd. most fool proof way to stop anything from going wrong is to disconnect primary hdd durning install (i have hot swap hdd and this is what i did). if your using the entire disk just use guided install in this configuration and it will install fine.  also do a test run without install to see if it going to work on your system first. anything else?

also here's a video for manual install

[http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)

Thanks for the tip!

:D

---

