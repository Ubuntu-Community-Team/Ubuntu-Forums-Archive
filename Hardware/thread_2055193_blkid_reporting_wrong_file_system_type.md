---
title: "blkid reporting wrong file system type"
date: 2012-09-08
forum: Hardware
---

### Post by TheFu on 2012-09-08
More of a curiosity than an issue for me.
On an Ubuntu x64 10.04.x machine, the blkid command seems to be reading stale information about file systems.  The problem partition is from a USB3 connected drive.

```
$ blkid
/dev/sdh5: LABEL="mybook" UUID="F21E9E5F1E9E1D23" TYPE="ntfs" 

```But I did a mkfs.ext4 on that partition a few weeks ago.
```
$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdh5            965291104 540102124 376155048  59% /Data/mybook

```and 
```
$ grep mybook /etc/fstab 
UUID=ab2dbf42-2408-4316-9e62-6ad18ae6013f       /Data/mybook    ext4    defaults        0       2
```and mount shows the truth:
```
$ mount
/dev/sdh5 on /Data/mybook type ext4 (rw)

```So there are 3 places that show it correctly as ext4, but **blkid** doesn't.  Is this the expected behavior?

---

### Post by dandnsmith on 2012-09-09
One more thing?
what is the partition entry flagged as? (and is it a GPT HDD?)

---

### Post by Morbius1 on 2012-09-09
Run blkid this way and see it it updates to the new information:
```
sudo blkid -c /dev/null
```

---

### Post by TheFu on 2012-09-09
Is it GPT or MBR?  I honestly do not know and don't recall.  

How can I tell?  

Only 1 HDD here was setup as GPT, but I can't recall if that was this one or not.  My ignorance about GPT got the better of me.  My fear that GTP wasn't completely supported by Linux tools had me use MBR on some newer HDDs.  Just found [http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)  a few minutes ago - the summary has gained my interest.

**I didn't change the partition type inside fdisk, **at least I don't recall doing that. Just did a **mkfs -t ext4 **over the existing partition regardless of the type.   That explains what I'm seeing.

```
$ sudo fdisk -l /dev/sdh

Disk /dev/sdh: 2000.4 GB, 2000365289472 bytes
255 heads, 63 sectors/track, 243197 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00021365

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      243197  1953479871    5  Extended
/dev/sdh5               1      122089   980678656    7  HPFS/NTFS
/dev/sdh6          122089      243197   972800191   83  Linux
```I can't really blame those tools for honoring what they were told.  When the drive isn't busy in a few days, I'll change that partition type.

Both sdh5 and sdh6 have ext4 FS now, but I started out planning to use this portable disk between different devices and some only support NTFS partitions.  Now that it is connected to a server, having a linux-based file system was important. The network devices can access over CIFS.

I'm in the process of swapping out an old software RAID5 with 4x320G (drives from 2006!!!) for 2x2TB disks as RAID1.  This USB3 drive will be for backups.   I started doing a burn in on the new disks yesterday, but it seems that new firmware is needed AND I'm very willing to change from MBR to GPT on them if that is a better idea.

Comments welcome.

---

### Post by The Cog on 2012-09-09
It is probably still tagged as ntfs in the partition table. Try ```
sudo fdisk -l
``` to list the partition table.

It that's it, you can use fdisk to correct it:
**sudo fdisk /dev/sdh** then **t** to change the type, then **5** for the partition number, then **83** for a Linux type.

---

