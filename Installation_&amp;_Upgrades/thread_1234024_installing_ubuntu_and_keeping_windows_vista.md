---
title: "installing ubuntu and keeping windows vista"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by Cannon1230 on 2009-08-07
I want to install ubunu, and still keep my windows xp.   I have three questions.... first, will ubuntu run just as fast even though I will still have windows on my laptop? second, when I install ubuntu and keep my windows, will all of my info on my vista (pics songs, ect..) be deleted? third, will my wireless internet still work??
Hope someone can help!! Thanks
Cannon1230:D

---

### Post by phillw on 2009-08-07
Hi ...

Good place to start is here ...

[https://help.ubuntu.com/community/Beginners/FAQ](https://help.ubuntu.com/community/Beginners/FAQ)

If you are in XP or Vista, the instructions are slightly different..

But the above should explain it all for you.

Regards,

Phill.

---

### Post by Mark Phelps on 2009-08-08
Best thing to do first is boot from the Ubuntu LiveCD to see how well it detects your hardware and installs the proper drivers.  Wireless can be a particular problem.  If everything works in LiveCD mode, it should work OK after install.

Since you mentioned Vista, be sure to use the Vista Disk Management tool to shrink the OS partition to make room for Ubuntu.  Do NOT use the Ubuntu installer to do that; doing so risks corrupting your Vista OS partition such that it becomes no longer unbootable.

If, when you go to install Ubuntu, it does not detect your Vista installation, do NOT continue!  Reboot into the LiveCD and use the Partition Editor (GParted) to manually create an Ext3-formatted partition in your unallocated space. Then, when you install again, select manual partitioning and select the partition you just created.  This helps insure that you don't accidentally overwrite the Vista OS.

When Ubuntu finishes its install, it will overwrite the MBR on your laptop so that when you next boot, it will boot into GRUB and you will get a boot menu listing your Uubuntu options and Vista.

---

### Post by raymondh on 2009-08-08
> **Mark Phelps said:**
> Best thing to do first is boot from the Ubuntu LiveCD to see how well it detects your hardware and installs the proper drivers.  Wireless can be a particular problem.  If everything works in LiveCD mode, it should work OK after install.

Since you mentioned Vista, be sure to use the Vista Disk Management tool to shrink the OS partition to make room for Ubuntu.  Do NOT use the Ubuntu installer to do that; doing so risks corrupting your Vista OS partition such that it becomes no longer unbootable.

If, when you go to install Ubuntu, it does not detect your Vista installation, do NOT continue!  Reboot into the LiveCD and use the Partition Editor (GParted) to manually create an Ext3-formatted partition in your unallocated space. Then, when you install again, select manual partitioning and select the partition you just created.  This helps insure that you don't accidentally overwrite the Vista OS.

When Ubuntu finishes its install, it will overwrite the MBR on your laptop so that when you next boot, it will boot into GRUB and you will get a boot menu listing your Uubuntu options and Vista.

Also, defrag Vista first and back-up your files.  Post back if you need assistance in doing this manually.

Read the release notes too.  This is for [Jaunty]("https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes").

Good luck.

---

### Post by raymondh on 2009-08-08
> **Cannon1230 said:**
>  second, when I install ubuntu and keep my windows, will all of my info on my vista (pics songs, ect..) be deleted? 
Cannon1230:D

If you DO NOT touch your windows install (i.e. install Ubuntu over your windows partition hence effectively erasing windows), it should not.

As mentioned by others, read up on an [installation]("https://help.ubuntu.com/community") guide.

---

### Post by Cannon1230 on 2009-08-16
> **Mark Phelps said:**
> Best thing to do first is boot from the Ubuntu LiveCD to see how well it detects your hardware and installs the proper drivers.  Wireless can be a particular problem.  If everything works in LiveCD mode, it should work OK after install.

Since you mentioned Vista, be sure to use the Vista Disk Management tool to shrink the OS partition to make room for Ubuntu.  Do NOT use the Ubuntu installer to do that; doing so risks corrupting your Vista OS partition such that it becomes no longer unbootable.

If, when you go to install Ubuntu, it does not detect your Vista installation, do NOT continue!  Reboot into the LiveCD and use the Partition Editor (GParted) to manually create an Ext3-formatted partition in your unallocated space. Then, when you install again, select manual partitioning and select the partition you just created.  This helps insure that you don't accidentally overwrite the Vista OS.

When Ubuntu finishes its install, it will overwrite the MBR on your laptop so that when you next boot, it will boot into GRUB and you will get a boot menu listing your Uubuntu options and Vista.

THANKS SO MUCH! 
This is great info!!!! UBUNTU ROCKS!!!!!!

---

