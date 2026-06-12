---
title: "Cannot mount CDRW's"
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by JMO707 on 2006-09-04
I have found that whenever I try to mount a cdrw, it just didnt work.
Nor automount nor manual via *sudo mount -t iso9660 /dev/hdb /media/cdrom*
There is a /media/cdrom folder with right permissions and I belong to the cdrom group.

Here is the dmesg tail:

[I][17180437.696000] cdrom: hdb: mrw address space DMA selected
[17180439.008000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17180439.020000] ISOFS: changing to secondary root
[17180578.924000] cdrom: hdb: mrw address space DMA selected
[17180578.924000] cdrom open: mrw_status 'not mrw'
[17180586.956000] hdb: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[17180586.956000] hdb: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[17180586.956000] ide: failed opcode was: unknown
[17180586.956000] end_request: I/O error, dev hdb, sector 64
[17180586.960000] isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16[/I]

By the way, I recive an strange *mount: is not a directory* with the cdrw's.

Thank you for your time.

P.D: fstab line: 

*/dev/hdb        /media/cdrom    udf,iso9660 user,noauto                 0       0*

---

