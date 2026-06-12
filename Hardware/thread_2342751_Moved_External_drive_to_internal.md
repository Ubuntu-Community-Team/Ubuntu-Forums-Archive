---
title: "Moved External drive to internal"
date: 2016-11-09
forum: Hardware
---

### Post by semperfratres on 2016-11-09
I have recently moved an external HDD to internal and am now having trouble getting it mounted.
I can see it in Disks, but am unable to mount it from there.
I have tried everything from this page ([https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)) with the exception of formatting it.
When I do ```
sudo  mount -a
``` it tells me that the mount point does not exist.

Any help I can get would be greatly appreciated.

[IMG]http://i.imgur.com/qzMYozD.png[/IMG]

---

### Post by oldfred on 2016-11-09
If you use Nautilus and click on a folder it will auto mount it in /media/$USER/UUID or label.

But if an internal drive, you probably want to have it auto mount on reboot, so then you have to add to fstab.
You then have to create a mount point like /mnt/data or /media/data.
Often best not to use spaces as then with Linux you have to escape or use ASCII code for  the space or use quotes every time.

I prefer to mount the partition and link the folders into /home. But you can just mount each folder or just mount partition and manually drill down to folders in partition. One advantage to /mnt/data is that folder will not be shown twice in Nautilus second time with underscore and will not work.

What is format of partition(s) on drive? If NTFS you can only set ownership & permissions as part of mount. If Linux format, you may have to set your own permissions & ownership.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

 [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) 
      
 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Bashing-om on 2016-11-09
semperfratres; Hello'

Yes, if you are to mount the drive that is now internal, you must declare a mount point and tell the system to attach this file system to the installed file system. A couple of ways one can do this, Depending on what the end goal here is . Me, I prefer to mount my storage drives as " on-demand " rather then always mounted when booted up .

As it is now internal, I prefer the mount point to be in the traditional point of the /mnt directory ; though this mount point can be anywhere , inclusive of /media.

For now, let us see what we can do with the current mount point.
Post back the results of terminal commands:
```

sudo parted -l
ls -al /media
ls -al /media/<username>/

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Which will tell us where and what file system we are dealing with .. and if there exist a mount point .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by slickymaster on 2016-11-09
Threads merged.

Please do not create duplicate threads (in your case it's actually triplicate), it dilutes the community&#8217;s efforts to provide support and causes confusion.

---

### Post by semperfratres on 2016-11-10
Sorry about that slickymaster. When I posted, I kept getting a screen that said that the forums were down. Did that twice before I actually saw that it posted and had no idea that it had already done so.

> **Bashing-om said:**
> semperfratres; Hello'

Yes, if you are to mount the drive that is now internal, you must declare a mount point and tell the system to attach this file system to the installed file system. A couple of ways one can do this, Depending on what the end goal here is . Me, I prefer to mount my storage drives as " on-demand " rather then always mounted when booted up .

As it is now internal, I prefer the mount point to be in the traditional point of the /mnt directory ; though this mount point can be anywhere , inclusive of /media.

For now, let us see what we can do with the current mount point.
Post back the results of terminal commands:
```

sudo parted -l
ls -al /media
ls -al /media/<username>/

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Which will tell us where and what file system we are dealing with .. and if there exist a mount point .[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


sudo parted -l gives me the following info on the drive in question:
```
Model: ATA WDC WD30EZRX-00D (scsi)
Disk /dev/sde: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start  End    Size   Type     File system  Flags
 1      131kB  375GB  375GB  primary
```
 
 ls -al /media gives me the following info:
 ```
total 20
drwxr-xr-x   5 root root 4096 Nov  7 22:07 .
drwxr-xr-x  24 root root 4096 Nov  9 15:38 ..
drwxr-x---+  2 root root 4096 Aug 29 21:53 guest-qfhvkn
drwxr-x---+  7 root root 4096 Nov  8 22:34 tim
drwxr-xr-x   2 root root 4096 Nov  7 22:07 WesternDigital
```




la -al /media/tim gives me the following info:
```
drwxr-x---+ 7 root root  4096 Nov  8 22:34 .
drwxr-xr-x  5 root root  4096 Nov  7 22:07 ..
drwxrwxrwx  1 tim  tim   4096 Aug 26 23:18 Cartoons Fitness Reality
drwx------  3 tim  tim   4096 Nov  7 21:53 HGST1
drwxrwxr-x  2 root root  4096 Sep 12 15:08 Movies PremiumTV
drwxr-xr-x  2 root root  4096 Sep 12 15:08 SitCom Drama
drwxrwxrwx  1 tim  tim  12288 Sep  1 06:57 SitCom Drama1
```


All of my drives, external and internal are mounting at boot, except Movies PremiumTV
Sitcom Drama/Sitcom Drama1 is the only external drive now.
(I dont know why there are two of those. Sitcom Drama1 is the one that shows files)


The drive in question is NTFS, although Disks is telling me it is HPFS/NTSF. I have no idea what HPFS is.
The HGST1 is a brand new drive that I just installed and it mounts with no issues.

> **oldfred said:**
> If you use Nautilus and click on a folder it will auto mount it in /media/$USER/UUID or label.

But if an internal drive, you probably want to have it auto mount on reboot, so then you have to add to fstab.
You then have to create a mount point like /mnt/data or /media/data.
Often best not to use spaces as then with Linux you have to escape or use ASCII code for  the space or use quotes every time.

I prefer to mount the partition and link the folders into /home. But you can just mount each folder or just mount partition and manually drill down to folders in partition. One advantage to /mnt/data is that folder will not be shown twice in Nautilus second time with underscore and will not work.

What is format of partition(s) on drive? If NTFS you can only set ownership & permissions as part of mount. If Linux format, you may have to set your own permissions & ownership.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

 [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) 
      
 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)



As I use this for my Plex, I need it to mount automatically at boot. I have tried to add it to fstab, but I am only getting a partial UUID. When I try to add it as /dev/sde (as shown in Disks),
my PC wont boot into the OS. I had to remove the input via nano from root.


As stated in my previous post, I followed the directions in the link I posted and did create a mount point.
When I previously used "blkid", it only returned a partial UUID for that drive.
As of this morning, it isn't even showing that drive (sde1):

```
tim@plex:~$ blkid
/dev/sda1: UUID="7a69cf3d-a111-45f5-8db9-c50468f2548c" TYPE="ext2" PARTUUID="7fcdeef2-01"
/dev/sda5: UUID="QVHezb-Lm15-VEFa-8scx-jXDE-mwHq-LPJv8m" TYPE="LVM2_member" PARTUUID="7fcdeef2-05"
/dev/sdb1: LABEL="Classic SitCom" UUID="B4DA0878DA0838DE" TYPE="ntfs" PARTUUID="38943d93-01"
/dev/sdc1: LABEL="Cartoons Fitness Reality" UUID="DC96E0AE96E08A7A" TYPE="ntfs" PARTUUID="38943d9c-01"
/dev/sdd: LABEL="HGST1" UUID="daaa4a2a-d7d7-4196-b8e6-fcfa3e5c44fb" TYPE="ext4"
/dev/sdf1: LABEL="SitCom Drama" UUID="CC3AC5F33AC5DA9A" TYPE="ntfs"
/dev/mapper/ubuntu--vg-root: UUID="1319cd58-e47e-484b-b937-2e64aa24f333" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="62b0c6c6-f0cf-4d89-bdf3-e6de6cfe2939" TYPE="swap"
/dev/dm-1: UUID="62b0c6c6-f0cf-4d89-bdf3-e6de6cfe2939" TYPE="swap"
```

---

### Post by oldfred on 2016-11-10
This is a problem.

Disk /dev/sde: [COLOR=#ff0000]3001GB[/COLOR]
Sector size (logical/physical): 512B/4096B
Partition Table: [COLOR=#ff0000]msdos[/COLOR]

You cannot have MBR(msdos) with a drive over 2TiB. But for compatibility with XP some vendors created proprietary ways to use MBR.

 [URL="http://en.wikipedia.org/wiki/GUID_Partition_Table"]http://en.wikipedia.org/wiki/GUID_Partition_Table
[/URL]
 MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record) 

You may be able to convert, but if proprietary scheme it may not work. Or make sure you have good backups.

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 

[URL="http://en.wikipedia.org/wiki/GUID_Partition_Table"]
[/URL] What is sdd? It looks like a formatted drive without partitions, which leads to issues. 
Systems first look for partition table and if not found some things just do not work.

---

### Post by semperfratres on 2016-11-10
> **oldfred said:**
> This is a problem.

Disk /dev/sde: [COLOR=#ff0000]3001GB[/COLOR]
Sector size (logical/physical): 512B/4096B
Partition Table: [COLOR=#ff0000]msdos[/COLOR]

You cannot have MBR(msdos) with a drive over 2TiB. But for compatibility with XP some vendors created proprietary ways to use MBR.

 [URL="http://en.wikipedia.org/wiki/GUID_Partition_Table"]http://en.wikipedia.org/wiki/GUID_Partition_Table
[/URL]
 MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record) 

You may be able to convert, but if proprietary scheme it may not work. Or make sure you have good backups.

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 

[URL="http://en.wikipedia.org/wiki/GUID_Partition_Table"]
[/URL] What is sdd? It looks like a formatted drive without partitions, which leads to issues. 
Systems first look for partition table and if not found some things just do not work.

I'm not exactly sure how that was formatted to msdos. It was an external drive that containes my movies.


/sdd is the most recent drive I have installed that has one partition formatted to ext4. It is mounted fine.

---

