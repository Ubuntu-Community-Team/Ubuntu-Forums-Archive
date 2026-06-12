---
title: "partition  issuses with super ubuntu/windows dual boot"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by ufish54 on 2009-02-22
I would like to put super ubuntu back on as a dual boot with windows vista/7 but when installing ,it  wants to use 109 gb of my hard drive and leave only 44 gb for windows . can i change the partition size afterword with gparted,which is part of the installed programs on this ubuntu? I got a warning that after writing this partition/install to disk that this cant be undone and I only wanted to give ubuntu 40 gbs of space..Thanks

---

### Post by cariboo on 2009-02-22
Use Vista's Disk management tools to shrink you Vista partiton and create the empty space you need to install Ubuntu.

Jim

---

### Post by bgates on 2009-02-22
You can partition it any way you like during installation.  Simply choose the manual partitioning option.

But to answer the question, yes, you can also resize partitions at any time using gparted.  You can't resize the partition you are currently booted into, so if you want to resize your Ubuntu partition you can make the gparted liveCD and boot from that.

Remember to back up important data before any partitioning maneuvers.

---

### Post by Mark Phelps on 2009-02-23
Just be aware that Vista (don't know about Seven) is VERY picky about any changes being made to its OS partition by other tools.  

If you use GParted or the Ubuntu installer to resize your Vista (or Seven?) partition to make room for Ubuntu, don't be surprised if the Windows OS will not boot anymore after that.  

If you have a Vista DVD, you can fix that OS by booting from that DVD and running a Startup Repair.  If you don't have that DVD, you run the risk of rendering Vista unbootable.

For some workarounds in using the Vista Disk Management tool to resize the OS partition, see the following link:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

---

