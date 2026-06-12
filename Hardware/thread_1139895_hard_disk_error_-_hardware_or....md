---
title: "hard disk error - hardware or...?"
date: 2009-04-27
forum: Hardware
---

### Post by DaiLaughing on 2009-04-27
This is a development/educational server (8.04) but I don't think it is a server issue.  The hard drive is clearly to blame but I don't know if it is a hardware or linux problem.  

The server seemed sluggish today so I had a look and some of the filesystem had gone read only.  Why that could be was way beyond me so I tried a restart which may not have been ideal.  It hangs on GRUB (stage 1.5) for a while and then starts to give me loads of obscure messages from hardware detection (snippet below) before giving me some sort of emergency console from initramfs.

I took the drive out and attached it to a new 9.04 server system as secondary IDE master and it caused the same sort of thing on that.  That system boots eventually (after the errors) and seems OK (not set up yet so have not tested fully as server) but trying to mount the troubled drive fails.  Below is the message on mount failure and below that is the last section of the dmesg output (there is much more before that but it seems similar).  The mount error message comes after more of the obscure messages each time I run it:

mount: wrong fs type, bad option, bad superblock on /dev/sdb1, etc etc

[ 7725.510395] ata2.00: configured for UDMA/33
[ 7725.510410] ata2: EH complete
[ 7727.188248] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 7727.188303] ata2.00: BMDMA stat 0x24
[ 7727.188352] ata2.00: cmd c8/00:08:4f:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 7727.188354]          res 51/40:00:4f:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 7727.188470] ata2.00: status: { DRDY ERR }
[ 7727.188515] ata2.00: error: { UNC }
[ 7727.240393] ata2.00: configured for UDMA/33
[ 7727.240411] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 7727.240416] sd 1:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[ 7727.240421] Descriptor sense data with sense descriptors (in hex):
[ 7727.240424]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 7727.240433]         00 00 00 4f 
[ 7727.240437] sd 1:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[ 7727.240443] end_request: I/O error, dev sdb, sector 79
[ 7727.240509] ata2: EH complete
[ 7727.240530] EXT3-fs: can't read group descriptor 1
[ 7727.245307] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 7727.245350] sd 1:0:0:0: [sdb] 80293248 512-byte hardware sectors: (41.1 GB/38.2 GiB)
[ 7727.245369] sd 1:0:0:0: [sdb] Write Protect is off
[ 7727.245372] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 7727.245401] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by DaiLaughing on 2009-04-30
Just in case it helps others this still appears to be physical hard disk problems but not necessarily as a new server on a new system ended up the same way after a couple of days.  The third attempt doesn't use maxtor disks and doesn't use ext3 just in case either of those was the cause (I have three servers at home which use ext3 and are rock solid so that seems unlikely).

---

