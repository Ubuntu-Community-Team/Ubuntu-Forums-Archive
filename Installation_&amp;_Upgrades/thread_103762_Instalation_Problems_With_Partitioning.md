---
title: "Instalation Problems With Partitioning"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by Kid Avatar on 2005-12-14
Ok im in the process of installing on the other computer.

Im at the partioning part. my sony computer has two harddrives a c and d drive. I want to use a percentage of the D drive for ubuntu and also i want to dual boot windows and ubuntu

how do i do this?

my system is using NTFS 

the d drive has 60 gb of space and i want to use half for ubuntu and the rest for windows which includes the c drive..

---

### Post by Kid Avatar on 2005-12-14
im new to ubuntu by the way

---

### Post by Herman on 2005-12-14
I haven't yet had any first-hand experience with more than one hard-disk myself, but see if one of the three illustrated example installs (single disk) in my signature link will help you. I guess it must be okay for people with more than one disk, I don't see anyone complaining, so I guess they manage somehow. Let me know if I need to make a new example sometime for those with multiple disks.  :D  (Herman)

---

### Post by Kid Avatar on 2005-12-14
it says file route not found at the end? i have no idea what that means im using ntfs by the way:confused: :confused: :(

---

### Post by gerrit stok on 2005-12-14
Hello,

I expect you to have two things ready:
-a working xp/2000 installation
-partition magic or something like that. I've experience with part. magic,so my answer is based on that program.

First of all make space for your ubuntu-linux. Is there only one drive divided in two
choose d:
At first,in windows,make two diskettes with partition magic(rescue disks)!!Don't forget.
Make a primary partition on d: (>5 giga ) and make it active
No format necessary
Put in the ubuntu cd and restart computer;cd start in bios=first
Ubuntu starts,follow screen. Ubuntu lists the partitions;choose the free space
on hda1. Accept.
At the end Grub is loaded. Grub installs in the mbr and destroys the windows bootloader. Before destroying Ubuntu marks the other os.Accept your os.
Ubuntu makes an upgrade via Internet. Accept.
Finishing all this restart your computer and scroll in Grub to Windows.
Does it start:congratulations and celebrations.
Don't:insert the diskettes and make the c: partition active.

Not convinced:use the live-cd
Not pleased:buy a cheap spare hard drive,put it in the place of your original harddrive,install Linux on that drive and change whenever you like.
I'm writing this on a laptop Hpnx 9010/40gb divided in three,ntfs,fat32 and linux.
I learned Linux on a spare drive.

Have luck

---

### Post by aysiu on 2005-12-14
Don't you have another thread on this?
[http://www.ubuntuforums.org/showthread.php?t=103759](http://www.ubuntuforums.org/showthread.php?t=103759)

---

