---
title: "Shifting mount points"
date: 2008-08-29
forum: General Help
---

### Post by paradexes on 2008-08-29
I am at the end of my rope here. I am having this issue where every time I reboot my mount points shift. 

/dev/sda1 could be /dev/sdm1 on the next boot or any other mount point in between. Quite an aggravating situation. I was unable to find anything that specifically described this issue. 

While for my fixed drives this is not a problem as my FSTAB is setup by UUID, I have issues with my eSATA (setup in a softraid setup) and USB drives which are semi fixed. 

This is the output of fdisk -l (which incidentally changes every time I reboot)

```
root@paradexes:~# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000faac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00024919

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000383e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002748a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c342e

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdf: 0 MB, 327680 bytes
255 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table

Disk /dev/sdk: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e57ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1   *           1       18662   149902483+  83  Linux
/dev/sdk2           18663       19457     6385837+   5  Extended
/dev/sdk5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdl: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000943f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1   *           1       48641   390708801   83  Linux

Disk /dev/sdm: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00050e47

   Device Boot      Start         End      Blocks   Id  System
/dev/sdm1   *           1       30401   244196001   83  Linux

Disk /dev/sdn: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000a504

   Device Boot      Start         End      Blocks   Id  System
/dev/sdn1   *           1       91201   732572001   83  Linux

Disk /dev/sdo: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6324

   Device Boot      Start         End      Blocks   Id  System
/dev/sdo1               1       30402   244196352    7  HPFS/NTFS

```

The contents of my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UID=ee96f702-12ef-4ab6-ac23-cc348408e1fe /               ext3    relatime,error$
# /dev/sda5
UUID=e190574e-326e-4b8b-b757-9b56a963a35f none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
UUID=9e468ea2-a188-44b3-8b28-a60e5e3174be       /media/sdb      ext3 defaults,d$
UUID=ba2bbb37-5111-4f08-8cb3-c78f64f16e3e       /media/sdc      reiserfs defaul$
UUID=42d8e45d-9aae-4878-b00f-fa25b0e69db7       /media/sdd      reiserfs defaul$
#/dev/sdk1      /media/USBNAS   ext3 defaults,data=writeback 0 0
#/dev/sdi1      /media/USBNAS   ext3 defaults,data=writeback 0 0
/dev/md0         /media/3tb     ext3 users,rw,auto,data=writeback 0 0
#UUID=8ab2e558-6e0a-475b-81cb-913ca22035e4

```

If adding those drives by UUID is the way to go what would the file system name be? I am using mdadm for softraid here. I have the /dev/md0 mount point setup. But I cant use it because the other drives are not setup there. 

Shifting mount points is one really annoying bug when I reboot the machine. Alternatively is there a way to disable this ability for Ubuntu shift mounts like this?

Any help is appreciated.

---

### Post by mssever on 2008-08-29
> **paradexes said:**
> I am at the end of my rope here. I am having this issue where every time I reboot my mount points shift. 
I don't have a solution, but I have a workaround that *might* work. If you look in /dev/disk, you'll find several different ways to identify your device. You can use one of those in your fstab.

---

### Post by drs305 on 2008-08-29
I don't use RAID but I think you can solve your problems by using labels to reference these drives in fstab. Shifting mount points is one of the reasons removable drives/external drives aren't listed by default in fstab. But if you use either UUIDs or labels to mount the devices the labels won't change and you can get some consistency in your mounts.

If you decide to label the devices, there are differing apps used to label them. Ext2/3 uses tune2fs, NTFS uses ntfslabel from the ntfsprogs app, and vfat uses mkfs.vat.

Here is a good link on how to label all of them:
[Understanding Fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Vivaldi Gloria on 2008-08-29
> **paradexes said:**
> If adding those drives by UUID is the way to go what would the file system name be?

How about ext3?

---

