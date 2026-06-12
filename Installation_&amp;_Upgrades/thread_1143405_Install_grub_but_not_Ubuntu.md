---
title: "Install grub but not Ubuntu"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by RealG187 on 2009-04-29
Okay first I need to give a breif history of my machine's setup.

I installed Windows XP to a 120 GB Maxtor hard drive (I think it was set as Master). Next I installed a 10/20 GB hard drive (I think it was 10 or 20 GB) and set it as the master, moving the 120 GB to slave, or I might have made it primary master and the Maxtor one Secondary Master (and the CD-ROM drive Secondary Slave, but either way IDE0 was this drive and the Maxtor one wasn't.

I installed Ubuntu to this hard drive and when it installed GRUB it added my Windows XP to the list.

Now I want to swap out this 10/20 GB drive and leave the 120 GB one there (I am gonna get a drive bay). I am gonna put in a 40 GB one on there and install either Windows 98 or Windows 2000. I want to be able to boot either Windows 98/2000 off this hard drive or XP off my Maxtor without changing the BIOS. I know to dual boot Windows 98/2000 and XP you would have to install them first (the older OS gets installed first for the Windows bootloader), so I am not sure if I can use the Windows bootloader. I may want to use GRUB, but I don't wanna install Ubuntu to this hard drive because it's already on the 10/20 GB one!

---

### Post by louieb on 2009-04-29
You can copy the files from /boot/grub to a small (16MB is plenty) partition on the other drive.  Its called making a dedicated GRUB partition. Herman has a detailed description here [IDBS make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")

---

### Post by RealG187 on 2009-04-29
Does it have to be EXT?

So I make a EXT partition and copy those files, then make the partition for Windows?

Then the Entry for XP (second hard drive) and since the entry for Ubuntu goes to the primary master, it would start 98 or 2000?

---

### Post by louieb on 2009-04-29
I use ext for my dedicated GRUB partition, I know that works. Might want to make your windows partition 1st. It really does not matter where on the the drive the GRUB partition is.

---

### Post by RealG187 on 2009-04-29
So it can me after the Windows partition?

> is the best way to dual or multiple boot more than one Windows if there is no Linux operating system in the computer.that seems to be what I want.

The part on that page that says to reinstall Grub (as it will be removed when Windows is installed), those are the same directions I would follow if I reinstalled Windows after Installing Ubuntu (cuz I did that before, I had to reinstall Windows on this one machine and it removed Grub.)

---

### Post by louieb on 2009-04-30
Yes it the same as if you has installed Ubuntu 1st then windows. Your  changing the boot loader from windows NTLDR to GRUB.

---

