---
title: "Help the Noobie"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by mhklein on 2009-06-23
I had Vista on my laptop and wanted to try Ubuntu to make sure it works and that I would like it. I set it up with a dual boot (So I had Vista and Ubuntu). I decided I wanted to keep Ubuntu and remove Vista, so I reinstalled Ubuntu using the entire partition. As expected Vista is gone, but it still dual boots, now to the initial Ubuntu installation and the new installation. I probably did this all wrong, so feel free to make fun of the noobie. 

How can I get rid of the initial installation?

---

### Post by aesis05401 on 2009-06-23
There are a couple of ways to do this - but my longterm recommendation (useful in the widest range of emergency situations) is to keep a burned utility livecd around at all times.  I am currently using the GParted livecd, but there are all sorts of these utility disks covering different types of computer management/emergency recovery scenarios. 

The easiest way to blow away a partition that is *not* the partition you are currently booted into is through : System/Administration/Partition Editor.  This partition manager will not work for the partition you are booting into, and if you need to change the metrics on your boot partition you need to reboot with a utility based livecd so that the boot partition is not mounted and you can perform maintenance.

From within the Partition Editor (which is itself a version of GParted) you can change between physical devices using the drop down in the upper right corner, and you can access all the standard information about the partitions you are viewing.  Simply right-click on a partition to view options.

Before you blow anything away, though, you will want to make sure you understand how Ubuntu installed on your machine.  There are many ways to configure Ubuntu including placing root, home, data shares etc on different partition.  So unlike Windows, there may be partitions outside of your root Ubuntu install that are being used by your current install.

---

