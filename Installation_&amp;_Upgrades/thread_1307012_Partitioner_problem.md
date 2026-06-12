---
title: "Partitioner problem"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by socket on 2009-10-30
Hi,

I'm facing some problems when trying to install Ubuntu Desktop 9.10 on my machine.

I have an Athlon XP 2400+, 1GB RAM and 250GB Sata HD, with dual boot Windows XP and Kubuntu 7 (very old, I know). 

My HD has the following partitions:

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfec4fec4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2435    19559106    7  HPFS/NTFS
/dev/sda2            2436       30401   224636895    f  W95 Ext'd (LBA)
/dev/sda5            2436        3748    10546641    b  W95 FAT32
/dev/sda6            3749        4793     8393931    b  W95 FAT32
/dev/sda7            4794       26474   174152601    b  W95 FAT32
/dev/sda8           26475       26746     2184808+  83  Linux
/dev/sda9           26747       26885     1116486   82  Linux swap / Solaris
/dev/sda10          26886       28251    10972363+  83  Linux
/dev/sda11          28252       30401    17269843+  83  Linux


On /dev/sda8 partition I have the / (root) and on /dev/sda11 the /home. 

So, I'm booting the Ubuntu 9.10 CD (Live CD) and when I try to install the O.S., at the partition manager nothing appears to me (blank screen). I also tried to install directly (without booting Live CD), but the same happens.

Take a look at screen-shot (it is in pt-BR):
[IMG]http://i263.photobucket.com/albums/ii122/r00lz/Screenshot.png[/IMG]

I'm stuck here!

My Live CD is working correctly because I already installed it on other computer (clean install). So, the problem is specifically related to my PC, maybe because of my partitions.

Does anybody can help me?

My best regards.

---

### Post by louieb on 2009-10-30
For what its worth - fdisk listing looks fine - don't see any problem. Or any reason for it not to work. Guess your trying to use manual partitioning? Is that right. 

Guess you could try the alternate (text based Debian installer) CD - it uses a different partitioner - might have better results.

---

### Post by socket on 2009-10-31
> **louieb said:**
> For what its worth - fdisk listing looks fine - don't see any problem. Or any reason for it not to work. Guess your try to use manual partitioning? Is that right. 

Guess you could try the alternate (text based Debian installer) CD - it uses a different partitioner - might have better results.

I was thinking about it... because in older versions I only got success with alternate CD.

I'll give a try, again!

Thanks for your reply!

---

### Post by ColJep on 2009-10-31
I opened a thread with this exact problem yesterday. While writing it I had the idea to try gparted from the live install. This worked and then the installation went fine afterwards.

Obviously something wrong here.

---

### Post by socket on 2009-10-31
It's good (or not) to see that I'm not the only one with this issue!
I'm downloading the Alternate CD... maybe it works!

---

