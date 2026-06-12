---
title: "Dissapeared NTFS partition"
date: 2016-01-17
forum: Hardware
---

### Post by Adrian_Ksz on 2016-01-17
Hi,
I've make the switch to ubuntu, full time, but i still have some ntfs partitions. I was trying to set the label for one of the partitions and I did mkntfs -L command after reading online and also the help that it sets the volume label.
Now the partition is gone, it appears when I do fsdisk -l, but when i try to mount it with gparted for example, I get 
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error

is there anything i can do? i had a lot of data on that partition and really wouldn't want to loose it.

thanks

---

### Post by pfeiffep on 2016-01-17
You might try [URL="http://www.dedoimedo.com/computers/linux-data-recovery.html"]testdisk
More info
[/URL]

---

### Post by LostFarmer on 2016-01-17
Can you give exact 'mkntfs -L' command used ?   Can you post the output of 'fdisk -l ' ?

---

### Post by Adrian_Ksz on 2016-01-17
> **LostFarmer said:**
> Can you give exact 'mkntfs -L' command used ?   Can you post the output of 'fdisk -l ' ?

mkntfs -L Data /dev/sda3

no output

---

### Post by weatherman2 on 2016-01-17
And the output of "fdisk -l " is - ?

---

### Post by yancek on 2016-01-17
My understanding of the command you used not only creates a Label but also formats the partition which is going to make it difficult to get the data.  Try the suggested software, testdisk.

---

### Post by Adrian_Ksz on 2016-01-18
> **weatherman2 said:**
> And the output of "fdisk -l " is - ?

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          4094  336570367  336566274 160,5G  5 Extended
/dev/sda2        336570368 1677715455 1341145088 639,5G  7 HPFS/NTFS/exFAT
/dev/sda3       1677716145 1953520064  275803920 131,5G  7 HPFS/NTFS/exFAT
/dev/sda5             4096   20975615   20971520    10G 82 Linux swap / Solaris
/dev/sda6         20977664   22001101    1023438 499,7M 83 Linux
/dev/sda7         22003712  126861311  104857600    50G 83 Linux
/dev/sda8        126863360  336570367  209707008   100G 83 Linux

---

### Post by weatherman2 on 2016-01-18
Oh, I think yancek is right: you probably formatted the partition with that command; the -L is used during format to add a label.  Time to try a file recovery program like testdisk to see what you can get back.  (You may get almost everything back but the names may be all messed up.)  There's some chance that testdisk can in fact repair the partition.

---

### Post by Adrian_Ksz on 2016-01-18
thank you all for your help, i will give testdisk a try and let you know

---

