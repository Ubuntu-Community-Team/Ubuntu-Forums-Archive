---
title: "Can not install ubuntu 9.10 using a live CD"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by armageddon1 on 2009-10-30
Hi, I am trying to install ubuntu but I get a message telling me "No root file system is defined." (I get this when pressing "forward" right after pic 4 below). So I google for this and find out peoples suggestions and so I do this:

I create a partition (sda4 below) to be given the ext3 file system. I also create a partition as swap (sda1) and run swapon on it. But still I am not able to install ubuntu 9.10. What can the problem be?

Thank you.

> sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800200

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1020     8193118+  82  Linux swap / Solaris
/dev/sda2           23331       24321     7960207+   5  Extended
/dev/sda3   *       12506       23330    86951812+  a5  FreeBSD
/dev/sda4            1021       12505    92253262+  83  Linux
/dev/sda5           23331       24321     7960176   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         488     3919841    b  W95 FAT32

---

### Post by Fire_Chief on 2009-10-30
It appears as though /dev/sda4 is nearly full (1.42 GB Unused). Unless you format that space, it is likely not usable as the root mountpoint (not enough free space for install files). Also, why do you have 2 swap partitions (1 at the beginning and 1 at the end of the drive)?

The partitioner thinks /dev/sda3 is unused space. Is that accurate? If so, you could designate that as the root mountpoint instead and keep whatever data is on /dev/sda4.

Cheers!

---

### Post by armageddon1 on 2009-10-31
Hi Fire_Chief,

So now I have merged sda4 and sda1. I've tried having it as unallocated space. I've tried setting it as unformatted space. I've tried formatting  it as ext3. Yet nothing works. Also it first says that the partition is nearly empty but as soon as I mount it to / it gets filled up. 

The first picture shows right after I've formatted the space and the second shows right after I've done a "sudo mount /dev/sda1 /". (In these pictures it is sda1 I want. The sda3 partition contains freebsd and I do not want to remove it)

Thanks

---

### Post by armageddon1 on 2009-10-31
My HD seems to have a few bad sectors, and I am told in the IRC-channel that this might be the problem.

---

### Post by Fire_Chief on 2009-11-02
Interesting...I've not actually seen that before. Please let us know if it is indeed a bad sectors problem. Unfortunately, I'm not well versed in testing drives for bad sectors when it's not formatted already. :(

---

### Post by armageddon1 on 2009-11-17
> **Fire_Chief said:**
> Interesting...I've not actually seen that before. Please let us know if it is indeed a bad sectors problem. Unfortunately, I'm not well versed in testing drives for bad sectors when it's not formatted already. :(

The problem turned out to be RAID related (something to do with the RAID configuration). As it wasn't me who fixed it, and since I do not know much about hardware issues, I can not say more than that. Sorry that I could not give any exact details but hopefully this might be enough to help out people with the same problem. :)

---

### Post by armageddon1 on 2010-06-27
I am about to make a clean install of the latest Ubuntu version but I am faced with the same issue again. I cannot reach the person who helped me the last time. So can anyone help me out here? As I said in my last post, the problem was RAID related. Anyone know what I should check for?

Thanks

Edit, sudo dmraid -r gives
/dev/sda: isw, "isw_eeegihide", GROUP, ok, 390721966 sectors, data@ 0
And "ls /dev/mapper" only gives "control".

> sudo dmraid -s
ERROR: isw device for volume "lin" broken on /dev/sda in RAID set "isw_eeegihide_lin"
ERROR: isw: wrong # of devices in RAID set "isw_eeegihide_lin" [1/2] on /dev/sda
ERROR: isw device for volume "win" broken on /dev/sda in RAID set "isw_eeegihide_win"
ERROR: isw: wrong # of devices in RAID set "isw_eeegihide_win" [1/2] on /dev/sda
*** Group superset isw_eeegihide
--> Subset
name   : isw_eeegihide_lin
size   : 222939136
stride : 128
type   : mirror
status : broken
subsets: 0
devs   : 1
spares : 0
--> Subset
name   : isw_eeegihide_win
size   : 167772160
stride : 128
type   : mirror
status : broken
subsets: 0
devs   : 1
spares : 0

(Don't know if this is helpful)

---

