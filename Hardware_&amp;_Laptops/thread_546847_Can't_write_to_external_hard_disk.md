---
title: "Can't write to external hard disk"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by mrajmorgan on 2007-09-09
I realise this has been discussed numerous times but I don't know if every case is the same, and /etc/fstab is the last thing I want to mess up.

People have asked in the past for the output of ls -l /media, which is as follows:

**dr-xr-xr-x 1 root root 4096 2007-04-08 19:26 disk**

And also "cat /etc/fstab" which is as follows:

[B]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5b31f769-de89-461c-812c-38f33c413f74 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=da3202dd-4d42-4c0c-a188-8282a0fecf4b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
[/B]

I have tried "chmod u+rwx /media/disk" and this returns the message: **chmod: changing permissions of `/media/disk': Read-only file system**

This was done while logged in as root... I'm not sure in general if "sudo su root" extends it's permissions to the GUI so to speak, but I tried both in the console and using the GUI and nothing worked. 

It's USB 2.0 if that's of any importance...

Any ideas? 

Thanks,
Andrew

---

### Post by merlinus on 2007-09-09
What is the filesystem?

-merlin

---

### Post by ghantoos on 2007-09-09
it's not the best solution,

but you could try

sudo nautilus /media/disk

Cheers,

ghantoos

---

### Post by mrajmorgan on 2007-09-09
In my own endeavours I plugged it into my mothers windows computer, now that I have plugged it into my Linux computer it isn't showing up at all... this may have something to do with some other advice I received:

mkdir /mnt/external
mount -t vfat32 /media/disk /mnt/external

I can see it in the device manager, and apparently it's NTFS file system

---

### Post by taurus on 2007-09-09
> **mrajmorgan said:**
> In my own endeavours I plugged it into my mothers windows computer, now that I have plugged it into my Linux computer it isn't showing up at all... this may have something to do with some other advice I received:

mkdir /mnt/external
mount -t vfat32 /media/disk /mnt/external

I can see it in the device manager, and apparently it's NTFS file system

If it's ntfs, you can't mount it as vfat!  (And there is no such driver as vfat32).

```
sudo fdisk -l
```

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by ghantoos on 2007-09-09
> **mrajmorgan said:**
> 

mount -t vfat32 /media/disk /mnt/external


The mount command won't work this way,

you should enter something like,

sudo mount -t vfat /dev/sdb1 /mnt/external

Can you post the output of  "sudo fdisk -l", to check if the HD is visible to your system.

Cheers,

ghantoos

---

### Post by mrajmorgan on 2007-09-09
Ok, I finally got it, it is visible, 

[B]Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS[/B]

and I used ghantoos

**mount -t ntfs /dev/sdb1 /mnt/external**

and then 

**sudo nautilus /mnt/external** to view them in Nautilus, all worked great, but I still lack write privileges... I've tried chmod u+rwx /mnt/external, but no joy...

Thanks, 
Andrew

I only just noticed the link posted before, I followed that, installed ntfs-config and it had the option enable write privileges for external drives, I clicked ok, but it also hasn't helped any.

---

### Post by vanadium on 2007-09-09
ntfs is read-only in Linux. Very recently, the ntfs-3g driver that allows writing has been declared stable. If you want to write to ntfs, you have to install and enable ntfs-3g.

---

### Post by mrajmorgan on 2007-09-09
I already have it apparently since I use Fiesty...

---

### Post by mrajmorgan on 2007-09-09
Ok, all sorted now, thank you all very much for your help, for anyone who is experiencing a similar problem:

[https://help.ubuntu.com/community/Mo...irdPartyNTFS3G](https://help.ubuntu.com/community/Mo...irdPartyNTFS3G)

I followed the manual instructions on this, and as always, it worked like a charm. 

Thanks again, and good luck all,
Andrew

---

