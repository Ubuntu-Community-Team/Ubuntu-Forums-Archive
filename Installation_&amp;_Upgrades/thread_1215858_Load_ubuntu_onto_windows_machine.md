---
title: "Load ubuntu onto windows machine"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by mparker1113 on 2009-07-17
Hello, i have a machine that is running windows xp. I would like to make that machine a linux server, and have acquired the ubuntu .iso file. I can open that file with software i have and treat it like a CD, but, none of the file types are recogninzed. 

What is the best way for me to load ubuntu onto that machine ?

(thank you for any input)

---

### Post by TheNosh on 2009-07-17
[COLOR="Red"]if you want to keep windows as well be sure to look into drive partitioning, if you pan to get rid of windows and install Ubuntu be sure to make any back ups you may need[/COLOR]

burn the iso to disk using imgburn, or nero or something.

leave the disk in the drive

restart the computer and it will boot from the disk into the installer

(if not you need to put disk first on the boot list in the BIOS)

---

### Post by Troy Martin on 2009-07-17
You'll need to write the .iso to a CD or DVD (whichever the .iso is for) and use it to boot the computer and install Ubuntu from within Ubuntu. As I recall, you can use GParted to shrink the XP partition and use the rest of the drive to install Linux. That way, you can (logically) use GRUB to dual-boot between Ubuntu and XP.

Anything anyone wants to add?

---

### Post by jerrardm09 on 2009-07-17
Get vmware and run it. much easier.

---

### Post by lisati on 2009-07-17
If you choose to put it on CD/DVD then this might help: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

