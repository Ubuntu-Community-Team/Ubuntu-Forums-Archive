---
title: "RunCore 64Gb SSD mini PCI-X block device not being allocated"
date: 2010-06-09
forum: Hardware
---

### Post by echo6 on 2010-06-09
```
[    0.368542] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.564471] ata2.00: ATA-0: ASUS-PHISON OB SSD, TST2.04L, max UDMA/66
[    0.564478] ata2.00: 7880544 sectors, multi 0: LBA 
[    0.564562] ata2.01: ATA-7: RunCore  64G-C  SSD, J090331, max UDMA/100
[    0.564568] ata2.01: 126189568 sectors, multi 1: LBA 
[    0.572541] ata2.00: configured for UDMA/66
[    0.584816] ata2.01: configured for UDMA/100
[    0.600308] ata2.00: configured for UDMA/66
[    0.608323] ata2.01: configured for UDMA/100
[    0.608339] ata2: EH complete
[    1.199755] sd 1:0:1:0: [sdb] 126189568 512-byte logical blocks: (64.6 GB/60.1 GiB)
[    1.199976] sd 1:0:1:0: [sdb] Write Protect is off
[    1.199982] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.200091] sd 1:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.200392]  sdb:
[   31.816062] ata2: lost interrupt (Status 0x58)
[   31.820018] ata2: drained 32768 bytes to clear DRQ.
[   31.889073] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   31.889079] ata2.01: BMDMA stat 0x64
[   31.889087] ata2.01: failed command: READ DMA
[   31.889101] ata2.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 0 dma 4096 in
[   31.889112] ata2.01: status: { DRDY DRQ }
[   31.889147] ata2: soft resetting link
[   37.084063] ata2: link is slow to respond, please be patient (ready=0)
[   38.372242] ata2.01: NODEV after polling detection
[   38.372248] ata2.01: revalidation failed (errno=-2)
[   43.372098] ata2: soft resetting link
[   48.568064] ata2: link is slow to respond, please be patient (ready=0)
[   49.901895] ata2.01: failed to IDENTIFY (I/O error, err_mask=0x3)
[   49.901902] ata2.01: revalidation failed (errno=-5)
[   54.864093] ata2: soft resetting link
[   60.060065] ata2: link is slow to respond, please be patient (ready=0)
[   61.348233] ata2.01: NODEV after polling detection
[   61.348239] ata2.01: revalidation failed (errno=-2)
[   61.348245] ata2.01: disabled
[   61.348253] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x40)
[   61.348259] ata2.00: revalidation failed (errno=-5)
[   66.348087] ata2: soft resetting link
[   71.544061] ata2: link is slow to respond, please be patient (ready=0)
[   72.856281] ata2.00: configured for UDMA/66
[   72.872278] ata2.00: configured for UDMA/66
[   72.872290] ata2: EH complete
[   72.872339] sd 1:0:1:0: [sdb] Unhandled error code
[   72.872345] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.872353] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   72.872373] end_request: I/O error, dev sdb, sector 0
[   72.872381] Buffer I/O error on device sdb, logical block 0
[   72.872487] sd 1:0:1:0: [sdb] Unhandled error code
[   72.872494] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.872501] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   72.872519] end_request: I/O error, dev sdb, sector 0
[   72.872524] Buffer I/O error on device sdb, logical block 0
[   72.872592] sd 1:0:1:0: [sdb] Unhandled error code
[   72.872597] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.872605] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   72.872622] end_request: I/O error, dev sdb, sector 0
[   72.872628] Buffer I/O error on device sdb, logical block 0
[   72.872705] sd 1:0:1:0: [sdb] Unhandled error code
[   72.872710] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.872717] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   72.872734] end_request: I/O error, dev sdb, sector 0
[   72.872740] Buffer I/O error on device sdb, logical block 0
[   72.872802] sd 1:0:1:0: [sdb] Unhandled error code
[   72.872808] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.872815] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   72.872832] end_request: I/O error, dev sdb, sector 0
[   72.872837] Buffer I/O error on device sdb, logical block 0
[   72.872912] sd 1:0:1:0: [sdb] Unhandled error code
[   72.872917] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.872924] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   72.872942] end_request: I/O error, dev sdb, sector 0
[   72.872947] Buffer I/O error on device sdb, logical block 0
[   72.873012] sd 1:0:1:0: [sdb] Unhandled error code
[   72.873017] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.873024] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   72.873044] end_request: I/O error, dev sdb, sector 0
[   72.873049] Buffer I/O error on device sdb, logical block 0
[   72.873113] sd 1:0:1:0: [sdb] Unhandled error code
[   72.873118] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.873125] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   72.873142] end_request: I/O error, dev sdb, sector 0
[   72.873148] Buffer I/O error on device sdb, logical block 0
[   72.873233] sd 1:0:1:0: [sdb] Unhandled error code
[   72.873238] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.873246] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   72.873263] end_request: I/O error, dev sdb, sector 0
[   72.873269] Buffer I/O error on device sdb, logical block 0
[   72.873284] Dev sdb: unable to read RDB block 0
[   72.873323] sd 1:0:1:0: [sdb] Unhandled error code
[   72.873328] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.873335] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   72.873352] end_request: I/O error, dev sdb, sector 0
[   72.873358] Buffer I/O error on device sdb, logical block 0
[   72.873423] sd 1:0:1:0: [sdb] Unhandled error code
[   72.873428] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.873435] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   72.873453] end_request: I/O error, dev sdb, sector 0
[   72.873529] sd 1:0:1:0: [sdb] Unhandled error code
[   72.873534] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.873541] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   72.873559] end_request: I/O error, dev sdb, sector 24
[   72.873628] sd 1:0:1:0: [sdb] Unhandled error code
[   72.873633] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.873640] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[   72.873658] end_request: I/O error, dev sdb, sector 24
[   72.873723] sd 1:0:1:0: [sdb] Unhandled error code
[   72.873728] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.873736] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   72.873753] end_request: I/O error, dev sdb, sector 0
[   72.873816] sd 1:0:1:0: [sdb] Unhandled error code
[   72.873821] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.873828] sd 1:0:1:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[   72.873845] end_request: I/O error, dev sdb, sector 0
[   72.874177] sd 1:0:1:0: [sdb] READ CAPACITY(16) failed
[   72.874182] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.874190] sd 1:0:1:0: [sdb] Sense not available.
[   72.874254] sd 1:0:1:0: [sdb] READ CAPACITY failed
[   72.874258] sd 1:0:1:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   72.874266] sd 1:0:1:0: [sdb] Sense not available.
[   72.874372] sd 1:0:1:0: [sdb] Attached SCSI disk
```

```
fdisk -l

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003e0b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          34      273073+  83  Linux
/dev/sda2              35         490     3662820   82  Linux swap / Solaris

Disk /dev/sdc: 16.0 GB, 16039018496 bytes
255 heads, 63 sectors/track, 1949 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b5e57

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1863    14957568   83  Linux
/dev/sdc2            1863        1950      702465    5  Extended
/dev/sdc5            1863        1950      702464   82  Linux swap / Solaris
```

---

