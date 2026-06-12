---
title: "Partitions and Boot Sectors"
date: 2005-08-22
forum: Hardware &amp; Laptops
---

### Post by Chris Mounce on 2005-08-22
I like to play old Dos games. I installed DosBox, which works well enough for most of my purposes, but it's not quite like the real thing. I've been thinking about creating a Dos partition so that when GRUB starts (already installed on my system), I'll be able to boot either into Dos or Ubuntu Linux.

I've got two hard disks: the first one is blank, and the second contains my installation of Ubuntu. I'm going to create the Dos partition on the first disk, but before I do so, I need some reassurance. If I use fdisk or cfdisk, is there any chance of messing up the boot sector on the first disk (which starts GRUB which starts Ubuntu)? Also, how would I go about setting up the boot sector again, assuming I had a bootable CD? Finally, is it possible to mount a Dos partition from inside Ubuntu?

Many thanks ahead of time.

---

### Post by nad on 2005-08-23
It's been a long time. Your issue will not be with with your partition editor, but with the dos sys utility which will install the dos bootloader in the mbr (if I remember correctly). You will then need to reinstall grub to your boot sector and then modify your /boot/grub/menu.lst to include dos.

As far as reinstalling grub, here is a good discussion: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

Yes, you may mount a FAT file system in ubuntu.

---

### Post by Chris Mounce on 2005-08-23
Thank you very much!

---

