---
title: "Problems mounting a drive"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by egd on 2007-01-18
Hi

I've just returned from 5 weeks away and have discovered I'm unable to mount one of my hard drives which has a single partition /dev/sdg1.

Prior to going away it used to automount via fstab.  Trying to manually mount it now using "sudo mount /dev/sdg1 /media/sdg" results in:
mount: wrong fs type, bad option, bad superblock on /dev/sdg1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

I know the drive is formatted ext3 and gparted confirms same, as well as tells me there is about 73gb of data on the partition.

The only thing I recall doing prior to going away was to connect an external ATA drive via USB and copy some data to it to take away with me.

Looking at /var/log/ssylog (from a liveboot session) shows the following:
[SIZE=1]Jan 18 23:46:28 ubuntu kernel: [17181848.******] ata8: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
Jan 18 23:46:28 ubuntu kernel: [17181848.******] ata8: status=0x51 { DriveReady SeekComplete Error }
Jan 18 23:46:28 ubuntu kernel: [17181848.******] ata8: error=0x40 { UncorrectableError }
Jan 18 23:46:30 ubuntu kernel: [17181850.264000] ata8: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
Jan 18 23:46:30 ubuntu kernel: [17181850.264000] ata8: status=0x51 { DriveReady SeekComplete Error }
Jan 18 23:46:30 ubuntu kernel: [17181850.264000] ata8: error=0x40 { UncorrectableError }
Jan 18 23:46:32 ubuntu kernel: [17181852.108000] ata8: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
Jan 18 23:46:32 ubuntu kernel: [17181852.108000] ata8: status=0x51 { DriveReady SeekComplete Error }
Jan 18 23:46:32 ubuntu kernel: [17181852.108000] ata8: error=0x40 { UncorrectableError }
Jan 18 23:46:34 ubuntu kernel: [17181853.948000] ata8: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
Jan 18 23:46:34 ubuntu kernel: [17181853.948000] ata8: status=0x51 { DriveReady SeekComplete Error }
Jan 18 23:46:34 ubuntu kernel: [17181853.948000] ata8: error=0x40 { UncorrectableError }
Jan 18 23:46:36 ubuntu kernel: [17181855.788000] ata8: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
Jan 18 23:46:36 ubuntu kernel: [17181855.788000] ata8: status=0x51 { DriveReady SeekComplete Error }
Jan 18 23:46:36 ubuntu kernel: [17181855.788000] ata8: error=0x40 { UncorrectableError }
Jan 18 23:46:37 ubuntu kernel: [17181857.632000] ata8: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
Jan 18 23:46:37 ubuntu kernel: [17181857.632000] ata8: status=0x51 { DriveReady SeekComplete Error }
Jan 18 23:46:37 ubuntu kernel: [17181857.632000] ata8: error=0x40 { UncorrectableError }
Jan 18 23:46:37 ubuntu kernel: [17181857.632000] sd 7:0:0:0: SCSI error: return code = 0x8000002
Jan 18 23:46:37 ubuntu kernel: [17181857.632000] sdg: Current: sense key: Medium Error
Jan 18 23:46:37 ubuntu kernel: [17181857.632000]     Additional sense: Unrecovered read error - auto reallocate failed
Jan 18 23:46:37 ubuntu kernel: [17181857.632000] Info fld=0x30ff
Jan 18 23:46:37 ubuntu kernel: [17181857.632000] end_request: I/O error, dev sdg, sector 12543
Jan 18 23:46:37 ubuntu kernel: [17181857.632000] JBD: IO error reading journal superblock
Jan 18 23:46:37 ubuntu kernel: [17181857.632000] EXT3-fs: error loading journal.
[/SIZE]

The drive is close to brand new. Any ideas what all of this means and/or what my options are before I proceed down the path of an igoramus and try to repartition the drive (I've no idea what was on the drive so I guess I'll never miss it).

---

### Post by taurus on 2007-01-18
```
sudo fdisk -l
```

---

### Post by egd on 2007-01-18
> **taurus said:**
> ```
sudo fdisk -l
```

Disk /dev/sdg: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       30401   244196001   83  Linux

Now what?

---

### Post by taurus on 2007-01-18
What does your /etc/fstab look like?

```
cat /etc/fstab
```

---

### Post by egd on 2007-01-19
> **taurus said:**
> What does your /etc/fstab look like?

```
cat /etc/fstab
```

I've installed SuSE in place of Ubuntu (don't ask) so I don't have a configured fstab right now.  Irrespective, the partition won't mount.  I'm running all these tests from Edgy via a liveboot.

 sudo mke2fs -n /dev/sdg1
mke2fs 1.39 (29-May-2006)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
30539776 inodes, 61049000 blocks
3052450 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=62914560
1864 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872

~~~~~~~~~
sudo e2fsck -v -f -n /dev/sdg1
e2fsck 1.39 (29-May-2006)
/dev/sdg1: Attempt to read block from filesystem resulted in short read while reading block 1560

/dev/sdg1: Attempt to read block from filesystem resulted in short read reading journal superblock

e2fsck: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sdg1
~~~~~~~~~
sudo e2fsck -b 32768 -v -f -n /dev/sdg1
e2fsck 1.39 (29-May-2006)
/dev/sdg1: Attempt to read block from filesystem resulted in short read while reading block 1560

/dev/sdg1: Attempt to read block from filesystem resulted in short read reading journal superblock

e2fsck: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sdg1

---

