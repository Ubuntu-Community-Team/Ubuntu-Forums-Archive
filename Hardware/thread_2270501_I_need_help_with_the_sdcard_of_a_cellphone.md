---
title: "I need help with the sdcard of a cellphone"
date: 2015-03-23
forum: Hardware
---

### Post by nargaroth_reg on 2015-03-23
Hello! I have a cellphone that is ages old (samsung model e2121l) and I want  to change the music I have in it but I can't use the sdcard (the  filesystem it uses is FAT) well on linux. In the settings of the cellphone  I have set it to 'usb mass storage mode'. I can see it in lsusb, browse the files and folders and copy small files with file managers, but I'm unable to copy larger files in or out (like .mp3 ones u.u). It is not compatible with mtp. It works ok on windows so the  device does not seem to be flawed.
lsusb output:
```
[  427.932117] usb 5-1: new full-speed USB device number 3 using ohci_hcd
[  428.116291] usb 5-1: New USB device found, idVendor=04e8, idProduct=681e
[  428.116302] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  428.116309] usb 5-1: Product: USB MMC Storag
[  428.116314] usb 5-1: Manufacturer: SAMSUNG Electronics Co.,Ltd  
[  428.411150] Initializing USB Mass Storage driver...
[  428.411258] scsi6 : usb-storage 5-1:1.0
[  428.411322] usbcore: registered new interface driver usb-storage
[  428.411323] USB Mass Storage support registered.
[  429.414474] scsi 6:0:0:0: Direct-Access     Samsung  E2121L  0        USB  PQ: 0 ANSI: 0 CCS
[  429.419153] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  429.468417] sd 6:0:0:0: [sdb] 494080 512-byte logical blocks: (252 MB/241 MiB)
[  429.474408] sd 6:0:0:0: [sdb] Write Protect is off
[  429.474420] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  429.480449] sd 6:0:0:0: [sdb] No Caching mode page found
[  429.480460] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  429.510457] sd 6:0:0:0: [sdb] No Caching mode page found
[  429.510469] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  429.519478]  sdb: sdb1
[  429.557454] sd 6:0:0:0: [sdb] No Caching mode page found
[  429.557466] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  429.557474] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  437.153042] FAT-fs (sdb1): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[  589.304660] fuse init (API version 7.17)
```

dmesg output:
```
[  802.190654] sd 6:0:0:0: [sdb] Unhandled error code
[  802.190663] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[  802.190673] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 05 8e 40 00 00 f0 00
[  802.190693] end_request: I/O error, dev sdb, sector 364096
[  833.000104] usb 5-1: reset full-speed USB device number 3 using ohci_hcd
[  863.976119] usb 5-1: reset full-speed USB device number 3 using ohci_hcd
[  895.016116] usb 5-1: reset full-speed USB device number 3 using ohci_hcd
[  925.992100] usb 5-1: reset full-speed USB device number 3 using ohci_hcd
[  956.968114] usb 5-1: reset full-speed USB device number 3 using ohci_hcd
[  960.836118] INFO: task udisks-daemon:4131 blocked for more than 120 seconds.
[  960.836127] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  960.836134] udisks-daemon   D ffff88012fc13780     0  4131   4105 0x00000000
[  960.836147]  ffff880128e2c880 0000000000000082 ffff880128e2c880 ffff8800cfaea0c0
[  960.836158]  0000000000013780 ffff880127c0dfd8 ffff880127c0dfd8 ffff880128e2c880
[  960.836167]  0000000000000000 ffffffff81040d9e ffff880129cc0b80 7fffffffffffffff
[  960.836177] Call Trace:
[  960.836192]  [<ffffffff81040d9e>] ? select_task_rq_fair+0x421/0x667
[  960.836204]  [<ffffffff8134fabb>] ? schedule_timeout+0x2c/0xdb
[  960.836213]  [<ffffffff810371fc>] ? test_tsk_need_resched+0xa/0x13
[  960.836222]  [<ffffffff8103b077>] ? check_preempt_curr+0x52/0x5f
[  960.836230]  [<ffffffff8134f701>] ? wait_for_common+0xa0/0x119
[  960.836237]  [<ffffffff8103f6d2>] ? try_to_wake_up+0x197/0x197
[  960.836244]  [<ffffffff8105ad7e>] ? wait_on_work+0xe6/0x11c
[  960.836252]  [<ffffffff8105a3b8>] ? worker_set_flags+0x8f/0x8f
[  960.836260]  [<ffffffff8105b9de>] ? __cancel_work_timer+0xb2/0xf4
[  960.836270]  [<ffffffff811a1181>] ? disk_block_events+0x5b/0x74
[  960.836278]  [<ffffffff811232fc>] ? __blkdev_get+0x92/0x3a9
[  960.836306]  [<ffffffff811238ba>] ? blkdev_get+0x2a7/0x2a7
[  960.836313]  [<ffffffff811237da>] ? blkdev_get+0x1c7/0x2a7
[  960.836321]  [<ffffffff81102f56>] ? path_to_nameidata+0x27/0x3a
[  960.836329]  [<ffffffff8110afe3>] ? dput+0x27/0xee
[  960.836335]  [<ffffffff811238ba>] ? blkdev_get+0x2a7/0x2a7
[  960.836343]  [<ffffffff810f98a0>] ? __dentry_open+0x1ab/0x2c2
[  960.836351]  [<ffffffff81102dac>] ? dget+0x12/0x1e
[  960.836359]  [<ffffffff81105e49>] ? do_last+0x553/0x58d
[  960.836367]  [<ffffffff8110647b>] ? path_openat+0xce/0x33a
[  960.836376]  [<ffffffff81350a17>] ? _raw_spin_unlock_irqrestore+0xe/0xf
[  960.836386]  [<ffffffff811067a9>] ? do_filp_open+0x2a/0x6e
[  960.836393]  [<ffffffff8134f64c>] ? _cond_resched+0x7/0x1c
[  960.836402]  [<ffffffff811b52a9>] ? __strncpy_from_user+0x18/0x48
[  960.836411]  [<ffffffff8110f52f>] ? alloc_fd+0x64/0x109
[  960.836419]  [<ffffffff810fa775>] ? do_sys_open+0x5e/0xe5
[  960.836427]  [<ffffffff81355a92>] ? system_call_fastpath+0x16/0x1b
[  988.008073] usb 5-1: reset full-speed USB device number 3 using ohci_hcd
[  988.174734] sd 6:0:0:0: [sdb] Unhandled error code
[  988.174744] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[  988.174754] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 05 8f 40 00 00 f0 00
[  988.174773] end_request: I/O error, dev sdb, sector 364352
```
Any help to make it work will be appreciated, thanks!

---

### Post by SeijiSensei on 2015-03-23
Have you tried copying all the files to your hard drive, then reformatting the drive?  Either do that in Windows or, in Linux, run
```
sudo mkfs -t vfat /dev/sdb1
```

---

### Post by nargaroth_reg on 2015-03-28
Thanks for your suggestion, I did that on windows but I'm still getting the same errors on linux unfortunately.

---

