---
title: "Jaunty Installed but says I have no free space??"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by ScottBurnham on 2009-04-24
I have a 400gb hard drive. I shrunk my windows partition down giving me about 130gb of free space in a new partition. I installed Jaunty onto the new 130gb partition. I then try and install programs and such and updated but it says I have zero free space. How can this be??

---

### Post by mcduck on 2009-04-24
> **ScottBurnham said:**
> I have a 400gb hard drive. I shrunk my windows partition down giving me about 130gb of free space in a new partition. I installed Jaunty onto the new 130gb partition. I then try and install programs and such and updated but it says I have zero free space. How can this be??

Could you run "df -h" and "sudo fdisk -l" in a terminal and post the outputs here so we can check what your actual partition sizes are?

("sudo fdisk -l" lists all your disks, partitions and their sizes. "df -h" shows mounted partitions and the amounts of used/free space on them.)

---

### Post by ScottBurnham on 2009-04-24
Here is the output from running those:

```
modifiedreality@modifiedreality-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 754M     0  754M   0% /lib/init/rw
varrun                754M   96K  754M   1% /var/run
varlock               754M     0  754M   0% /var/lock
udev                  754M  152K  754M   1% /dev
tmpfs                 754M   84K  754M   1% /dev/shm
lrm                   754M  2.4M  752M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp


modifiedreality@modifiedreality-desktop:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93dd8dff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48316   388097246    7  HPFS/NTFS
/dev/sda2           48317       48641     2610562+   5  Extended
/dev/sda5           48317       48619     2433816   83  Linux
/dev/sda6           48620       48641      176683+  82  Linux swap / Solaris

```

---

### Post by drs305 on 2009-04-24
It says you installed it on a 2.3GB partition. Something got messed up during the installation. 

Your extended partition (sda2), which contains everything following, is very small and only large enough to accomodate the 2.3GB system and the swap partitions.

It looks like windows ended up with 390+GB of the drive. I don't see a 130GB partition listed in the results you mentioned.

You can run *testdisk* if you think the partition table is in error but it is likely the table is correct and something happened during the installation partitioning.

---

### Post by ScottBurnham on 2009-04-24
I have no idea what happened. I used the Vista tool to shrink my Vista partition to create a new partition. Vista showed the two partitions. so I installed Ubuntu on that on the new one. Not sure what I did during the install. oh well. I said screw and wiped out window and reinstalled ubuntu using the whole drive. I am going to pick a couple new hard drive up on pay day and I will just throw vista on that when I do. I only really need to use vista for my ipod/iphone and the rare chance I want to play a game.

---

