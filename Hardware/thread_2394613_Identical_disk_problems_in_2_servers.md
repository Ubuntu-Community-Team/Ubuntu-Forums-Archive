---
title: "Identical disk problems in 2 servers"
date: 2018-06-19
forum: Hardware
---

### Post by warwound on 2018-06-19
We have two HP ProLiant ML10 Gen9 servers running Ubuntu Server 14.04 and are experiencing very similar disk errors on each server.
A typical example from earlier this morning:

An rsync backup task is running overnight, i SSH into the server and am greeted with:

```

Last login: Tue Jun 19 06:35:41 2018 from mydomain
/usr/bin/xauth:  error in locking authority file /home/myusername/.Xauthority
-bash: /home/myusername/.profile: Input/output error
myusername@amsterdam:~$

```

I run the command 'dmesg -T' and see:

```

[Tue Jun 19 01:19:54 2018] perf interrupt took too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[Tue Jun 19 02:38:19 2018] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[Tue Jun 19 02:38:19 2018] ata3.00: failed command: FLUSH CACHE EXT
[Tue Jun 19 02:38:19 2018] ata3.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 18
[Tue Jun 19 02:38:19 2018]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[Tue Jun 19 02:38:19 2018] ata3.00: status: { DRDY }
[Tue Jun 19 02:38:19 2018] ata3: hard resetting link
[Tue Jun 19 02:38:24 2018] ata3: link is slow to respond, please be patient (ready=0)
[Tue Jun 19 02:38:29 2018] ata3: COMRESET failed (errno=-16)
[Tue Jun 19 02:38:29 2018] ata3: hard resetting link
[Tue Jun 19 02:38:34 2018] ata3: link is slow to respond, please be patient (ready=0)
[Tue Jun 19 02:38:39 2018] ata3: COMRESET failed (errno=-16)
[Tue Jun 19 02:38:39 2018] ata3: hard resetting link
[Tue Jun 19 02:38:44 2018] ata3: link is slow to respond, please be patient (ready=0)
[Tue Jun 19 02:39:14 2018] ata3: COMRESET failed (errno=-16)
[Tue Jun 19 02:39:14 2018] ata3: limiting SATA link speed to 3.0 Gbps
[Tue Jun 19 02:39:14 2018] ata3: hard resetting link
[Tue Jun 19 02:39:19 2018] ata3: COMRESET failed (errno=-16)
[Tue Jun 19 02:39:19 2018] ata3: reset failed, giving up
[Tue Jun 19 02:39:19 2018] ata3.00: disabled
[Tue Jun 19 02:39:19 2018] ata3: EH complete
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#19 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#19 CDB: Synchronize Cache(10) 35 00 00 00 00 00 00 00 00 00
[Tue Jun 19 02:39:19 2018] blk_update_request: I/O error, dev sdb, sector 5859720768
[Tue Jun 19 02:39:19 2018] Aborting journal on device sdb1-8.
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#20 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#20 CDB: Write(16) 8a 00 00 00 00 00 81 c0 08 20 00 00 00 08 00 00
[Tue Jun 19 02:39:19 2018] blk_update_request: I/O error, dev sdb, sector 2176845856
[Tue Jun 19 02:39:19 2018] Buffer I/O error on dev sdb1, logical block 272105476, lost async page write
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#21 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#21 CDB: Write(16) 8a 00 00 00 00 00 81 d6 b6 00 00 00 08 00 00 00
[Tue Jun 19 02:39:19 2018] blk_update_request: I/O error, dev sdb, sector 2178332160
[Tue Jun 19 02:39:19 2018] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 55122515 (offset 828112896 size 2359296 starting block 272291776)
[Tue Jun 19 02:39:19 2018] Buffer I/O error on device sdb1, logical block 272291264
[Tue Jun 19 02:39:19 2018] Buffer I/O error on device sdb1, logical block 272291265
[Tue Jun 19 02:39:19 2018] Buffer I/O error on device sdb1, logical block 272291266
[Tue Jun 19 02:39:19 2018] Buffer I/O error on device sdb1, logical block 272291267
[Tue Jun 19 02:39:19 2018] Buffer I/O error on device sdb1, logical block 272291268
[Tue Jun 19 02:39:19 2018] Buffer I/O error on device sdb1, logical block 272291269
[Tue Jun 19 02:39:19 2018] Buffer I/O error on device sdb1, logical block 272291270
[Tue Jun 19 02:39:19 2018] Buffer I/O error on device sdb1, logical block 272291271
[Tue Jun 19 02:39:19 2018] Buffer I/O error on device sdb1, logical block 272291272
[Tue Jun 19 02:39:19 2018] Buffer I/O error on device sdb1, logical block 272291273
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#22 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#22 CDB: Write(16) 8a 00 00 00 00 00 81 d6 be 00 00 00 0a 00 00 00
[Tue Jun 19 02:39:19 2018] blk_update_request: I/O error, dev sdb, sector 2178334208
[Tue Jun 19 02:39:19 2018] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 55122515 (offset 828112896 size 2359296 starting block 272292032)
[Tue Jun 19 02:39:19 2018] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 55122515 (offset 828112896 size 2359296 starting block 272292096)
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#23 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#23 CDB: Write(16) 8a 00 00 00 00 00 81 d6 c8 00 00 00 08 00 00 00
[Tue Jun 19 02:39:19 2018] blk_update_request: I/O error, dev sdb, sector 2178336768
[Tue Jun 19 02:39:19 2018] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 55122515 (offset 830472192 size 8388608 starting block 272292352)
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#24 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#24 CDB: Write(16) 8a 00 00 00 00 00 81 d6 d0 00 00 00 08 00 00 00
[Tue Jun 19 02:39:19 2018] blk_update_request: I/O error, dev sdb, sector 2178338816
[Tue Jun 19 02:39:19 2018] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 55122515 (offset 830472192 size 8388608 starting block 272292608)
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#25 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#25 CDB: Write(16) 8a 00 00 00 00 00 81 d6 d8 00 00 00 08 00 00 00
[Tue Jun 19 02:39:19 2018] blk_update_request: I/O error, dev sdb, sector 2178340864
[Tue Jun 19 02:39:19 2018] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 55122515 (offset 830472192 size 8388608 starting block 272292864)
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#26 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#26 CDB: Write(16) 8a 00 00 00 00 00 81 d6 e0 00 00 00 08 00 00 00
[Tue Jun 19 02:39:19 2018] blk_update_request: I/O error, dev sdb, sector 2178342912
[Tue Jun 19 02:39:19 2018] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 55122515 (offset 830472192 size 8388608 starting block 272293120)
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#27 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#27 CDB: Write(16) 8a 00 00 00 00 00 81 d6 e8 00 00 00 08 00 00 00
[Tue Jun 19 02:39:19 2018] blk_update_request: I/O error, dev sdb, sector 2178344960
[Tue Jun 19 02:39:19 2018] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 55122515 (offset 830472192 size 8388608 starting block 272293376)
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#28 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 02:39:19 2018] sd 2:0:0:0: [sdb] tag#28 CDB: Write(16) 8a 00 00 00 00 00 81 d6 f0 00 00 00 08 00 00 00
[Tue Jun 19 02:39:19 2018] blk_update_request: I/O error, dev sdb, sector 2178347008
[Tue Jun 19 02:39:19 2018] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 55122515 (offset 830472192 size 8388608 starting block 272293632)
[Tue Jun 19 02:39:19 2018] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 55122515 (offset 830472192 size 8388608 starting block 272293888)
[Tue Jun 19 02:39:19 2018] EXT4-fs error (device sdb1) in ext4_do_update_inode:4703: Journal has aborted
[Tue Jun 19 02:39:19 2018] Buffer I/O error on dev sdb1, logical block 732463104, lost sync page write
[Tue Jun 19 02:39:19 2018] JBD2: Error -5 detected when updating journal superblock for sdb1-8.
[Tue Jun 19 02:39:19 2018] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
[Tue Jun 19 02:39:19 2018] EXT4-fs error (device sdb1): mpage_map_and_submit_extent:2345: comm kworker/u4:0: Failed to mark inode 55122515 dirty
[Tue Jun 19 02:39:19 2018] EXT4-fs (sdb1): previous I/O error to superblock detected
[Tue Jun 19 02:39:19 2018] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
[Tue Jun 19 02:39:19 2018] EXT4-fs error (device sdb1) in ext4_writepages:2647: IO failure
[Tue Jun 19 02:39:19 2018] EXT4-fs (sdb1): previous I/O error to superblock detected
[Tue Jun 19 02:39:19 2018] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
[Tue Jun 19 02:39:19 2018] EXT4-fs (sdb1): previous I/O error to superblock detected
[Tue Jun 19 02:39:19 2018] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
[Tue Jun 19 02:39:19 2018] EXT4-fs error (device sdb1): ext4_journal_check_start:56: Detected aborted journal
[Tue Jun 19 02:39:19 2018] EXT4-fs (sdb1): Remounting filesystem read-only
[Tue Jun 19 02:39:19 2018] EXT4-fs (sdb1): previous I/O error to superblock detected
[Tue Jun 19 02:39:19 2018] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
[Tue Jun 19 02:39:19 2018] EXT4-fs (sdb1): ext4_writepages: jbd2_start: 3072 pages, ino 55122516; err -30
[Tue Jun 19 02:39:19 2018] JBD2: Detected IO errors while flushing file data on sdb1-8
[Tue Jun 19 04:11:04 2018] scsi_io_completion: 147 callbacks suppressed
[Tue Jun 19 04:11:04 2018] sd 2:0:0:0: [sdb] tag#7 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 04:11:04 2018] sd 2:0:0:0: [sdb] tag#7 CDB: Read(16) 88 00 00 00 00 00 c3 04 20 e0 00 00 00 08 00 00
[Tue Jun 19 04:11:04 2018] blk_update_request: 153 callbacks suppressed
[Tue Jun 19 04:11:04 2018] blk_update_request: I/O error, dev sdb, sector 3271827680
[Tue Jun 19 04:11:04 2018] sd 2:0:0:0: [sdb] tag#8 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 04:11:04 2018] sd 2:0:0:0: [sdb] tag#8 CDB: Read(16) 88 00 00 00 00 00 c3 04 20 e0 00 00 00 08 00 00
[Tue Jun 19 04:11:04 2018] blk_update_request: I/O error, dev sdb, sector 3271827680
[Tue Jun 19 04:11:05 2018] sd 2:0:0:0: [sdb] tag#9 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 04:11:05 2018] sd 2:0:0:0: [sdb] tag#9 CDB: Read(16) 88 00 00 00 00 00 c3 05 02 58 00 00 00 08 00 00
[Tue Jun 19 04:11:05 2018] blk_update_request: I/O error, dev sdb, sector 3271885400
[Tue Jun 19 04:11:05 2018] sd 2:0:0:0: [sdb] tag#10 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 04:11:05 2018] sd 2:0:0:0: [sdb] tag#10 CDB: Read(16) 88 00 00 00 00 00 c3 05 02 58 00 00 00 08 00 00
[Tue Jun 19 04:11:05 2018] blk_update_request: I/O error, dev sdb, sector 3271885400
[Tue Jun 19 04:11:05 2018] sd 2:0:0:0: [sdb] tag#11 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 04:11:05 2018] sd 2:0:0:0: [sdb] tag#11 CDB: Read(16) 88 00 00 00 00 00 c9 1a 94 e0 00 00 00 40 00 00
[Tue Jun 19 04:11:05 2018] blk_update_request: I/O error, dev sdb, sector 3373962464
[Tue Jun 19 04:11:05 2018] sd 2:0:0:0: [sdb] tag#12 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 04:11:05 2018] sd 2:0:0:0: [sdb] tag#12 CDB: Read(16) 88 00 00 00 00 00 c9 1a 94 e0 00 00 00 08 00 00
[Tue Jun 19 04:11:05 2018] blk_update_request: I/O error, dev sdb, sector 3373962464
[Tue Jun 19 04:11:05 2018] sd 2:0:0:0: [sdb] tag#13 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 04:11:05 2018] sd 2:0:0:0: [sdb] tag#13 CDB: Read(16) 88 00 00 00 00 00 c9 1a 94 e0 00 00 00 08 00 00
[Tue Jun 19 04:11:05 2018] blk_update_request: I/O error, dev sdb, sector 3373962464
[Tue Jun 19 04:11:29 2018] sd 2:0:0:0: [sdb] tag#14 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 04:11:29 2018] sd 2:0:0:0: [sdb] tag#14 CDB: Read(16) 88 00 00 00 00 00 c9 1a 94 e0 00 00 00 08 00 00
[Tue Jun 19 04:11:29 2018] blk_update_request: I/O error, dev sdb, sector 3373962464
[Tue Jun 19 04:11:33 2018] sd 2:0:0:0: [sdb] tag#15 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 04:11:33 2018] sd 2:0:0:0: [sdb] tag#15 CDB: Read(16) 88 00 00 00 00 00 c3 04 20 b8 00 00 00 08 00 00
[Tue Jun 19 04:11:33 2018] blk_update_request: I/O error, dev sdb, sector 3271827640
[Tue Jun 19 04:11:33 2018] sd 2:0:0:0: [sdb] tag#16 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 04:11:33 2018] sd 2:0:0:0: [sdb] tag#16 CDB: Read(16) 88 00 00 00 00 00 c3 04 20 b8 00 00 00 08 00 00
[Tue Jun 19 04:11:33 2018] blk_update_request: I/O error, dev sdb, sector 3271827640
[Tue Jun 19 04:11:33 2018] sd 2:0:0:0: [sdb] tag#17 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 04:11:33 2018] sd 2:0:0:0: [sdb] tag#17 CDB: Read(16) 88 00 00 00 00 00 c9 1a 94 e0 00 00 00 08 00 00
[Tue Jun 19 04:11:33 2018] blk_update_request: I/O error, dev sdb, sector 3373962464
[Tue Jun 19 06:33:32 2018] sd 2:0:0:0: [sdb] tag#16 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:33:32 2018] sd 2:0:0:0: [sdb] tag#16 CDB: Read(16) 88 00 00 00 00 00 c3 04 20 e0 00 00 00 08 00 00
[Tue Jun 19 06:33:32 2018] blk_update_request: I/O error, dev sdb, sector 3271827680
[Tue Jun 19 06:33:32 2018] sd 2:0:0:0: [sdb] tag#17 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:33:32 2018] sd 2:0:0:0: [sdb] tag#17 CDB: Read(16) 88 00 00 00 00 00 c3 05 02 58 00 00 00 08 00 00
[Tue Jun 19 06:33:32 2018] blk_update_request: I/O error, dev sdb, sector 3271885400
[Tue Jun 19 06:33:32 2018] sd 2:0:0:0: [sdb] tag#18 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:33:32 2018] sd 2:0:0:0: [sdb] tag#18 CDB: Read(16) 88 00 00 00 00 00 c9 1a 94 e0 00 00 00 08 00 00
[Tue Jun 19 06:33:32 2018] blk_update_request: I/O error, dev sdb, sector 3373962464
[Tue Jun 19 06:33:32 2018] sd 2:0:0:0: [sdb] tag#19 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:33:32 2018] sd 2:0:0:0: [sdb] tag#19 CDB: Read(16) 88 00 00 00 00 00 c9 1a 94 e0 00 00 00 08 00 00
[Tue Jun 19 06:33:32 2018] blk_update_request: I/O error, dev sdb, sector 3373962464
[Tue Jun 19 06:33:46 2018] sd 2:0:0:0: [sdb] tag#20 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:33:46 2018] sd 2:0:0:0: [sdb] tag#20 CDB: Read(16) 88 00 00 00 00 00 c3 04 20 b8 00 00 00 08 00 00
[Tue Jun 19 06:33:46 2018] blk_update_request: I/O error, dev sdb, sector 3271827640
[Tue Jun 19 06:33:46 2018] sd 2:0:0:0: [sdb] tag#21 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:33:46 2018] sd 2:0:0:0: [sdb] tag#21 CDB: Read(16) 88 00 00 00 00 00 c9 1a 94 e0 00 00 00 08 00 00
[Tue Jun 19 06:33:46 2018] blk_update_request: I/O error, dev sdb, sector 3373962464
[Tue Jun 19 06:35:42 2018] sd 2:0:0:0: [sdb] tag#24 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:35:42 2018] sd 2:0:0:0: [sdb] tag#24 CDB: Read(16) 88 00 00 00 00 00 c3 04 20 e0 00 00 00 08 00 00
[Tue Jun 19 06:35:42 2018] blk_update_request: I/O error, dev sdb, sector 3271827680
[Tue Jun 19 06:35:43 2018] sd 2:0:0:0: [sdb] tag#25 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:35:43 2018] sd 2:0:0:0: [sdb] tag#25 CDB: Read(16) 88 00 00 00 00 00 c3 05 02 58 00 00 00 08 00 00
[Tue Jun 19 06:35:43 2018] blk_update_request: I/O error, dev sdb, sector 3271885400
[Tue Jun 19 06:35:43 2018] sd 2:0:0:0: [sdb] tag#26 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:35:43 2018] sd 2:0:0:0: [sdb] tag#26 CDB: Read(16) 88 00 00 00 00 00 c9 1a 94 e0 00 00 00 08 00 00
[Tue Jun 19 06:35:43 2018] blk_update_request: I/O error, dev sdb, sector 3373962464
[Tue Jun 19 06:35:43 2018] sd 2:0:0:0: [sdb] tag#27 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:35:43 2018] sd 2:0:0:0: [sdb] tag#27 CDB: Read(16) 88 00 00 00 00 00 c9 1a 94 e0 00 00 00 08 00 00
[Tue Jun 19 06:35:43 2018] blk_update_request: I/O error, dev sdb, sector 3373962464
[Tue Jun 19 06:35:45 2018] sd 2:0:0:0: [sdb] tag#28 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:35:45 2018] sd 2:0:0:0: [sdb] tag#28 CDB: Read(16) 88 00 00 00 00 00 c3 04 20 b8 00 00 00 08 00 00
[Tue Jun 19 06:35:45 2018] blk_update_request: I/O error, dev sdb, sector 3271827640
[Tue Jun 19 06:35:45 2018] sd 2:0:0:0: [sdb] tag#29 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:35:45 2018] sd 2:0:0:0: [sdb] tag#29 CDB: Read(16) 88 00 00 00 00 00 c9 1a 94 e0 00 00 00 08 00 00
[Tue Jun 19 06:35:45 2018] blk_update_request: I/O error, dev sdb, sector 3373962464
[Tue Jun 19 06:35:54 2018] sd 2:0:0:0: [sdb] tag#30 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:35:54 2018] sd 2:0:0:0: [sdb] tag#30 CDB: Read(16) 88 00 00 00 00 00 c3 04 20 e0 00 00 00 08 00 00
[Tue Jun 19 06:35:54 2018] blk_update_request: I/O error, dev sdb, sector 3271827680
[Tue Jun 19 06:35:54 2018] sd 2:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:35:54 2018] sd 2:0:0:0: [sdb] tag#0 CDB: Read(16) 88 00 00 00 00 00 c3 05 02 58 00 00 00 08 00 00
[Tue Jun 19 06:35:54 2018] blk_update_request: I/O error, dev sdb, sector 3271885400
[Tue Jun 19 06:35:54 2018] sd 2:0:0:0: [sdb] tag#1 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:35:54 2018] sd 2:0:0:0: [sdb] tag#1 CDB: Read(16) 88 00 00 00 00 00 c9 1a 94 e0 00 00 00 08 00 00
[Tue Jun 19 06:35:54 2018] blk_update_request: I/O error, dev sdb, sector 3373962464
[Tue Jun 19 06:35:54 2018] sd 2:0:0:0: [sdb] tag#2 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[Tue Jun 19 06:35:54 2018] sd 2:0:0:0: [sdb] tag#2 CDB: Read(16) 88 00 00 00 00 00 c9 1a 94 e0 00 00 00 08 00 00
[Tue Jun 19 06:35:54 2018] blk_update_request: I/O error, dev sdb, sector 3373962464

```

Both servers have the same setup:
sda is a 240GB Toshiba SSD and is the root mount point.
sdb is a 6TB Seagate mechanical HDD and is the /home mount point.
So sector errors have been found on the 6TB mechanical HDD.

I send a 'sudo reboot' command via SSH and the BIOS only detects the SSD, the HDD is not detected.
Ubuntu starts to boot and reports: 'ALERT! /dev/disk/by-uuid/<UUID HERE> does not exist.
The UUID is the UUID of the / root partition on the SSD.
By the time this alert line appears the server has partly booted - so it has managed to mount at least the boot partition which is on the SSD.
(It must also have read the 'fstab' file and tried to mount the / root partition but the fstab file is located on the partition that is not found!)
The boot process hangs and the server needs a power cycle after which it boots successfully.
The server then runs with no problem until at some (random) point the identical disk problems reoccur.

Heavy disk writing, such as when an rsync backup is taking place, seems to cause the error 90% of the time.

Both servers are just under 18 months old and the SSDs and HDDs are the same age.

Both servers show the same, very similar, behaviour:
The syslog shows a load of sector errors on the mechanical HDD and HDD is remounted read only.
The syslog never shows any errors relating to the SSD.
A software reboot fails when Ubuntu fails to find the / root partition on the SSD.
Only a power cycle fixes things.

Can anyone suggest what i can do to debug this problem?

Thanks.

---

### Post by gabe. on 2018-06-19
Hello.
Have you tried to check the smart data on the disks? Or run a full diagnostic on them? (If they are the same model and belong to same batch, could be a batch flaw.)
Smartmon Tools is your friend here.
Are you by any chance running hardware RAID? (Those HP controllers are really problematic, at least in my experience... so much that I always go for software RAID)
Maybe, by a distant shot, you've hit a bug in the driver version you are using.
In the end, if you don't have any bad sectors and the smart data is ok, I would definitely put more effort on checking those disk controllers. Specially if you are using hardware RAID.
I hope it gives at least a little step to move close to find the solution for your problem.
See you.

---

### Post by warwound on 2018-06-20
Thanks for the suggestions.

We are not running any type of RAID, the SSDs and HDDs are connected as standard SATA drives.
I have previously installed Smartmon Tools and the SMART data for all drives (both SSDs and HDDs) shows no problems whatsoever.

The HDD on one server has passed both a short and an extended test.
The HDD on the other server has, to date, only passed a short test so i'll schedule an extended test to run tonight.

The SSDs in both servers passed both short and extended tests a couple of weeks ago.
I then found that a firmware update existed for the SSDs and the firmware update documentation stated "This Firmware update aims to prevent the phenomenon in which a host does not recognize SSD.".
After reading this i thought 'bingo this must be our problem' and arranged for the SSDs' firmwares to be updated.
They were both updated but the problem persists.

I'm thinking that a single hardware disk error is unlikely, it wouldn't explain why Ubuntu fails to find the SSD when rebooting after the HDD has been remounted in read only mode.
How would i debug a problem with the disk controllers?
Ubuntu Server 14.04.05 LTS is installed on each server and no 3rd party drivers have been installed, so the disk controller is using whatever the default Ubuntu driver is.
Are there any utilities that can can perform disk controller tests?

---

### Post by gabe. on 2018-06-20
So you are not using the hpvsa drivers.
You could simulate some heavy loading using hdparm or dd and look for error messages in the logs.
And just for safety, I would check the cables, power supply and/or try other sata ports on these machines. The dvd drive port would be a good choice to easily avoid a possible connection problem with the hd cage.
Anyway, are you using an updated kernel and bios/controller firmware? Have you checked the integrity of your partition table and the partitions themselves?
A more direct, but not simplest way, would be trying to boot the disk on another totally different machine or the same machine with another temporary system/disk (other than the ones you are using) and see if the problem persists. See what happens if you eliminate the SSDs and boot from a regular hd alone. (not an easy task for a server)
In the end, I wouldn't be surprised if it is a driver stability problem and the HP disk controller.
Unfortunately, HP only offers support for RHEL/Centos.

---

### Post by warwound on 2018-06-21
You inspired me to research a possible disk hardware driver issue, which led me to the HP website where i found the latest BIOS for our servers is version 1.11, version 1.11 is marked as a **CRITICAL** update.
Our servers are running version 1.02 so my priority now is to get the servers' BIOSes updated.
After that we'll physically inspect the drives and cables etc looking for any dodgy or damaged connections.
Finally i plan to boot each server to 'single user mode' with the HDD (/home partition) not mounted.
I'll then see what i can establish - disk checks and stress testing the HD.

Thanks again for taking the time to help.

---

