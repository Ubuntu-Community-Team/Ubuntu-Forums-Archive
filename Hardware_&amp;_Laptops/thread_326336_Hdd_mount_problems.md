---
title: "Hdd mount problems"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by Talako on 2006-12-27
Hi all
just got a 120GB hdd for christmas, I made 4 partitions as follows:
hda1 linux-swap 1.95GB
hda4 ext3          18.55GB <-- Linux Partition
hda2 fat32         19.53GB <-- Windows Partition
hda3 ext3          71.75GB <-- Shared Partition

I'm kindof a noob when it comes to mounting/editing fstab, so here's the problem: Windows recognizes all of the partitions (i installed drivers for ext3), but when I boot to Ubuntu (Edgy), it doesn't recognize the other 2 partitions:-k , before I updated to Edgy, it recognized them, but wouldn't mount them because it said they weren't removable drives (uh-duh)](*,) , so it couldn't pmount. I need help on how to edit fstab or w/e to recognize the drives.
Please help, thanks
Talako

---

### Post by taurus on 2006-12-27
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Talako on 2006-12-27
I looked at that website, the problem is that I don't have the other partitions in my fstab, here's the coding:
fdisk:
```

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         255     2048256   82  Linux swap / Solaris
/dev/hda2   *        2678        5227    20482875    c  W95 FAT32 (LBA)
/dev/hda3            5228       14593    75232395   83  Linux
/dev/hda4             256        2677    19454715   83  Linux

```

fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4 -- converted during upgrade to edgy
UUID=36c14f25-2b46-4c67-b355-c0ed8faeb47a / ext3 defaults,errors=remo$
# /dev/hda1 -- converted during upgrade to edgy
UUID=603af087-6372-4792-978b-77368a7a4d45 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

what should i put in for these fields? Is there a way to force Ubuntu to set all the remaining partitions into fstab?
thanks so far

---

### Post by taurus on 2006-12-27
So you want to mount /dev/hda2 & /dev/hda3...

From a terminal, open /etc/fstab so you can edit it.

```
gksudo gedit /etc/fstab
```
Then, add the following two lines to the end of it.

```

/dev/hda2   /media/hda2   vfat   iocharset=utf8,umask=000   0   0
/dev/hda3   /media/hda3   ext3   defaults   0   1

```
Save it and create two new mount points for those two partitions and mount them.

```
sudo mkdir /media/hda2  /media/hda3
sudo mount -a
df -h
```

---

### Post by Talako on 2006-12-27
YAY! Much better now, thanks taurus! One last question, last time I made a shared partition, my linux files kept getting overwritten when I booted into Windows, I'm pretty sure it has something to do with permissions, but I don't know how/where to change them, or if I should make the partition in linux under gparted. Any ideas?
Thanks again

---

### Post by taurus on 2006-12-27
Maybe you need to look into Windows to make sure it doesn't format or erase stuff from that share partition.

---

### Post by Talako on 2006-12-27
Ok, I'll go and fiddle with Windows a little bit. Thanks for your help, taurus.

---

### Post by taurus on 2006-12-27
> **Talako said:**
> Ok, I'll go and fiddle with Windows a little bit. Thanks for your help, taurus.
You're welcome.

---

