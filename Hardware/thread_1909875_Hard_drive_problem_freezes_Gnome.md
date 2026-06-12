---
title: "Hard drive problem freezes Gnome"
date: 2012-01-16
forum: Hardware
---

### Post by sauen on 2012-01-16
My computer has started to freeze approximately every half hour. This has never happened before, and it has got uptime of months, only to be rebooted for kernel upgrades.

Nothing appears in the logs, but I was able to capture the output of dmesg while being logged in with ssh at the event of a freeze. I have cut out the interresting part, where the errors start. At first I believed the SSD disk (sda) was crashing, but SMART data shows no error. Also, I was able to dd-clone the disk using a live CD without errors. I can't figure out what is going on. Is the disk crashing, or what?

```
[  161.009799] [fglrx] Reserved FB block: Unshared offset:fbff000, size:401000 
[  161.009800] [fglrx] Reserved FB block: Unshared offset:26ffb000, size:5000 
[  180.371920] init: tty5 main process ended, respawning
[ 3573.824080] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
[ 3573.824093] ata1.00: failed command: WRITE FPDMA QUEUED
[ 3573.824108] ata1.00: cmd 61/28:00:50:e8:f8/00:00:03:00:00/40 tag 0 ncq 20480 out
[ 3573.824111]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 3573.824119] ata1.00: status: { DRDY }
[ 3573.824128] ata1: hard resetting link
[ 3583.836064] ata1: softreset failed (device not ready)
[ 3583.836075] ata1: hard resetting link
[ 3593.848052] ata1: softreset failed (device not ready)
[ 3593.848063] ata1: hard resetting link
[ 3604.420057] ata1: link is slow to respond, please be patient (ready=0)
[ 3628.892030] ata1: softreset failed (device not ready)
[ 3628.892042] ata1: limiting SATA link speed to 3.0 Gbps
[ 3628.892050] ata1: hard resetting link
[ 3634.080027] ata1: softreset failed (device not ready)
[ 3634.080034] ata1: reset failed, giving up
[ 3634.080039] ata1.00: disabled
[ 3634.080049] ata1.00: device reported invalid CHS sector 0
[ 3634.080066] ata1: EH complete
[ 3634.080109] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.080115] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.080123] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 03 f8 e8 50 00 00 28 00
[ 3634.080146] end_request: I/O error, dev sda, sector 66644048
[ 3634.080178] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.080183] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.080191] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 04 38 71 78 00 00 08 00
[ 3634.080212] end_request: I/O error, dev sda, sector 70807928
[ 3634.080224] Aborting journal on device sda2-8.
[ 3634.080246] EXT4-fs error (device sda2) in ext4_reserve_inode_write:5638: Journal has aborted
[ 3634.080261] EXT4-fs error (device sda2) in ext4_new_inode:1073: Journal has aborted
[ 3634.080274] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.080281] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.080292] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 05 34 63 18 00 00 08 00
[ 3634.080318] end_request: I/O error, dev sda, sector 87319320
[ 3634.080329] EXT4-fs error (device sda2) in ext4_reserve_inode_write:5638: Journal has aborted
[ 3634.080343] quiet_error: 36 callbacks suppressed
[ 3634.080351] Buffer I/O error on device sda2, logical block 8912995
[ 3634.080357] lost page write due to I/O error on sda2
[ 3634.080382] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.080387] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.080394] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 04 38 71 78 00 00 08 00
[ 3634.080411] end_request: I/O error, dev sda, sector 70807928
[ 3634.080439] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.080443] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.080451] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 07 34 70 a8 00 00 08 00
[ 3634.080466] end_request: I/O error, dev sda, sector 120877224
[ 3634.080473] Buffer I/O error on device sda2, logical block 13107733
[ 3634.080478] lost page write due to I/O error on sda2
[ 3634.080502] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.080507] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.080514] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 04 38 71 78 00 00 08 00
[ 3634.080529] end_request: I/O error, dev sda, sector 70807928
[ 3634.080562] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.080567] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.080574] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 04 34 61 18 00 00 08 00
[ 3634.080589] end_request: I/O error, dev sda, sector 70541592
[ 3634.080595] Buffer I/O error on device sda2, logical block 6815779
[ 3634.080600] lost page write due to I/O error on sda2
[ 3634.080624] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.080629] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.080636] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 04 38 71 78 00 00 08 00
[ 3634.080651] end_request: I/O error, dev sda, sector 70807928
[ 3634.080672] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.080682] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.080689] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 04 34 62 00 00 00 08 00
[ 3634.080705] end_request: I/O error, dev sda, sector 70541824
[ 3634.080711] Buffer I/O error on device sda2, logical block 6815808
[ 3634.080716] lost page write due to I/O error on sda2
[ 3634.080735] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.080744] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.080751] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 04 34 65 c0 00 00 08 00
[ 3634.080767] end_request: I/O error, dev sda, sector 70542784
[ 3634.080773] Buffer I/O error on device sda2, logical block 6815928
[ 3634.080777] lost page write due to I/O error on sda2
[ 3634.080793] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.080798] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.080810] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 04 34 6c f8 00 00 08 00
[ 3634.080825] end_request: I/O error, dev sda, sector 70544632
[ 3634.080831] Buffer I/O error on device sda2, logical block 6816159
[ 3634.080836] lost page write due to I/O error on sda2
[ 3634.080852] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.080856] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.080868] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 04 34 6e c0 00 00 10 00
[ 3634.080883] end_request: I/O error, dev sda, sector 70545088
[ 3634.080889] Buffer I/O error on device sda2, logical block 6816216
[ 3634.080894] lost page write due to I/O error on sda2
[ 3634.080901] Buffer I/O error on device sda2, logical block 6816217
[ 3634.080906] lost page write due to I/O error on sda2
[ 3634.080921] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.080930] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.080937] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 04 34 94 20 00 00 08 00
[ 3634.080952] end_request: I/O error, dev sda, sector 70554656
[ 3634.080958] Buffer I/O error on device sda2, logical block 6817412
[ 3634.080963] lost page write due to I/O error on sda2
[ 3634.080979] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.080983] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.080995] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 04 34 95 a8 00 00 08 00
[ 3634.081010] end_request: I/O error, dev sda, sector 70555048
[ 3634.081016] Buffer I/O error on device sda2, logical block 6817461
[ 3634.081021] lost page write due to I/O error on sda2
[ 3634.081036] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.081041] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.081053] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 04 50 62 18 00 00 08 00
[ 3634.081068] end_request: I/O error, dev sda, sector 72376856
[ 3634.081084] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.081089] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.081096] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 04 74 8e 30 00 00 08 00
[ 3634.081116] end_request: I/O error, dev sda, sector 74747440
[ 3634.081131] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.081136] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.081143] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 04 74 91 38 00 00 08 00
[ 3634.081158] end_request: I/O error, dev sda, sector 74748216
[ 3634.081179] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.081183] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.081190] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 04 78 d1 88 00 00 08 00
[ 3634.081205] end_request: I/O error, dev sda, sector 75026824
[ 3634.081213] Buffer I/O error on device sda2, logical block 7376433
[ 3634.081228] EXT4-fs warning (device sda2): ext4_end_bio:258: I/O error writing to inode 1858369 (offset 0 size 4096 starting block 9378354)
[ 3634.081249] EXT4-fs error (device sda2) in ext4_reserve_inode_write:5638: Journal has aborted
[ 3634.081253] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.081260] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.081269] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 04 f4 77 98 00 00 08 00
[ 3634.081294] end_request: I/O error, dev sda, sector 83130264
[ 3634.081313] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.081318] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.081330] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 00 f5 db e0 00 00 10 00
[ 3634.081345] end_request: I/O error, dev sda, sector 16112608
[ 3634.081352] Buffer I/O error on device sda2, logical block 12156
[ 3634.081359] Buffer I/O error on device sda2, logical block 12157
[ 3634.081371] EXT4-fs warning (device sda2): ext4_end_bio:258: I/O error writing to inode 1703954 (offset 118784 size 8192 starting block 2014078)
[ 3634.081394] EXT4-fs error (device sda2) in ext4_reserve_inode_write:5638: Journal has aborted
[ 3634.081406] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.081411] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.081418] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 00 f5 df b0 00 00 08 00
[ 3634.081434] end_request: I/O error, dev sda, sector 16113584
[ 3634.081440] Buffer I/O error on device sda2, logical block 12278
[ 3634.081449] EXT4-fs warning (device sda2): ext4_end_bio:258: I/O error writing to inode 1704922 (offset 94208 size 4096 starting block 2014199)
[ 3634.081466] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.081476] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.081483] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 04 38 71 78 00 00 08 00
[ 3634.081498] end_request: I/O error, dev sda, sector 70807928
[ 3634.081513] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.081517] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.081524] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 00 f4 60 00 00 00 08 00
[ 3634.081544] end_request: I/O error, dev sda, sector 16015360
[ 3634.081570] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.081574] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.081582] sd 0:0:0:0: [sda] CDB: 
[ 3634.081595] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.081603] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.081615] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 04 38 71 78 00 00 08 00
[ 3634.081641] end_request: I/O error, dev sda, sector 70807928
[ 3634.081655] sd 0:0:0:0: [sda] Unhandled error code
[ 3634.081659] Write(10): 2a 00 03 f8 60 00 00 00 08 00
[ 3634.081682] end_request: I/O error, dev sda, sector 66609152
[ 3634.081698] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3634.081708] JBD2: I/O error detected when updating journal superblock for sda2-8.

```

---

### Post by LinuxFan999 on 2012-01-16
Which version of Ubuntu are you using?

---

### Post by sauen on 2012-01-16
Latest version (11.10).

---

### Post by sauen on 2012-01-17
Update.

I booted into a live Knoppix CD and made a script that did small reads and writes to the same disk. After a few hours the script was unable to read or write to the SSD disk, and the same errors appeared in dmesg. I think this is a clear indication that this is a hardware problem, most likely a disk error. Especially because Ubuntu and Knoppix are running different kernels, 3.0.0-14 and 2.6.39.3.

---

### Post by LinuxFan999 on 2012-01-19
Your SSD is probably failing. I personally do not recommend using SSDs for this exact reason. I recommend replacing it with a mechanical hard drive with at least 1 TB of space or more.

---

### Post by sauen on 2012-01-30
Update.

It was the previously mentioned SSD disk. I sent it back to the supplier, and got it replaced under the warranty. It now works. Anybody experiencing similar problems should take note of this.

---

