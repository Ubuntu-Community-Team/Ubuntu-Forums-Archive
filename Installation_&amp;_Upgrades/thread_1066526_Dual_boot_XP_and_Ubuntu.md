---
title: "Dual boot XP and Ubuntu"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by jakenbake42 on 2009-02-10
I've got all my files backed up, and I've started over, but I have XP on my computer, and when I try to install Ubuntu to dual boot, it just won't partition the disk properly

How can I do this, from started to install XP to finishing intalling Ubuntu, what formats do I use and when do I make partitions??

Thanks! :]

---

### Post by Partyboi2 on 2009-02-11
What do you mean by "it just won't partition the disk properly"?  Are you having problems with the automatic partitioning choosing the wrong size for your partitions, any error messages etc....

---

### Post by dvlchd3 on 2009-02-11
If you do not have XP already installed on your PC.  Install it first.  Create a partition with the XP startup disc that leaves as much space as you want for ubuntu as "Unallocated space".

Then install Ubuntu.  When asked where you want to install it use Guided - Largest contious free space (or something like that).  This will format the blank space as EXT3.  Also, Ubuntu will install GRUB as the default bootloader replacing the Windows bootloader.

When starting for the first time, you will see GRUB showing 4 options:
Ubuntu 8.10
Ubuntu 8.10 (Recovery Mode)
MemTest
Other Operating Systems: (Not an option)
Windows XP

Choose the appropiate operating system (usually either Ubuntu 8.10 or Windows XP).

---

### Post by jakenbake42 on 2009-02-11
Oh, this all worked, thanks so much guys!! :]

---

