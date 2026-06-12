---
title: "Ubuntu, XP, and OpenSuse"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by TechSteveMK on 2009-07-15
Hi all!

Welcome to my 1st post!

Wonder if you guys and gals can help me out...

I have just bought a laptop from ebay, with a 60GB hard drive, and Vista installed.

I would like to wipe/format the drive and install Ubuntu Studio (which I have used briefly on my desktop machine, and is excellent), OpenSuse, and WinXP.

I would also like a 'storage' type area on the drive, which is accessible from all 3 installations, so I dont have to reboot to gain access to files.

What's the best way to proceed? What software is good for formatting the drive, and how should I partition? I have had Opensuse and XP sitting on the same drive together quite happily. But I assume that after Ubuntu Studio is installed I would need to take a look at the boot menu to make all 3 installs work.

I'm quite a Linux noob, so go easy!

Many thanks for your help in advance.

Steve

---

### Post by x33a on 2009-07-15
try this:

1. 15 GB windows / NTFS
2. 10 GB opensuse (mount point = root)
3. 10-15 GB ubuntu studio (mount point =root)
 
rest you can format in ntfs (accessible through ntfs-3g) or fat32.

first install windows, then opensuse, then ubuntu.

ubuntu's bootloader (grub) will likely detect all three installations.

---

### Post by lisati on 2009-07-15
If your laptop didn't come with recovery disks, I'd recommend checking it to see if it came with software to create them, "just in case". I've heard of other forum users running into problems when taking their machines in for servicing, only to be told something along the lines of, "Sorry, but no, because you've changed your machine."

---

### Post by TechSteveMK on 2009-07-15
Thanks for that guys. 

No need to worry about servicing or warrante as its a used laptop.

I will install the os's in the order mentioned, but whats the best way\software to format and partition? Back in the day I would just do format C: , but now with Vista and stuff in the way Im sure its not that easy. 

I seem to remember that last time I installed studio, the setup program gave me the opurtunity to create partitions as i wanted before the install. Is it a good idea to boot from the ubuntu studio cd, format and partition as i want, then install xp, suse, studio?

Many thanks

Steve

---

### Post by x33a on 2009-07-15
use gparted, best in my opinion. it should be available on the live cd of ubuntu studio, or you can download gparted live cd:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

