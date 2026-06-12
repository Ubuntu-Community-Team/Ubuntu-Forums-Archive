---
title: "strange partition probs"
date: 2009-01-08
forum: Hardware
---

### Post by obmhost on 2009-01-08
Hi everyone - i'm new to this forum, hope i can find some help as i have a strange partition related problem.

I had a 750 GB external USB disk, this was almost full, (690GB)

WINDOWS somehow created a new partition on it. This stopped me from seeing any files, and prompted for me to format it.

I dumped windows in favour of Linux, I was formatting a 40GB drive called secondary for a server on a different USB port in the back of my PC.
Somehow windows formatted two drives in one format ??


Anyway I have since been trying to format the 750GB drive so i can transfer the data back onto it. I managed to successfully recover the data to an internal 1TB drive.

I've run into all kinds of probs.

sudo cfdisk /dev/sda2 

error on run of above command :
FATAL ERROR: Bad primary partition 0: Partition ends after end-of-disk

help!


sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5fca6ccf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         383     3072000   12  Compaq diagnostics
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         383       19458   153216000    7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?       13578      119522   850995205    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sdc4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

----
df -h

Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G   11G  1.8G  86% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  104K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.9M  498M   1% /dev
tmpfs                 501M  224K  501M   1% /dev/shm
/dev/sda2             147G   63G   84G  43% /host
lrm                   501M  2.0M  499M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda2             147G   63G   84G  43% /windows
/dev/sda2             147G   63G   84G  43% /media/secondary


new to linux so this is all new to me. 
I am running an Advent 4213 on Ubuntu 8.10
I have mounted the windows partition in fstab but that is all.

I tried :
mount -t ntfs-3g /dev/sda2 /media/secondary -o force

as i saw it on the forum somewhere. but no joy.
All i want is to format the drive !

appreciate any advice anyone can give.
If you need more details just reply..

---

### Post by theinnercityhippy on 2009-01-08
If you have backed up you could try a low level format which should remove the partition tables using dd

```
sudo dd if=/dev/zero of=/dev/sda
```
```

mkfs.ext3 /dev/sda
```

---

### Post by obmhost on 2009-01-08
Thanks will try this.

---

### Post by obmhost on 2009-01-08
cheers for the quick reply

dev/sda ?

is this the external drive?

had to check, don't want to format my internal main disk

i thought it was dev/sdc  for my external drive.

need top be sure !

---

