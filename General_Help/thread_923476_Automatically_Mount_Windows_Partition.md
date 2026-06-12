---
title: "Automatically Mount Windows Partition?"
date: 2008-09-18
forum: General Help
---

### Post by TheSe7enthProphet on 2008-09-18
Hello, all!

I'm using Ubuntu on a machine dual-booting with Windows, and all of my music is on the Windows partition. This can be frustrating when I try to listen to my music after forgetting to mount the partition that it is on, haha. 

So, I was wondering if there is an easy way to mount drives when I boot or log in? 

Thanks for any help!

---

### Post by karlr42 on 2008-09-18
```
sudo gedit /etc/fstab
```
Add the following to the end:
```
/dev/<windows drive>	/media/disk	ntfs	auto,user,exec,rw	0	0
```
Don't know which is the Windows drive?
```
sudo fdisk -l
```
and find the one which is ntfs type. 

Once it's edited, reboot and see if it mounts. Let me know if it doesn't.

Example: 
my fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          15      120456   de  Dell Utility
/dev/sda2   *          16       10532    84477802+   7  HPFS/NTFS
/dev/sda3           10533       19131    69071467+   f  W95 Ext'd (LBA)
/dev/sda4           19132       19457     2618595   82  Linux swap / Solaris
/dev/sda5           11224       19131    63521010   83  Linux
/dev/sda6           10533       11223     5550394+  83  Linux

Partition table entries are not in disk order

```
So, /dev/sda2 is my Windows drive. So I'd add:
```
/dev/sda2	/media/disk	ntfs	auto,user,exec,rw	0	0
``` to fstab. QED

---

### Post by LowSky on 2008-09-18
make it simple, under add/remove. install NTFS-Config

To run Application>system> NTFS config

turn on auto mount

---

### Post by TheSe7enthProphet on 2008-09-18
> **karlr42 said:**
> ```
sudo gedit /etc/fstab
```
Add the following to the end:
```
/dev/<windows drive>	/media/disk	ntfs	auto,user,exec,rw	0	0
```
Don't know which is the Windows drive?
```
sudo fdisk -l
```
and find the one which is ntfs type. 

Once it's edited, reboot and see if it mounts. Let me know if it doesn't.

Example: 
my fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          15      120456   de  Dell Utility
/dev/sda2   *          16       10532    84477802+   7  HPFS/NTFS
/dev/sda3           10533       19131    69071467+   f  W95 Ext'd (LBA)
/dev/sda4           19132       19457     2618595   82  Linux swap / Solaris
/dev/sda5           11224       19131    63521010   83  Linux
/dev/sda6           10533       11223     5550394+  83  Linux

Partition table entries are not in disk order

```
So, /dev/sda2 is my Windows drive. So I'd add:
```
/dev/sda2	/media/disk	ntfs	auto,user,exec,rw	0	0
``` to fstab. QED

Sorry for taking so long to reply.

When I ran fdisk, I got:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2              11        1316    10485760    7  HPFS/NTFS
/dev/sda3   *        1316       35324   273167352    7  HPFS/NTFS
/dev/sda4           35325       38914    28829795+   f  W95 Ext'd (LBA)
/dev/sda5           38587       38914     2620416   dd  Unknown
/dev/sda6           35325       38363    24410736   83  Linux
/dev/sda7           38364       38545     1461883+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

So I added the following line to /etc/fstab:

```
/dev/sda3	/media/disk	ntfs	auto,user,exec,rw	0	0
```

I then restarted. The Windows drive didn't mount. Did I do it right?

Thanks for your reply!

> **LowSky said:**
> make it simple, under add/remove. install NTFS-Config

To run Application>system> NTFS config

turn on auto mount

Thanks, also, for your reply! If I can't get the method karlr42's post to work, I'll go with this.

---

### Post by pretzelboy on 2008-09-18
I'm trying to do the same thing only I have 2 other (physically seperate) NTFS drives.
Normally I would add these to fstab.

Ubuntu is confusing me however because I don't see them listed in fstab, yet I can mount or unmount them from places or using the "Diskmounter" applet.

So where is Ubuntu getting the mount information from if not from fstab?

In short, want them to mount automatically but I don't want to screw up the system by adding them to fstab if they have been specified elsewhere as well.
TIA

---

