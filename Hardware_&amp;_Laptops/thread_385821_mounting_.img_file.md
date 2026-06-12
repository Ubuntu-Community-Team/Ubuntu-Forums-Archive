---
title: "mounting .img file"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by dhigger on 2007-03-16
I have used dd_rescue to try and recover a FAT32 external HDD which won't mount. dd_rescue successfully wrote a .img file to another (NTFS) external hard drive.

I am now having problems mounting the IMG, to browse / copy files out from it.

I have created a mount point, then used the [FONT="Courier New"]-o loop[/FONT] trick, and still [FONT="Courier New"]mount[/FONT] complains that I need to specify the filesystem type. Whatever I try (ntfs (which should be correct I think), hpfs, vfat), nothing works. The output of [FONT="Courier New"]dmesg | tail[/FONT] always has errors saying that no filesystem of that type was found.

Any ideas?! How can I get my files out of that .img file, which is on my NTFS HDD?

Help!

Here's what I've been trying: [FONT="Courier New"]sudo mount -o loop backup.img /mnt/recoverydata -t ntfs[/FONT]
and [FONT="Courier New"]sudo mount -o loop backup.img /mnt/recoverydata -t auto[/FONT]

---

### Post by taurus on 2007-03-16
```
sudo mount -t iso9660 -o loop backup.img /mnt/recoverydata
```

---

### Post by dhigger on 2007-03-16
I've tried this filesystem type too. Using the exact command you suggest, I get:

[FONT="Courier New"]mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/FONT]

And [FONT="Courier New"]dmesg | tail[/FONT]:

[FONT="Courier New"][17179691.228000] sda: assuming drive cache: write through
[17179691.232000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179691.232000] sda: Write Protect is off
[17179691.232000] sda: Mode Sense: 03 00 00 00
[17179691.232000] sda: assuming drive cache: write through
[17179691.236000]  sda: sda1
[17179697.216000] sd 0:0:0:0: Attached scsi disk sda
[17179697.244000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179988.016000] loop: loaded (max 8 devices)
[17179988.208000] Unable to identify CD-ROM format.[/FONT]

If I swap [FONT="Courier New"]iso9660[/FONT] for [FONT="Courier New"]ntfs[/FONT], [FONT="Courier New"]dmesg | tail[/FONT] then gives:

[FONT="Courier New"][17179691.236000]  sda: sda1
[17179697.216000] sd 0:0:0:0: Attached scsi disk sda
[17179697.244000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179988.016000] loop: loaded (max 8 devices)
[17179988.208000] Unable to identify CD-ROM format.
[17180162.096000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17180162.116000] NTFS-fs warning (device loop0): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17180162.116000] NTFS-fs error (device loop0): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180162.116000] NTFS-fs error (device loop0): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180162.116000] NTFS-fs error (device loop0): ntfs_fill_super(): Not an NTFS volume.[/FONT]

Any other ideas?

---

### Post by gray-squirrel on 2007-03-17
> **dhigger said:**
> I have used dd_rescue to try and recover a FAT32 external HDD which won't mount. dd_rescue successfully wrote a .img file to another (NTFS) external hard drive.

I am now having problems mounting the IMG, to browse / copy files out from it.

I have created a mount point, then used the [FONT="Courier New"]-o loop[/FONT] trick, and still [FONT="Courier New"]mount[/FONT] complains that I need to specify the filesystem type. Whatever I try (ntfs (which should be correct I think), hpfs, vfat), nothing works. The output of [FONT="Courier New"]dmesg | tail[/FONT] always has errors saying that no filesystem of that type was found.

Any ideas?! How can I get my files out of that .img file, which is on my NTFS HDD?

Help!

Here's what I've been trying: [FONT="Courier New"]sudo mount -o loop backup.img /mnt/recoverydata -t ntfs[/FONT]
and [FONT="Courier New"]sudo mount -o loop backup.img /mnt/recoverydata -t auto[/FONT]

The syntax looks correct (although I put the [FONT="Courier New"]-t[/FONT] option first, and by the way the [FONT="Courier New"]iso9660[/FONT] option is for CD and DVD images). . . 

I have question.  When you were obtaining your image, did you get an image of a particular partition, or the entire disk?  If it was a single partition then one of the above lines will suffice - unless there is a problem inside that actual partition image which also was in the partition on the hard disk.  If you obtained an image of the entire disk, you would need to specify which partition you want to access.   First, type ```
fdisk -l -u <drive>
``` to get a partition table of the imaged hard disk.  It will show the starting and ending sectors of your partitions.

Next take the starting sector of the partition you want to mount and multiply that by 512 (sector size for hard disks).  For example, if you want to mount the image for [FONT="Courier New"]hda1[/FONT], and saw in the partition table that it started on sector 63, you would then use 63 x 512 = 32256.

Then, mount the partition this way: ```
sudo mount -t ntfs -o loop,offset=32256 backup.img /mnt/recoverydata 
```

If you want to access different partition, you would replace 32256 with the appropriate number.

Let us know how this goes.

---

### Post by dhigger on 2007-03-18
Thanks for helping with this. Should I be applying the fdisk command on the image or on the malfunctioning external HDD?

**1. I tried the image:**

[FONT="Courier New"]fdisk -l -u backup.img[/FONT]

which produced:

[FONT="Courier New"]You must set cylinders.
You can do this from the extra functions menu.

Disk backup.img: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes

     Device Boot      Start         End      Blocks   Id  System
backup.img1   *          63   156296384    78148161    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(1022, 254, 63) logical=(9728, 254, 63)[/FONT]

There is only one partition on the malfunctioning HDD, and seeing a [FONT="Courier New"]Start[/FONT] of [FONT="Courier New"]63[/FONT] I tried:

[FONT="Courier New"]sudo mount -t ntfs -o loop,offset=32256 backup.img /mnt/recoverydata[/FONT]

which gives

[FONT="Courier New"]mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/FONT]

and [FONT="Courier New"]dmesg | tail[/FONT]:
[FONT="Courier New"]
[17182032.096000] sd 1:0:0:0: SCSI error: return code = 0x8000002
[17182032.096000] sdb: Current: sense key: Medium Error
[17182032.096000]     Additional sense: Unrecovered read error
[17182032.096000] end_request: I/O error, dev sdb, sector 63
[17182032.096000] Buffer I/O error on device sdb1, logical block 0
[17182044.908000] loop: loaded (max 8 devices)
[17182045.004000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17182045.036000] NTFS-fs error (device loop0): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17182045.036000] NTFS-fs error (device loop0): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17182045.036000] NTFS-fs error (device loop0): ntfs_fill_super(): Not an NTFS volume.
[/FONT]

Is is possible that because I can't mount the malfunctioning HDD, I won't be able to mount the [FONT="Courier New"]dd_rescue[/FONT]'d image of that drive? Incidentally, when I plug the malfunctioning HDD in, it never mounts, but clicks away for quite a while. Only after a long while does any [FONT="Courier New"]fdisk[/FONT] command work.

**2. I tried the malfunctioning HDD:**

[FONT="Courier New"]fdisk -l -u /dev/sda[/FONT]

which yielded:

[FONT="Courier New"]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156296384    78148161    c  W95 FAT32 (LBA)[/FONT]

So that's also a sector [FONT="Courier New"]63[/FONT] start. As a bit of a shot in the dark, I tried to mount the malfunctioning drive with

[FONT="Courier New"]sudo mount -t vfat -o loop,offset=32256 /dev/sda /mnt/recoverydata[/FONT]

which produces
[FONT="Courier New"]
mount: /dev/loop0: can't read superblock[/FONT]

and [FONT="Courier New"]dmesg | tail[/FONT], for good measure:

[FONT="Courier New"][17187168.852000] sda: Current: sense key: Medium Error
[17187168.852000]     Additional sense: Unrecovered read error
[17187168.852000] end_request: I/O error, dev sda, sector 56
[17187168.852000] Buffer I/O error on device sda, logical block 7
[17187219.684000] sd 3:0:0:0: SCSI error: return code = 0x8000002
[17187219.684000] sda: Current: sense key: Medium Error
[17187219.684000]     Additional sense: Unrecovered read error
[17187219.684000] end_request: I/O error, dev sda, sector 56
[17187219.684000] Buffer I/O error on device sda, logical block 7
[17187219.684000] FAT: unable to read boot sector[/FONT]


Have I done something wrong here? What about this [FONT="Courier New"]mount[/FONT] option [FONT="Courier New"]errors=recover[/FONT]? Is that appropriate for either the HDD or the [FONT="Courier New"]dd_rescue[/FONT]'d image?

---

### Post by dhigger on 2007-03-22
Bump...

How can I interrogate an .img file which won't mount?

---

### Post by gray-squirrel on 2007-03-25
I had to read everything carefully again.  At first I thought you were working with an NTFS image, until I saw the partition tables you posted.

Try this: 
```
sudo mount -t vfat -o loop,offset=32256 backup.img /mnt/recoverydata
```

I apologize, I would have suggested this earlier had I not misunderstood what was going on.

---

### Post by dhigger on 2007-03-26
Unfortunately that gives

[FONT="Courier New"]mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/FONT]

and [FONT="Courier New"]dmesg | tail[/FONT]

[FONT="Courier New"][17179767.396000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179767.396000] sda: Write Protect is off
[17179767.396000] sda: Mode Sense: 03 00 00 00
[17179767.396000] sda: assuming drive cache: write through
[17179767.400000]  sda: sda1
[17179767.404000] sd 0:0:0:0: Attached scsi disk sda
[17179767.428000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17180463.568000] loop: loaded (max 8 devices)
[17180463.632000] FAT: bogus number of reserved sectors
[17180463.632000] VFS: Can't find a valid FAT filesystem on dev loop0.[/FONT]

Any other suggestions?

---

### Post by 67comet on 2007-12-07
Bump

I'm experiencing very similar issues with my backup.img files. I've tried to mount them a plethora of ways, but I believe they are unfinished .img files so getting them mounted may not be possible.

Mine were taken from a 250gig hdd that was formated as xfs. I used  ddrescue to get all I could off sdd .. Not sdd1 .. Would have it been better to just taken the partition instead of the entire disk image?

Thanks much,
Justin

---

### Post by frego on 2007-12-29
After doing a dd_rescue, I would try mounting like this for NTFS:

sudo mount -t ntfs-3g -o force,loop /media/disk.img /mnt/recovered

of course, you must have the ntfs-3g installed. If it's a different file system, substitute the appropriate type in.  The -o force option will mount a partition that needs chkdsk run on it.

---

