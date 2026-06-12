---
title: "After Ubuntu installation my XP was gone"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by bobetko on 2009-04-19
I selected guided partitioning since I was instructed (from some web page) that it will leave my windows intact (It will partition only free space). It seems to me that windows is gone. What did I do wrong? It's long since I played with ubuntu last time. Geez, it will take me few days to get everything back.

If I go to FileSystem properties I get following report:
Free Space: 131GB
Contents: 150333 items, totaling 3.2 GB (some content unreadable)

My HD is 160 GB. If I remember well I had two windows partitions C and D. All together windows OS and my files were taking around 25GB. It seems that that space is missing from ubuntu report. How can I get to it. 
If it's possible, then I would have to edit GRUB loader, right?

Could it be that my XP is still somewhere?
Any help is appreciated.

Thanks,
Bobetko

---

### Post by 67GTA on 2009-04-19
Open a terminal and post the output of ```
sudo fdisk -l
```

---

### Post by bobetko on 2009-04-19
It seems it is gone.
Here:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18702   150223783+  83  Linux
/dev/sda2           18703       19457     6064537+   5  Extended
/dev/sda5           18703       19457     6064506   82  Linux swap / Solaris
bob@bob-laptop:~$

---

### Post by 67GTA on 2009-04-19
Yes, you nuked it:( I would suggest manual partitioning. Reinstall XP. Boot the ubuntu live CD, and open the partitioner. Menu>System>Administration>Partition Editor. Shrink XP to whatever you want. Then create 2 ext3 partitions and a swap partition (swap needs to be at least as big as your ram size if you want to hibernate). Then write down all of the partition numbers for reference. When you install Ubuntu, choose manual at the partitioner step. Tell it to mount one of your ext3 partitions as /home, and the other as / (root). This will let you keep a separate home partiton. Next time you reinstall, choose manual partitioning, and tell the partitioner to use your home partition as /home, but not format it. Your personal settings will stay intact. If your a little nervous about it, just practice before you reinstall XP, so you don't have anything to lose.

---

### Post by cariboo on 2009-04-19
I'm sorry to say it looks like you told the installer to use the whole disk. You may be able to get you missing data back using [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk"), it is in the repositories, you can use Add/Remove Programs or Synaptic Package Manager to install it. The testdisk package also includes a program called photorec which is great for recovering data files.

Jim

---

### Post by bobetko on 2009-04-20
Thanks guys. And thanks for that info on partitioning 67GTA.

---

