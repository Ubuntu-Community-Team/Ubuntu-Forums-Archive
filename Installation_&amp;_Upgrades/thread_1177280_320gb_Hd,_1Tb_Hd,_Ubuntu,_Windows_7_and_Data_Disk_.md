---
title: "320gb Hd, 1Tb Hd, Ubuntu, Windows 7 and Data Disk - Best way to partition ?"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by enfantterrible on 2009-06-03
Hello everybody

I am about to receive a new system, with no OS installed on it. I currently have XP/ubuntu 9.04 on a 80Gb ext4 Hdd and a shared FAT32 320Gb for data (mp3s, avis etc).

I would like to replicate a similar thing on the new system, but with a few catches.

a) the new system has no OS on it
b) all my data is on the 320Gb drive. I will put it in the computer, boot the first time with the ubuntu live cd and transfer that data to the Terabyte disc (after formatting it FAT32 with g-parted). then install ubuntu 9.04 on the 320 Gb drive (formatted ext4)
c) i want to install windows 7 (because it's free for a month still and i need windows for work) but only AFTER linux is up and running

so, how would the best partition scheme be ? is the one i lay out below reasonable ?

HDD 320 GB
- 100 GB ext4 Ubuntu system (including /home or excluding it?)
- 20 GB swap
- 220 GB NTFS Windows 7
HDD 1 TB
- all FAT32 ?

i was thinking of putting /home somewhere on the 1TB disk, but does it make sense? now i have a mount DATASHARE which is all the FAT32 disk where wins' "my documents" is located.

i know i can experiment, but since i dont like to play with partitions too much i would like to ask your opinions on what is the best way to partition. (and to make win7 work, as i will install in two weeks probably?)

thank you all for your help

---

### Post by smartidiot on 2009-06-03
I would suggest not using FAT32 formatting on your data drive.

With the driver from [http://www.fs-driver.org/](http://www.fs-driver.org/) Windows can read Ext2 and Ext3 partitions without any problem.

I would put /home on the larger drive - with only 100G of Space I know I would run out of room on Linux.  Of course I do everything in Linux.  Just think about how much room you might need.

[http://the-smartidiot.blogspot.com/](http://the-smartidiot.blogspot.com/)

---

### Post by Mark Phelps on 2009-06-03
In terms of sharing the 1TB data between Seven and Ubuntu, I would opt for NTFS instead of Ext3.  This will present no problems with either OS, since Seven can obviously work with NTFS, and with the ntfs-3g and ntfsprogs packages, Ubuntu can do so as well.

Personally, I'd rather trust the NTFS-3g driver to work with NTFS partitions without problems, than to trust the other driver in Seven to work with ext3 partitions.

But ... it's your call.

---

### Post by merlinus on 2009-06-03
Can you imagine having to regularly defrag a iT hdd!!!  That alone is a reason to use ext3.

---

