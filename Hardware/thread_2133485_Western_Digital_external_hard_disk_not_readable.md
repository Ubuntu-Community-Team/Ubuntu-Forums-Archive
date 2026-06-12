---
title: "Western Digital external hard disk not readable"
date: 2013-04-08
forum: Hardware
---

### Post by Padre Maronno on 2013-04-08
Hi all!
I have a 1.5 TB western digital external hard disk, formatted as ext3, that is not accessible after mounting.
After I plug the device in, automount tries to mount and then I get the error message saying that it is unable to read the content (You don't have permissions).

It's not a matter of permissions (I think) as Nautilus marks the mount point as unreadable.

The output from desmg is as follows:

```
[   56.630454] usb 2-1.6: new high-speed USB device number 3 using ehci_hcd
[   57.738001] Initializing USB Mass Storage driver...
[   57.738100] scsi6 : usb-storage 2-1.6:1.0
[   57.738173] usbcore: registered new interface driver usb-storage
[   57.738174] USB Mass Storage support registered.
[   58.243002] usbcore: registered new interface driver uas
[   58.733516] scsi 6:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4
[   58.734749] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   58.735603] sd 6:0:0:0: [sdb] 2930272256 512-byte logical blocks: (1.50 TB/1.36 TiB)
[   58.736533] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   58.737543] sd 6:0:0:0: [sdb] Asking for cache data failed
[   58.737549] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   58.739296] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   58.740145] sd 6:0:0:0: [sdb] Asking for cache data failed
[   58.740148] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   58.766896]  sdb: sdb1
[   58.769126] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   58.769951] sd 6:0:0:0: [sdb] Asking for cache data failed
[   58.769957] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   58.769963] sd 6:0:0:0: [sdb] Attached SCSI disk
[   59.216607] kjournald starting.  Commit interval 5 seconds
[   59.217998] EXT3-fs (sdb1): using internal journal
[   59.218006] EXT3-fs (sdb1): mounted filesystem with ordered data mode
```

I executed e2fsck, it did a scan but the partition is still unreadable (even though is marked as clean).

Do you know if there is a way at least to recover the data (and/or if is possible to recover the HD as it is) ?

---

### Post by tgalati4 on 2013-04-08
Install *testdisk* and run *testdisk* and *photorec*, which is part of testdisk.  Proceed carefully.  It's better to snapshot the drive to another drive and operate on the snapshot.  You don't know when the disk will fail completely.

---

### Post by Padre Maronno on 2013-04-08
Hi tgalati4

Thank you for the suggestion!
How do you suggest me to do the snapshot? Will dd_rescue do the job?

PM.

---

### Post by Padre Maronno on 2013-04-10
Interesting enough, if I give *sudo fdisk -l *the WD HD (now /dev/sdc) is not recognized as ext3 partition:

```
Disk /dev/sdc: 1500.3 GB, 1500299395072 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930272256 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007b3d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  2930272255  1465135104    7  HPFS/NTFS/exFAT
```

What could be the corrupted bit? MBR, maybe?

PM.

---

### Post by Bashing-om on 2013-04-10
Padre Maronno; Hi !
This out put:
>  Device Boot      Start         End      Blocks   Id  System /dev/sdc1            2048  2930272255  1465135104    7  HPFS/NTFS/exFATsays Windows format.

I suggest you take the drive to a Windows machine and run Windows' diagnostics on it.[INDENT=2]
regards

[/INDENT]

---

### Post by Padre Maronno on 2013-04-10
> **Bashing-om said:**
> Padre Maronno; Hi !
This out put:
says Windows format.

I suggest you take the drive to a Windows machine and run Windows' diagnostics on it.[INDENT=2]
regards

[/INDENT]

That's the interesting bit. It says it is a windows partition but the drive has been formatted in ext3 a long time ago. Anyway windows doesn't recognise the partition. 

After running dd_rescue, copying all the data to a new drive, and running testdisk, it turns out that all the files are still there (haven't tried to copy anything though) so some meta information should be messed up...

---

### Post by Bashing-om on 2013-04-10
Padre Maronno; Wow, that indeed is strange. Got beyond me. One could swap out that superblock with the backup, but what if the back up super block is not good ? Might then be in a world of hurt ??
Others may have better advise; at this point I would clone that drive and work on the clone to retrieve my data // Then repair the original disk.[INDENT=2]just my opinion

[/INDENT]

---

### Post by tgalati4 on 2013-04-10
Run *testdisk* on the clone and see if it can recreate the partition table.  If it is successful, then you should be able to navigate your directory structure and see your files.  If not successful, then use *photorec* to recover files.  The file names will be random, but at least you will have recovered your user files.

---

### Post by Padre Maronno on 2013-04-11
> **tgalati4 said:**
> Run *testdisk* on the clone and see if it can recreate the partition table.  If it is successful, then you should be able to navigate your directory structure and see your files.  If not successful, then use *photorec* to recover files.  The file names will be random, but at least you will have recovered your user files.

I have already run testdisk and it retrieved the directory structure, thank god. Of course I am working on a cloned version of the disk.

I will try to rewrite the partition table (last time forbid saying "not possible to write blablabla" me but it could be an interference from gparted that was running concurrently). So you think is the partition table, not the superblock?

I am afraid I can do testing from Sunday onwards though, will keep you updated!

---

### Post by tgalati4 on 2013-04-11
It may not be able to write the partition if the drive is mounted--as in viewing file folders.  Unmount the drive then run gparted and write the partition table as you remember it.  If it fails, then you might have a problem on the drive with bad sectors located where the partition table is stored.  

The superblock is stored in multiple, defined locations.  Reference:  [http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html](http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html)

The partition table (as far as I know--reference:  [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)) is only located at the very beginning of the drive.  I have had drives with unreadable/unwriteable partition tables, but still able to read and write data to ext2--this was a while ago.  So I presume that as long as the kernel can read the superblock (or backup superblock) then you can access your files.  But if the first sector (Sector 0) is bad, then you may not be able to partition the drive or use it for a boot disk.  But it may be OK for data storage and backup.

You could try *fixmbr* using a Windows install or recovery CD.  Or Ultimate Boot CD, or several other tools.  Make sure your data is backed up to a decent/new disk before partitioning.

If *fixmbr* doesn't work, then I would presume that the disk is damaged at sector 0 and I don't know of any way to recover from that.

I'm glad you were able to clone the drive and practice recovery on the clone.  This is an important step in data recovery.

---

