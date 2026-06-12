---
title: "Ubuntu sometimes boots to busybox, with later hard drive errors"
date: 2015-10-09
forum: Hardware
---

### Post by bm90 on 2015-10-09
I have a issue with my home media server (OS ubuntu 14.04 LTS), where about 50% of the time I power it up, instead of booting into the os, I see the following:

```
BusyBox v1.21.1 (ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) [ 66.386735 ata1: STST failed (errno=-16)
[71.40 ...] ata1: SRST failed(errno=-16)
[71.41 ...] ata1: reset failed, giving up

```

I'm not sure if this is a RAM issue (initramfs), or with the hard drive (ata1). I am inclinded towards the later, as I have a second issue that I think is connected to this one.

In the second problem, one of the hard drives becomes read-only during runtime (I cannot predict when it will do it, sometimes I goes for a few days without happening, someones it happens a few times a day). I am currently waiting until happens again so I can look at the dmesg output.

Edit: I caught this in dmseg. At this time I attempted to access the hdd over the network (samda), and got a error as it had slipped into read-only mode
```
[ 7344.659295] ata5: soft resetting link
[ 7349.686555] ata5: SRST failed (errno=-16)
[ 7349.697955] ata5: reset failed, giving up
[ 7349.697961] ata5.01: disabled
[ 7349.697972] ata5.01: device reported invalid CHS sector 0
[ 7349.697997] ata5: EH complete
[ 7349.698055] sd 4:0:1:0: [sdd] FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 7349.698061] sd 4:0:1:0: [sdd] CDB: 
[ 7349.698065] Write(16): 8a 00 00 00 00 00 ae 84 08 20 00 00 00 10 00 00
[ 7349.698103] blk_update_request: I/O error, dev sdd, sector 2927888416
[ 7349.698139] sd 4:0:1:0: [sdd] FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 7349.698146] sd 4:0:1:0: [sdd] CDB: 
[ 7349.698149] Read(16): 88 00 00 00 00 01 44 41 0b b0 00 00 00 08 00 00
[ 7349.698172] blk_update_request: I/O error, dev sdd, sector 5440080816
[ 7349.698459] Aborting journal on device sdd1-8.
[ 7349.698470] EXT4-fs error (device sdd1): ext4_find_entry:1289: inode #170000532: comm mhddfs: reading directory lblock 0
[ 7349.698484] sd 4:0:1:0: [sdd] FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 7349.698485] sd 4:0:1:0: [sdd] FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 7349.698486] sd 4:0:1:0: [sdd] CDB: 
[ 7349.698487] Write(16): 8a
[ 7349.698490] sd 4:0:1:0: [sdd] CDB: 
[ 7349.698491] Write(16): 8a 00 00 00 00 00 ae 84 08 00 00 00 00 08 00 00
[ 7349.698502] blk_update_request: I/O error, dev sdd, sector 2927888384
[ 7349.698503]  00 00 00
[ 7349.698505] Buffer I/O error on dev sdd1, logical block 365985792, lost sync page write
[ 7349.698507]  00 00 00 00 08
[ 7349.698513] JBD2: Error -5 detected when updating journal superblock for sdd1-8.
[ 7349.698518]  00 00 00 00 08 00 00
[ 7349.698560] blk_update_request: I/O error, dev sdd, sector 2048
[ 7349.698562] Buffer I/O error on dev sdd1, logical block 0, lost sync page write
[ 7349.885463] EXT4-fs (sdd1): previous I/O error to superblock detected
[ 7349.885509] sd 4:0:1:0: [sdd] FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 7349.885513] sd 4:0:1:0: [sdd] CDB: 
[ 7349.885515] Write(16): 8a 00 00 00 00 00 00 00 08 00 00 00 00 08 00 00
[ 7349.885531] blk_update_request: I/O error, dev sdd, sector 2048
[ 7349.885536] Buffer I/O error on dev sdd1, logical block 0, lost sync page write
[ 7349.885551] EXT4-fs error (device sdd1): ext4_journal_check_start:56: Detected aborted journal
[ 7349.885556] EXT4-fs (sdd1): Remounting filesystem read-only
[ 7349.885560] EXT4-fs (sdd1): previous I/O error to superblock detected
[ 7349.885579] sd 4:0:1:0: [sdd] FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 7349.885582] sd 4:0:1:0: [sdd] CDB: 
[ 7349.885584] Write(16): 8a 00 00 00 00 00 00 00 08 00 00 00 00 08 00 00
[ 7349.885599] blk_update_request: I/O error, dev sdd, sector 2048
[ 7349.885602] Buffer I/O error on dev sdd1, logical block 0, lost sync page write
[ 7635.410532] sd 4:0:1:0: [sdd] FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 7635.410540] sd 4:0:1:0: [sdd] CDB: 
[ 7635.410544] Read(16): 88 00 00 00 00 00 ca 05 e2 18 00 00 00 08 00 00
[ 7635.410565] blk_update_request: I/O error, dev sdd, sector 3389383192
```

The last "FAILED" statements just repeat after that on sector 3389383192


Does this sounds like a problem with my RAM, or with the hard drive? The hdd is a WD 3TB Red, less than two months old.

Let me know if anyone needs any further outputs.

---

