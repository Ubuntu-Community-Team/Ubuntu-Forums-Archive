---
title: "Grub issues"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by bean56 on 2009-01-25
So I have a few problems.  Installed Ubuntu and all was well.  I installed a lot of updates and restarted and for whatever reason ubuntu decided it will just boot into the console instead of the Desktop GUI so that is one issue.  

The other issue is I already had Vista and XP installed on the hard drive and for whatever reason the grub doesn't have either of them on there. I've tried to do some of these things mentioned around here, but I always just get error 11. Any help with either issues would be great.  Here is my stuff

---

### Post by Pumalite on 2009-01-25
[http://users.bigpond.net.au/hermanzone/p15.htm#11](http://users.bigpond.net.au/hermanzone/p15.htm#11)

---

### Post by caljohnsmith on 2009-01-25
Both Vista and XP are installed to logical partitions sda5 and sda6 respectively; whenever you install Windows to a logical partition, it will put its boot files in some primary NTFS/FAT partition. Since you don't have a primary NTFS/FAT partition any more, it looks like both Vista and XP are missing their boot files. I would recommend following [this tutorial]("http://ubuntuforums.org/showthread.php?t=813628") in order to restore Vista's and XP's boot files, and also so you can configure them to boot from their logical partitions. Be sure to run the "testdisk" procedure on both the Vista and XP partitions, because their boot sectors need fixing. When you follow post #4 of that tutorial to fix your Vista partition, you can skip the "bootsect" command in step #2 since your Vista boot sector does not need it. Let me know how it goes or if you run into problems.

---

### Post by bean56 on 2009-01-25
> **caljohnsmith said:**
> Both Vista and XP are installed to logical partitions sda5 and sda6 respectively; whenever you install Windows to a logical partition, it will put its boot files in some primary NTFS/FAT partition. Since you don't have a primary NTFS/FAT partition any more, it looks like both Vista and XP are missing their boot files. I would recommend following [this tutorial]("http://ubuntuforums.org/showthread.php?t=813628") in order to restore Vista's and XP's boot files, and also so you can configure them to boot from their logical partitions. Be sure to run the "testdisk" procedure on both the Vista and XP partitions, because their boot sectors need fixing. When you follow post #4 of that tutorial to fix your Vista partition, you can skip the "bootsect" command in step #2 since your Vista boot sector does not need it. Let me know how it goes or if you run into problems.

So I followed those instructions to rebuild the boot sector for vista.  I'm not too worried about XP, I don't really use it. I got it going all smoothly starting to load up startup programs and everything, then suddenly blue screen and it restarted. Sounds to me like something got screwed up too much to fix.  I guess I'll try the repair on the vista cd since now it should at least find the installation.

If anyone could tell me how to get my linux to boot "properly" cause it's kinda hard to do everything from console, I'm not that linux Uber. At least then I won't have to boot from the linux cd every time.

---

