---
title: "How to recover data from broken NTFS partition..?"
date: 2008-09-23
forum: General Help
---

### Post by delduvath on 2008-09-23
Here's the problem i have to solve for one of my friends:
- she uses windows xp, yesterday she said she simply closed the lid of ther laptop, and after opening it again an error occured saying that data has been corrupted on her d:\ partition and required to run chkdsk - but when she tried to do so the soft asked for a restart first.... which she did, but after that windows won't boot, and when i tried re-installing windows the d:\ partition wouldn't come up, it would just show unalocated space :/

- all i want is use an ubuntu live cd to recover her data from that NTFS partition

- after mounting both partitions (c: and d:) i noticed i could access just fine the c: partition, but the d: one it says "The folder contents could not be displayed. Sorry, couldn't display all the contents of "disks-conf-sda2" ", and it doesn't show any file at all

- if i try to browse that partition through the terminal, on the ls command it says "ls: reading directory .: Input/output error"

- this is what it shows when i run "sudo fdisk -l" : 
"Disk /dev/sda: 60.0GB, 60011642880 bytes
15 heads, 63 sectors/track, 124032 cylinders
Units = cylinders of 945 * 512 = 483840 bytes

Device boot        Start        End        Blocks     Id      System
/dev/sda1             2          17754      8388292+    f     W95 Ext'd (LBA)
/dev/sda2           17755       124029      50214937+   7   HPFS/NTFS
/dev/sda5             2         17754       8388261     7   HPFS/NTFS"

- when accesed with Disks Manager, i can see both partition, i can also see how much space is used and how much isn't on BOTH of them, ubuntu recognizes them as Windows NTFS partitions

- all i want to do is recover the girl's data and FORMAT the freakin thing

So.... :confused: how to do it? any ideeas guys? txs for at least reading all this cr@p :P

---

### Post by pablopancho on 2008-09-23
Try installing ntfsprogs - this is a set of tools for ntfs. Then in terminal run:
```
sudo ntfsfix /dev/(partition)
```
where (partition) is the name of your d: drive in linux, e.g. sda1
in my case it is for example:
```
sudo ntfsfix /dev/sda2
```

---

### Post by bonmaria on 2010-08-12
Hi,

As u say's your NTFS psrtition is not work.

Microsoft providing you window's restore facilities.

These are step's
[B]
Go to Start >>[/B] **All Programs >>** **Accessories >>** **System Tools >>** **System Restore **

New window open of system restore

To start system restoration two option are there

1. Restore my computer to an earlier time

2. Create a restore point.

Select option "**Restore my computer to an earlier time**"

then click next button.

In calendar bold dates are restore points. then click desire date and restore your data.

If you have not get your particular data which you want then you can try a third party data recovery software, Kernel for NTFS recovery software from [www.ntfsrecovery.org]("http://www.ntfsrecovery.org")


Thanks
BonMaria

---

### Post by searchfgold6789 on 2011-09-30
Ntfsfix is a great idea.
However, System Restore is not a good idea, because it will not work in this situation. You have reinstalled Windows and deleted all the recovery data.
If you only want to use the Ubuntu Live CD to get all the data from D:\ back, then the best tool for this is [testdisk from CGsecurity]("http://www.cgsecurity.org/wiki/TestDisk"). It is amazingly powerful and is open source and free.

---

