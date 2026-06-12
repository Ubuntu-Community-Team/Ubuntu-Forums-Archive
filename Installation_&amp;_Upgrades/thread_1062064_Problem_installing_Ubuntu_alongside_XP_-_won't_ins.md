---
title: "Problem installing Ubuntu alongside XP - won't install on correct partition"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by hendo on 2009-02-06
I'm hoping someone can help me out here. A search of the Ubuntu Forums, and some more general Google searching, haven't given me a solution.

I have a Windows XP system that i would like to dual-boot with Ubuntu. The problem is, i can't seem to figure out how to get Ubuntu to install on the correct partition. 

My computer has two hard drives (320 and 750Gb SATA drives), formatted in the following way using GParted:

320GB drive:
[list]
[*]80Gb NTFS  <---- WinXP is already installed here.
[*]80Gb EXT3  <---- THIS IS WHERE I WANT TO PUT UBUNTU
[*]4Gb Linux Swap
[*]150Gb NTFS
[/list]
750Gb drive:
[list]
[*]150Gb NTFS
[*]150Gb NTFS
[*]150Gb NTFS
[*]150Gb FAT32
[*]100Gb NTFS
[/list]
The problem is that, when i boot using the Ubuntu install disc, and the process gets to the Partitioning part, it only gives me an option to install on a 150Gb drive, and it's not clear to me which drive Ubuntu is wanting to install on. I assume it must be the 150Gb FAT32 drive. I can't work out how to get the installation CD to install Ubuntu on the 80Gb EXT3 partition.

I'm sorry if this is a very basic question, but all my searches haven't found a solution. I don't want to proceed without understanding where Ubuntu is installing, because some of the partitions on the 750Gb disk have files on them, and while i have backups, i'd prefer not to overwrite them.

---

### Post by dstew on 2009-02-06
When you run the Live CD, does it see the 320 Gb drive?

---

### Post by hendo on 2009-02-06
Yes, it does. Here's a [screenshot](https://jshare.johnshopkins.edu/mhender4/public_html/gen_images/screen.png) from the Live CD.

As you can see, the first two drives are the ~80Gb drives. The first one showing (83.2Gb) is the EXT3 drive, and the second one (85.9Gb) is the WinXP drive. The other partitions on both drives also show up as well.

Does this help? Any suggestions?

Edit:

One thing just occurred to me: does the EXT3 partition have to be a Primary Partition for Ubuntu to install on it? At the moment, the 320Gb drive is partitioned like this:

Primary Partition - 80Gb NTFS Win XP

Extended Partition
- Logical Partition 80Gb EXT3
- Logical Partition 4Gb Linux Swap
- Logical Partition 100+Gb NTFS

Would this partitioning cause a problem?

---

### Post by Niniel on 2009-02-06
Yes, I think you should make both Ubuntu and Swap partitions primary partitions.

---

### Post by avtolle on 2009-02-06
> **Niniel said:**
> Yes, I think you should make both Ubuntu and Swap partitions primary partitions.
The system partition for Ubuntu and the swap partition may both be on logical partitions within the extended partition; they need not be primary to work.

When arriving at the partitioning step, I'd suggest you select manual; choose the partition for the Ubuntu system, give it a mountpoint of /; choose the partition for swap, and give it a mountpoint of /swap. I'm not clear on your intent for the NFTS logical partition, but it needs a mountpoint if it is to be mounted when running Ubuntu, and this is a good time to give it one, if that is your intent. Good luck.

---

### Post by caljohnsmith on 2009-02-06
> **Niniel said:**
> Yes, I think you should make both Ubuntu and Swap partitions primary partitions.
I disagree, Ubuntu can be installed to a logical or primary partition, it makes no difference. Hendo, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
That will give us a better idea of your HDDs and partitions.

---

### Post by hendo on 2009-02-07
Hi folks.

Well, i've done it. It appears that the problem was not the software, but me (surprise, i know!). I didn't realize that selecting Manual would take me to a new screen where i could select my partition. D'oh!

Anyway, it's installed now. I went with Kubuntu in the end.

Tomorrow i have to work out how the hell to get my dual-monitor setup working with my NVidia 5200. That should be fun.

Thanks for all your help.

---

