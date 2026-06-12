---
title: "extended partition on manual installation"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by excbuntu on 2009-03-01
to install linux on my laptop (asus eee 1000HA), i downloaded ubuntu (easypeasy 1.0) and put it on a usb drive via unebootin. i booted to the usb drive and found that my laptop contains the maximum 4 primary partitions (according to [this]("http://ubuntuforums.org/showthread.php?t=282018") guide): 

sda1 = windows, 9gb
sda2 = blank, fat 67gb
sda3 = laptop recovery, fat, 5gb
sda4 = laptop recovery, unknown, 41mb

i wanted to install linux in a simliar fashion as described in the "Bulldog's Partitioning advice" in the aforementioned link. to do this, sda2 should be deleted and be an extended drive divided into 3 logical ext3 partitions:

sda5 = / 35gb
sda6 = /home 29
sda7 = swap 3

my problem is that ubuntu's manual (as opposed to the guided) partitioner does not give me an option to create an extended drive. i am able to delete the partition, but making a new partition on the resulting free space only gives me the options for another primary or logical. i'm not understanding something.

---

### Post by taurus on 2009-03-01
Since you already have 4 primary partitions, you need to convert one of those primaries into extended partition and then create logical partitions under that extended partition.

---

### Post by excbuntu on 2009-03-01
> **taurus said:**
> Since you already have 4 primary partitions, you need to convert one of those primaries into extended partition and then create logical partitions under that extended partition.

thanks for the quick reply, but my problem is that ubuntu's manual (as opposed to the guided) partitioner does not give me an option to create an extended drive. i am able to delete the partition, but making a new partition on the resulting free space only gives me the options for another primary or logical. i'm not understanding something.

---

### Post by tommcd on 2009-03-01
> **excbuntu said:**
>  my problem is that ubuntu's manual (as opposed to the guided) partitioner does not give me an option to create an extended drive. i am able to delete the partition, but making a new partition on the resulting free space only gives me the options for another primary or logical. i'm not understanding something.

A logical partition is what you want. Your options are primary and logical. When you create a logical partition the result is that you get an extended partition with 1 (or more, if you create them) logical partitions inside the extended partition. For example, look at my **fdisk -l** :
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4080    12289725   83  Linux
/dev/sda3            4081        4207     1020127+  82  Linux swap
/dev/sda4            4208       30401   210403305    5  Extended
/dev/sda5            4208        5737    12289693+  83  Linux
/dev/sda6            5738        7267    12289693+  83  Linux
/dev/sda7            7268       30401   185823823+  83  Linux

```
/dev/sda4 is an extended partition which includes the logical partitions /dev/sda5-7.

---

