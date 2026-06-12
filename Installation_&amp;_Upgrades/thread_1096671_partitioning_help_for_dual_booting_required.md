---
title: "partitioning help for dual booting required"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by indianelephant on 2009-03-15
hi,
hi all,
my pc config is 2.53C2D,2gb ram, 160gb hdd.
Currently xp sp3 is installed.
Thinking to install ubuntu 8.1
PARTITIONING QUERY
partitions are as
c:[fat32] 30gb 15gb free space
d; ntfs 30gb    8gb "
e;ntfs 30gb     12  " 
f;ntfs 30gb     12  "
**free space of 30gb balance is unallocated.**
**I intend to install ubuntu 8.1 on this free space.**
Now i have read a lot on the net regarding the partition types possible with different suggestions. Eg ?,home & shared data partition,swap.

Given the case of my hdd. i want to know how should i go about to ensure proper utilisation of the partitions and what all should be created for ubuntu. For eg some where i read that if ram is 1gb or more no swap is required. Some wrote there is no point to create a 'home' partition as upon a new release of ubuntu the applications settings will be lost. Somewhere i read better create a "data" partition instead of home. Alot of these articles are 2yrs old etc.Now ubuntu must have also changed by that time i hope so.
Also on file systems which to go for ext3 or ext2. some Old articles were carrying ext2 new ones are ext3.
This being my first time install pls guide me as to what to do in the given case.

My best wishes

---

### Post by AXeS on 2009-03-15
Well idianelephant,

Surprising you haven't read any new material where you dont even have to 
partition your drive for you to have Ubuntu on your system.

If you have the disc of ubuntu, stay in windows and pop it in the drive and 
there should be auto-run prog that runs. It's called 'wubi'. What it does 
(in lamens terms) it take allocated space and makes it an image where ubuntu 
can install without you having to go through the trouble of partitioning it. 
So you say, lowest space it can take up would be 4gig on any available drive with that or more space preferably,then you set user name and password and there you go. It changes you windows boot menu, so now it looks as though you dual booting...which you are, and the 1st time you boot into ubuntu it will setup the rest , wait a while and you have it on your system.

No mess no fuss, no harm no foul.

---

### Post by vanadium on 2009-03-15
I don't agree with the suggestion of AXeS to go for a Wubi install. While a wubi install is easy and convenient, installation on separate partitions is to be preferred. In fact, you have 30 GB unallocated, so there is not any reason not to go for an install on a separate partition.

The Ubunut installer can adjust partitioning automatically. You do not have a very standard partitioning, so it might be better for you to do partitioning manually. All you need for an Ubuntu install is one partition to be used for the root directory (/) and one swap partition.

Out of your 30 unallocated GB, allocate a few gigabytes for the swap. The remainder can be occupied by /.

Eventually, you may want to post the output of the command "sudo fdisk -l" so we can see how your current partitioning is like (including extended and logical partitions).

---

### Post by indianelephant on 2009-03-15
Thanks for your replies. As far as wubi is concerned i have already tried it out and post that only i have decided to go for a dedicated partition install.Secondly with the live cd also i understand that the installer automatically resizes the partitions etc. But i dont want to disturb windows and want to give a seperate partition to ubuntu.Since excepting c: the balance of all my partitions are data partition i am just seeing for a better possibilty how the same can be done. I also can see nfts accessible from ubuntu. And have also read the psychocats site on partitioning

Here is the output of the sudo fdisk -l command for my hdd.
----------------------------------------------------------
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35433543

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3891    31254426    c  W95 FAT32 (LBA)
/dev/sda2            3892       19456   125025862+   f  W95 Ext'd (LBA)
/dev/sda5            3892        7782    31254426    7  HPFS/NTFS
/dev/sda6            7783       11673    31254426    7  HPFS/NTFS
/dev/sda7           11674       15564    31254426    7  HPFS/NTFS

-------------------------------------------------------------------

---

### Post by vanadium on 2009-03-15
What you can try first is run the Ubuntu installer, and select "use largest free space". The installer should then automatically install a logical sda8 to use as root, and a logical sda9 to use as swap.

If the installer cannot handle your situation, then create these two partitions yourself in the unallocated space at the end using gparted from the live CD. Then launch the installer and instruct it to use sda8 as / and sda9 as swap.

This would leave all your current partitions and your Windows install alone, and install Ubuntu. The grub bootmanager will be installed at the end of the installation proces, and allow you to choose either Windows or Ubuntu during start up.

---

### Post by munishvit on 2009-03-15
Sorry to mix-up my problem with this thread, but I too have problem with dual-boot and I want to install Windows XP on non-first primary partition. Please Check
[http://ubuntuforums.org/showthread.php?t=1095893](http://ubuntuforums.org/showthread.php?t=1095893)
aaanny help would be great. Thanks :D

---

### Post by indianelephant on 2009-03-15
OK will try the first suggestion and then report. Meanwhile i want to know how much space to allocate to the swap partition for my 2gb ram. Does the installer does it automatically or should i input in the first method which u mentioned.

---

### Post by vanadium on 2009-03-15
If the installer can handle your situation, all partitioning will proceed automatically. If you need to do manual partitioning, you will need to decide on the swap space yourself. For 2 GB Ram, you should take 2 or perhaps 3 GB of swap.

---

### Post by indianelephant on 2009-03-16
when i use the last option 'use the largest continuous free space' ubuntu installer showed me this
before c: 19% d:19% e:19% f:19% free:20%[read drive as sda1,5,6,7]
after : ...................ubuntu 8.1..........................
                            100%
So what should i interpret this as ? is ubuntu going to install the whole drive? so i stopped the installation there.

---

### Post by vanadium on 2009-03-16
You probably were about to wipe the entire drive indeed.

You will need to do manual partitioning if Ubuntu cannot use the largest free space in your setup. This can be done from within the installation procedure, or on beforehand from the live CD session.

The information you gave me ("sda1,5,6,7") learns me that you have 1 primary partition (sda1), and 1 extended partition (sda2) containing three logical partitions (sda5 - 7).

In the partitioner

* Make sure the extended partition does cover the free space as well. Otherwise, you will need to enlarge it first to cover that unused area
* After that, you must create your root partition (about 27 GB, it will become sda8) and your swap (the remaining 3 GB), both as logical partitions inside the extended partition. Format the root partition as ext3.

After partitioning, you will need to indicate the installer to use sda8 as your root, and sda9 as swap.

---

