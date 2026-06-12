---
title: "Installation advice please"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by dave39 on 2009-03-31
Hello,

Firstly apologies for asking a FAQ. I have searched the forums and docs but I think I still need to ask a question, sorry!

My primary hard disk currently has two bootable physical partitions: a FAT32 with Windows 98 on it, and an NTFS with Win XP Home.  The FAT32 partition is hidden when I boot XP.  I set this up with Partition Magic, which I find very reliable.  I currently use the Partition Magic boot manager, but I don't mind which boot manager I use as long as it works.

Now I want to decrease the Win XP NTFS partition size, add Ubuntu in new partitions, leave the existing OSs alone, and end up with a triple boot (Win 98/Win XP/Linux).

What is the best way to achieve this please?  If I want to do the partitioning with Partition Magic, how do I then complete the Ubuntu install?  Or is it easier to use the Ubuntu partitioner/manager?

Many thanks for some advice.

---

### Post by Linoobius on 2009-03-31
Dave39,

There is nothing wrong with using partition magic to create the partitions if you are comfortable with that program, however, I would recommend using partition magic to just create unallocated disk space, then when you go into the ubuntu installer you will have the option of installing ubuntu into that unallocated space and the installer will handle creating the ext3 and swap partitions for you. Also note that on the last screen of the setup process before the actual installation begins, there is an "Advanced" button in the lower right corner of the dialog box. Clicking this will allow you direct where you want to install GRUB which is the "GRand Unified Bootloader" that ubuntu uses as a boot manager. If you want to continue to use your partition magic to select your operating system make sure you tell it to install into the partition that ubuntu is installing into, by default, if I recall correctly, it will install into the boot sector overwriting your partition magic boot loader. GRUB is certainly capable of booting both Window 98 and Windows XP and it's fairly good at identifying and setting up the other OS's for you but just be aware that it's not as pretty as partition magic and the configuration could require some "massaging". I hope everything goes well for you,

Linoobius

---

### Post by dave39 on 2009-04-01
Many thanks Linoobius, that sounds like excellent advice.  I'll get started.

---

