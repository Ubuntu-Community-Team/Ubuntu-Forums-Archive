---
title: "&quot;Invalid mount option when attempting to mount the volume 'xxx'&quot; error"
date: 2008-11-09
forum: Hardware
---

### Post by frank.zappa on 2008-11-09
When trying to mount my 'Acer' or 'XP' partition, I get the error: "Invalid mount option when attempting to mount the volume 'xxx'".

I searched Google with the same error message and it directed me to someone else's thread here on UF where the person posted their fstab.
```

Here's mine: 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```
The first partition on my laptop is my Vista parition (Acer), then second is XP (XP), and last is Debian (Filesystem) and no swap partiton.

I'm guessing I should add /dev/sda1 and /dev/sda2 but I'm not sure what to put in for mount point and type, etc.

---

### Post by taurus on 2008-11-09
Can you post the partition table of your harddrive?

```
sudo fdisk -l
```

---

### Post by frank.zappa on 2008-11-09
Sure:
```

sam@debian:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x675cfa63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12161    97683201    7  HPFS/NTFS
/dev/sda2           12162       22363    81947565    7  HPFS/NTFS
/dev/sda3           22364       24321    15727635   83  Linux

```

---

### Post by taurus on 2008-11-09
So you want to mount those two ntfs partitions.  The easiest way is to install ntfs-config and use it to add two entries in /etc/fstab so they will be mounted automatically each time you boot Ubuntu. 

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```
Looks like you don't have a swap partition, eh!

---

### Post by frank.zappa on 2008-11-09
It'll work with Debian too right?
Well I had OS X running on here too and you can only have 4 primary partitions right? and I thought with 2GBs of RAM I wouldn't really need it, seeing as I don't do anything other than programming in Linux.

And thanks for the help.

Edit: Oh and I don't want to auto-mount the partitions when I boot up, are there options for that too?

---

### Post by shacristo on 2008-11-09
To prevent them from being mounted when you boot just add noauto to the list of options.

---

### Post by pastalavista on 2008-11-09
The most likely reason the drives can't be mounted is because Windows wsn't shutdown "cleanly", meaning one application or another had to be forced. Try rebooting into Windows first and make sure it shuts down totally. Close as many applications manually before shut-down. If some Windows application isn't cooperating, fix it or uninstall it.

---

### Post by frank.zappa on 2008-11-09
No, Windows was shut down cleanly, it's because the partitions aren't listed under /etc/fstab. I just wanted to know what parameters to add when I edit fstab but I found a handy community doc here: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) 

But thanks for the help.

---

### Post by pastalavista on 2008-11-09
The drives weren't listed because they weren't recognized. They can be force mounted anyway, but they would have been mounted automatically if Windows was finished with them. Good luck. I'm sure you'll get 'er done.

---

### Post by frank.zappa on 2008-11-09
Ok now I've edited my fstab to look like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1	/media/Acer	ntfs-3g	user,noauto	0	0
/dev/sda2	/media/XP	ntfs-3g	user,noauto	0	0		
/dev/sda3       /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```
but when I tried to mount my XP partition, it said I needed to install ntfs support. So I opened up Synaptic and installed ntfs-3g. But now when I try to mount either partition, i get:
**Cannot mount Volume.**
Unable to mount the volume 'XP'.
Error opening '/dev/sda2': Permission denied
Failed to mount '/dev/sda2': Permission denied
Please check '/dev/sda2' and the ntfs-3g binary permissions, and the mounting user ID. More information is provided at [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

I tried what it said:
```
chown root $(which ntfs-3g)
chmod 4755 $(which ntfs-3g)

```and it didn't make a difference.

---

### Post by taurus on 2008-11-09
Do you have those two mount points, /media/Acer & /media/XP?

```
sudo mkdir /media/Acer /media/XP
```

---

### Post by frank.zappa on 2008-11-09
> **taurus said:**
> Do you have those two mount points, /media/Acer & /media/XP?

```
sudo mkdir /media/Acer /media/XP
```
Yes I have /media/Acer and /media/XP, those were the first directories I made before even editing my fstab. 

So now I can mount and unmount either partition using:
```
$ sudo mount /dev/sda1 /dev/sda2
$ sudo umount /dev/sda1 /dev/sda2
```
But the thing is, if I click a shortcut to either disk, I get the error.

---

