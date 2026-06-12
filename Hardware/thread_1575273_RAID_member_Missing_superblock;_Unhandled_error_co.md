---
title: "RAID member Missing superblock; Unhandled error code - drive going bad?"
date: 2010-09-15
forum: Hardware
---

### Post by nstenz on 2010-09-15
1 TB RAID 1 array. Lucid x64, installed on different disk.
The system failed one of the disks in the array while or after I copied ~100 GB onto another disk for backup. I haven't been able to find out what the error messages in the system log mean exactly. It looks like I shut down the array while it was trying to rebuild (*because there's no notification of RAID disk failures in lucid!*), and when I tried to bring the array back online after a reboot, it failed, saying that one of the disks had a bad superblock.

The drive is a [Western Digital Caviar Blue 1 TB (WD10EALS)]("http://www.wdc.com/en/products/products.asp?driveid=793"). SMART reports no errors, including both the short and extended self-tests.

The question is, do I add this drive back into the array, or is it broken- and if it's broken, why are there no SMART errors? Or is md failing the disk for not responding in a timely manner? I tried not to get one of the disks WD cripples so RAID doesn't work properly...


> Sep 12 07:52:07 blackpowder kernel: [751578.282563] sd 0:0:0:0: [sdb] Unhandled error code
Sep 12 07:52:07 blackpowder kernel: [751578.282571] sd 0:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 12 07:52:07 blackpowder kernel: [751578.282580] sd 0:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 30 57 00 00 08 00
Sep 12 07:52:07 blackpowder kernel: [751578.282682] sd 0:0:0:0: [sdb] Unhandled error code
Sep 12 07:52:07 blackpowder kernel: [751578.282689] sd 0:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 12 07:52:07 blackpowder kernel: [751578.282699] sd 0:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 30 57 00 00 08 00
Sep 12 07:52:07 blackpowder kernel: [751578.289353] sd 0:0:0:0: [sdb] Unhandled error code
Sep 12 07:52:07 blackpowder kernel: [751578.289361] sd 0:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 12 07:52:07 blackpowder kernel: [751578.289369] sd 0:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 30 57 00 00 08 00
Sep 12 07:52:07 blackpowder kernel: [751578.361085] RAID1 conf printout:
Sep 12 07:52:07 blackpowder kernel: [751578.361092]  --- wd:1 rd:2
Sep 12 07:52:07 blackpowder kernel: [751578.361099]  disk 0, wo:1, o:0, dev:sdb1
Sep 12 07:52:07 blackpowder kernel: [751578.361105]  disk 1, wo:0, o:1, dev:sdc1
Sep 12 07:52:07 blackpowder kernel: [751578.400157] RAID1 conf printout:
Sep 12 07:52:07 blackpowder kernel: [751578.400163]  --- wd:1 rd:2
Sep 12 07:52:07 blackpowder kernel: [751578.400169]  disk 1, wo:0, o:1, dev:sdc1

Sep 15 00:14:41 blackpowder kernel: [983332.429389] sd 0:0:0:0: [sdb] Unhandled error code
Sep 15 00:14:41 blackpowder kernel: [983332.429397] sd 0:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 15 00:14:41 blackpowder kernel: [983332.429406] sd 0:0:0:0: [sdb] CDB: Read(10): 28 00 74 6c ea 9f 00 00 04 00
Sep 15 00:14:41 blackpowder kernel: [983332.429452] sd 0:0:0:0: [sdb] Unhandled error code
Sep 15 00:14:41 blackpowder kernel: [983332.429456] sd 0:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 15 00:14:41 blackpowder kernel: [983332.429463] sd 0:0:0:0: [sdb] CDB: Read(10): 28 00 74 6c ea a3 00 00 04 00
Sep 15 00:14:41 blackpowder kernel: [983332.429517] sd 0:0:0:0: [sdb] Unhandled error code
Sep 15 00:14:41 blackpowder kernel: [983332.429521] sd 0:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 15 00:14:41 blackpowder kernel: [983332.429528] sd 0:0:0:0: [sdb] CDB: Read(10): 28 00 74 6c ea 9f 00 00 08 00
Sep 15 00:14:41 blackpowder kernel: [983332.429615] sd 0:0:0:0: [sdb] Unhandled error code
Sep 15 00:14:41 blackpowder kernel: [983332.429620] sd 0:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 15 00:14:41 blackpowder kernel: [983332.429626] sd 0:0:0:0: [sdb] CDB: Read(10): 28 00 74 6c eb 1f 00 00 08 00
Sep 15 00:14:41 blackpowder kernel: [983332.429682] sd 0:0:0:0: [sdb] Unhandled error code
Sep 15 00:14:41 blackpowder kernel: [983332.429687] sd 0:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 15 00:14:41 blackpowder kernel: [983332.429693] sd 0:0:0:0: [sdb] CDB: Read(10): 28 00 74 6c eb 1f 00 00 08 00
Sep 15 00:16:09 blackpowder kernel: [983420.577201] md: requested-resync of RAID array md0
Sep 15 00:16:09 blackpowder kernel: [983420.577208] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Sep 15 00:16:09 blackpowder kernel: [983420.577214] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for requested-resync.
Sep 15 00:16:09 blackpowder kernel: [983420.577225] md: using 128k window, over a total of 968261504 blocks.
Sep 15 00:16:09 blackpowder kernel: [983420.577779] md: md0: requested-resync done.
Sep 15 00:17:14 blackpowder kernel: [983485.407464] md: requested-resync of RAID array md0
Sep 15 00:17:14 blackpowder kernel: [983485.407472] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Sep 15 00:17:14 blackpowder kernel: [983485.407478] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for requested-resync.
Sep 15 00:17:14 blackpowder kernel: [983485.407490] md: using 128k window, over a total of 968261504 blocks.
Sep 15 00:17:14 blackpowder kernel: [983485.408145] md: md0: requested-resync done.
Sep 15 00:17:16 blackpowder kernel: [983487.623033] md: requested-resync of RAID array md0
Sep 15 00:17:16 blackpowder kernel: [983487.623040] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Sep 15 00:17:16 blackpowder kernel: [983487.623046] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for requested-resync.
Sep 15 00:17:16 blackpowder kernel: [983487.623058] md: using 128k window, over a total of 968261504 blocks.
Sep 15 00:17:16 blackpowder kernel: [983487.623626] md: md0: requested-resync done.
Sep 15 00:17:21 blackpowder kernel: [983493.043015] md: md0 stopped.
Sep 15 00:17:21 blackpowder kernel: [983493.043130] md: unbind<sdb1>
Sep 15 00:17:22 blackpowder kernel: [983493.080095] md: export_rdev(sdb1)
Sep 15 00:17:22 blackpowder kernel: [983493.080161] md: unbind<sdc1>
Sep 15 00:17:22 blackpowder kernel: [983493.200137] md: export_rdev(sdc1)
Sep 15 00:17:33 blackpowder kernel: [983504.584210] md: md0 stopped.
Sep 15 00:17:33 blackpowder kernel: [983504.669062] sd 0:0:0:0: [sdb] Unhandled error code
Sep 15 00:17:33 blackpowder kernel: [983504.669070] sd 0:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 15 00:17:33 blackpowder kernel: [983504.669079] sd 0:0:0:0: [sdb] CDB: Read(10): 28 00 73 6c ff 3f 00 00 08 00
Sep 15 00:17:33 blackpowder kernel: [983504.669145] sd 0:0:0:0: [sdb] Unhandled error code
Sep 15 00:17:33 blackpowder kernel: [983504.669150] sd 0:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 15 00:17:33 blackpowder kernel: [983504.669156] sd 0:0:0:0: [sdb] CDB: Read(10): 28 00 73 6c ff 3f 00 00 08 00
Sep 15 00:17:57 blackpowder kernel: [983528.624341] md: md0 stopped.
Sep 15 00:17:57 blackpowder kernel: [983528.626840] sd 0:0:0:0: [sdb] Unhandled error code
Sep 15 00:17:57 blackpowder kernel: [983528.626848] sd 0:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 15 00:17:57 blackpowder kernel: [983528.626856] sd 0:0:0:0: [sdb] CDB: Read(10): 28 00 73 6c ff 3f 00 00 08 00
Sep 15 00:17:57 blackpowder kernel: [983528.626935] sd 0:0:0:0: [sdb] Unhandled error code
Sep 15 00:17:57 blackpowder kernel: [983528.626939] sd 0:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 15 00:17:57 blackpowder kernel: [983528.626946] sd 0:0:0:0: [sdb] CDB: Read(10): 28 00 73 6c ff 3f 00 00 08 00

Sep 15 08:15:01 blackpowder kernel: [  141.716356] md: md0 stopped.
Sep 15 08:15:01 blackpowder kernel: [  141.720776] md: bind<sdb1>
Sep 15 08:15:01 blackpowder kernel: [  141.720925] md: bind<sdc1>
Sep 15 08:15:01 blackpowder kernel: [  141.720940] md: kicking non-fresh sdb1 from array!
Sep 15 08:15:01 blackpowder kernel: [  141.720946] md: unbind<sdb1>
Sep 15 08:15:01 blackpowder kernel: [  141.741783] md: export_rdev(sdb1)
Sep 15 08:15:01 blackpowder kernel: [  141.764027] raid1: raid set md0 active with 1 out of 2 mirrors
Sep 15 08:15:01 blackpowder kernel: [  141.775749] md0: bitmap initialized from disk: read 15/15 pages, set 4621 bits
Sep 15 08:15:01 blackpowder kernel: [  141.775757] created bitmap (231 pages) for device md0
Sep 15 08:15:01 blackpowder kernel: [  141.805858] md0: detected capacity change from 0 to 991499780096
Sep 15 08:15:01 blackpowder kernel: [  141.806664]  md0: unknown partition table

---

### Post by nstenz on 2010-09-17
The Western Digital Lifeguard diagnostics show no problems with the disk. Can anybody tell me what these errors are?

---

