---
title: "Two linux OS on top of win vista"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by augustine.samuel on 2009-07-15
I have two questions! 

I installed linux mint OS on my laptop which orginally has windows vista in dual mode. Mint dint solve my purpose and I wanted to install Ubuntu linux. I searched in forum and it instructed me to install top of it and it should be fine. I did it and now I have 3 OS in my system. I want to remove Linux Mint OS from my system. What should I do?

When I istalled Ubuntu, I guess I dint alocate good space in that partition. now I have only 130 MB left. How can I increase this partition to install some applications or upgrades.

Thanks a lot for help
Sam!

---

### Post by ramnarayan on 2009-07-15
> **augustine.samuel said:**
> I have two questions! 

When I istalled Ubuntu, I guess I dint alocate good space in that partition. now I have only 130 MB left. How can I increase this partition to install some applications or upgrades.

Thanks a lot for help
Sam!

depends on your partitioning

post the results of this command
```
sudo df -h
```

this will tell us exactly where mint it and if doing away with it will affect your Bootloader or not

Though i think if you installed Ubuntu second (or over Mint) it would have overwrittent Mint.

So what you can do is boot into Ubuntu

go to System ->Administration -> Partition Manager and use that (very carefully) to blow away mint and then use the free space for what yu want

If partition manager is not there install it via synaptic

System ->Administration -> Synaptic

---

### Post by ajgreeny on 2009-07-15
Show us the output from the command ```
sudo fdisk -l
```This will tell us if you still have Mint on the disk or if you overwrote it with ubuntu, as well as the partition sizes.

It would also be useful if you booted to the live ubuntu CD, and run System >Administration >Partition Editor (or even install gparted on your installed ubuntu) and attach a screenshot to this thread.  This will not only show the partitions, but also exactly how they are arranged on disk, which will be helpful if we need to suggest deletion of any of them.

---

### Post by augustine.samuel on 2009-07-16
> **ramnarayan said:**
> depends on your partitioning

post the results of this command
```
sudo df -h
```

this will tell us exactly where mint it and if doing away with it will affect your Bootloader or not

Though i think if you installed Ubuntu second (or over Mint) it would have overwrittent Mint.

So what you can do is boot into Ubuntu

go to System ->Administration -> Partition Manager and use that (very carefully) to blow away mint and then use the free space for what yu want

If partition manager is not there install it via synaptic

System ->Administration -> Synaptic
**Output for "sudo df -h"**
 
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda10            2.3G  2.2G   77M  97% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  128K 1002M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  184K 1002M   1% /dev
tmpfs                1003M  120K 1002M   1% /dev/shm
lrm                  1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile

---

### Post by augustine.samuel on 2009-07-16
**Output of "sudo fdisk -l"**
 
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1280    10240000    7  HPFS/NTFS
/dev/sda3   *        1280        7482    49817408    7  HPFS/NTFS
/dev/sda4            7483       19457    96189187+   f  W95 Ext'd (LBA)
/dev/sda5            7809        9781    15846404    7  HPFS/NTFS
/dev/sda6            9781       11724    15606784    7  HPFS/NTFS
/dev/sda7           11725       19131    59496696    7  HPFS/NTFS
/dev/sda8           19132       19435     2441848+  83  Linux
/dev/sda9           19436       19457      176683+  82  Linux swap / Solaris
/dev/sda10           7483        7786     2441817   83  Linux
/dev/sda11           7787        7808      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order


Here you go. I have attached the screenshort of gparted as well. Please suggest me how to proceed. note that one of the partition in my hard disk has the name Linux. Thanks for your help!

Sam!

---

### Post by ajgreeny on 2009-07-16
You certainly appear to have got into a bit of a muddle on your disk, with 6 different partitions of either fat16 or ntfs for windows.  Is that the way the machine came to you or have you increased the number of partitions for windows yourself?

As you said,you also have two installs of linux, neither of which will really be usable because you have not got enough space for either one of them.

What exactly is in partitions sda5, 6, and 7, all of which are ntfs, but are not the device with the boot flag, which is where your windows OS install must be.  I assume they must be data partitions, but it looks from gparted as if they are completely empty.

If so the simplest way forward would be to use gparted to delete all your partitions within the extended sda4, ie sda5, 6, 7, 8, 9, 10, and 11, and start again with ubuntu.  You can make another ntfs partition for data to share between the two OSs if you want, and keep that next to the current sda3, but then make use of the ree space with sda4 for your ubuntu, installing according to the default if you prefer, or better using manual partitioning, though you may wish to keep away from that for the moment until you are better aquainted with ubuntu and the business of partitions etc etc.

If you want to know more about manual partitioning and all that is involved have a look at [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by augustine.samuel on 2009-07-17
Thanks for the detailed explanation. I managed to rip off all the unwanted partition and installed Ubuntu again without loosing any of my data :). Now is looks perfect and ready to go with Linux. Thanks once again!!

---

### Post by ajgreeny on 2009-07-17
Great!  My pleasure.

---

