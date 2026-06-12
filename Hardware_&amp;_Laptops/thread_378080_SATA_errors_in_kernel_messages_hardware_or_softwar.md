---
title: "SATA errors in kernel messages hardware or software problem?"
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by skiloup on 2007-03-06
I have an Inspiron 6400 with a Western Digital SATA drive running Edgy with kernel version 2.6.17.10-generic (not 11-generic, because I had a problem with my video driver and wireless combination using it).

When going through the install process with an ext3 fs, the system would hang, and I would get i/o error messages.  I finally got the install to work properly if I used jfs.  No biggie right?

Now at random my filesystem becomes readonly.  (My fstab is set to remount the partition as readonly on error, so that is why that is happening.) 
But once the error happens, if I happen to have a shell up, if I check my kernel messages with $dmesg I get the following dump:

> [17197355.948000] end_request: I/O error, dev sda, sector 177702072
[17197355.948000] Buffer I/O error on device sda2, logical block 452716
[17197358.748000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[17197358.748000] ata1: status=0x51 { DriveReady SeekComplete Error }
[17197358.748000] ata1: error=0x40 { UncorrectableError }
[17197361.344000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[17197361.344000] ata1: status=0x51 { DriveReady SeekComplete Error }
[17197361.344000] ata1: error=0x40 { UncorrectableError }
[17197364.136000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[17197364.136000] ata1: status=0x51 { DriveReady SeekComplete Error }
[17197364.136000] ata1: error=0x40 { UncorrectableError }
[17197366.732000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[17197366.732000] ata1: status=0x51 { DriveReady SeekComplete Error }
[17197366.732000] ata1: error=0x40 { UncorrectableError }
[17197369.324000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[17197369.324000] ata1: status=0x51 { DriveReady SeekComplete Error }
[17197369.324000] ata1: error=0x40 { UncorrectableError }
[17197372.328000] ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
[17197372.328000] ata1: status=0x51 { DriveReady SeekComplete Error }
[17197372.328000] ata1: error=0x40 { UncorrectableError }
[17197372.328000] sd 0:0:0:0: SCSI error: return code = 0x8000002
[17197372.328000] sda: Current: sense key: Medium Error
[17197372.328000]     Additional sense: Unrecovered read error - auto reallocate failed
[17197372.328000] Info fld=0xa9784bc
[17197372.328000] end_request: I/O error, dev sda, sector 177702076
[17197372.328000] Buffer I/O error on device sda2, logical block 452717


Is there a known problem that would cause this?
Is this a hardware or software issue?
If it is a hardware issue, how can I determine if it my SATA controller or my drive?

---

