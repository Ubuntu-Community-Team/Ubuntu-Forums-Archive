---
title: "USB3 Corrupts data copied to drives."
date: 2013-06-29
forum: Hardware
---

### Post by naviathan on 2013-06-29
I've been having this issue with all variants of Linux (Ubuntu, Ubuntu Gnome, Gentoo, Fedora, etc...) I think it's either a kernel or hardware issue. I'm running an ASROCK Z77 Pro 4 motherboard. Using the intel USB3 ports (any of them). I can plug in an external hard drive or thumb drive and start copying data. The first 10-20MB seem to go ok. Somtimes I can get even a GB or more, but eventually it starts running slower than dirt and corrupting the data it's copying. It looks like the USB root hub starts reseting. Here's some related dmesg output from a file copy:
```
 sd 10:0:0:0: [sdc]  [20830.258026] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[20830.258028] sd 10:0:0:0: [sdc] CDB: 
[20830.258030] Write(10): 2a 00 15 dc 15 80 00 00 08 00
[20830.258040] end_request: I/O error, dev sdc, sector 366744960
[20830.258044] Buffer I/O error on device sdc1, logical block 45842864
[20830.258046] lost page write due to I/O error on sdc1
[20830.369554] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[20830.385781] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a40
[20830.385786] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a00
[20830.505442] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[20830.521677] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a40
[20830.521682] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a00
[20830.641284] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[20830.657536] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a40
[20830.657541] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a00
[20830.777158] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[20830.793143] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a40
[20830.793148] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a00
[20830.912987] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[20830.929240] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a40
[20830.929245] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a00
[20831.048854] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[20831.065074] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a40
[20831.065079] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a00
[20831.065202] sd 10:0:0:0: [sdc] Unhandled error code
[20831.065205] sd 10:0:0:0: [sdc]  
[20831.065207] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[20831.065209] sd 10:0:0:0: [sdc] CDB: 
[20831.065211] Write(10): 2a 00 15 dc 95 80 00 00 20 00
[20831.065221] end_request: I/O error, dev sdc, sector 366777728
[20831.065225] Buffer I/O error on device sdc1, logical block 45846960
[20831.065227] lost page write due to I/O error on sdc1
[20831.065231] Buffer I/O error on device sdc1, logical block 45846961
[20831.065233] lost page write due to I/O error on sdc1
[20831.065235] Buffer I/O error on device sdc1, logical block 45846962
[20831.065237] lost page write due to I/O error on sdc1
[20831.065239] Buffer I/O error on device sdc1, logical block 45846963
[20831.065241] lost page write due to I/O error on sdc1
[20831.176758] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[20831.192943] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a40
[20831.192946] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a00
[20831.312633] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[20831.328851] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a40
[20831.328856] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a00
[20831.448511] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[20831.464728] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a40
[20831.464733] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a00
[20831.584328] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[20831.601118] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a40
[20831.601123] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a00
[20861.882965] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[20861.899227] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a40
[20861.899232] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a00
[20892.924827] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[20892.941026] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a40
[20892.941031] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a00
[20892.941286] sd 10:0:0:0: [sdc] Unhandled error code
[20892.941291] sd 10:0:0:0: [sdc]  
[20892.941293] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[20892.941296] sd 10:0:0:0: [sdc] CDB: 
[20892.941297] Read(10): 28 00 1d 1c 60 d0 00 00 f0 00
[20892.941307] end_request: I/O error, dev sdc, sector 488399056
[20892.941312] Buffer I/O error on device sdc1, logical block 61049626
[20892.941315] Buffer I/O error on device sdc1, logical block 61049627
[20892.941318] Buffer I/O error on device sdc1, logical block 61049628
[20892.941320] Buffer I/O error on device sdc1, logical block 61049629
[20892.941322] Buffer I/O error on device sdc1, logical block 61049630
[20892.941325] Buffer I/O error on device sdc1, logical block 61049631
[20892.941327] Buffer I/O error on device sdc1, logical block 61049632
[20892.941330] Buffer I/O error on device sdc1, logical block 61049633
[20892.941332] Buffer I/O error on device sdc1, logical block 61049634
[20892.941334] Buffer I/O error on device sdc1, logical block 61049635
[20923.870747] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[20923.887139] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a40
[20923.887144] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a00
[20954.816739] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[20954.832967] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a40
[20954.832973] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a00
[20954.944569] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[20954.960825] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a40
[20954.960830] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8803b3629a00
[20980.219854] INFO: task flush-8:32:20128 blocked for more than 120 seconds.
[20980.219859] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[20980.219861] flush-8:32      D ffff88042f393f40     0 20128      2 0x00000000
[20980.219866]  ffff88040e1517f0 0000000000000046 ffff88037ae40000 ffff88040e151fd8
[20980.219871]  ffff88040e151fd8 ffff88040e151fd8 ffff880418d5c5c0 ffff88037ae40000
[20980.219875]  ffff88037ae40000 ffff88042f3947f8 ffff880415552f10 ffff880415552ee0
[20980.219879] Call Trace:
[20980.219888]  [<ffffffff816ca8a9>] schedule+0x29/0x70
[20980.219892]  [<ffffffff816ca97f>] io_schedule+0x8f/0xd0
[20980.219897]  [<ffffffff81325a67>] get_request+0x197/0x6d0
[20980.219902]  [<ffffffff8107dc80>] ? finish_wait+0x80/0x80
[20980.219906]  [<ffffffff8132704d>] blk_queue_bio+0x7d/0x3d0
[20980.219909]  [<ffffffff813254b2>] generic_make_request+0xc2/0x110
[20980.219913]  [<ffffffff813257e9>] submit_bio+0x79/0x160
[20980.219917]  [<ffffffff811cac35>] ? bio_alloc_bioset+0x65/0x120
[20980.219922]  [<ffffffff811c5ea2>] submit_bh+0x112/0x1e0
[20980.219926]  [<ffffffff811c7d70>] __block_write_full_page+0x1e0/0x350
[20980.219929]  [<ffffffff811c7540>] ? __bread+0xa0/0xa0
[20980.219932]  [<ffffffff811cbd70>] ? I_BDEV+0x10/0x10
[20980.219935]  [<ffffffff811cbd70>] ? I_BDEV+0x10/0x10
[20980.219938]  [<ffffffff811c831b>] block_write_full_page_endio+0xfb/0x100
[20980.219942]  [<ffffffff811c8335>] block_write_full_page+0x15/0x20
[20980.219945]  [<ffffffff811cc3e8>] blkdev_writepage+0x18/0x20
[20980.219950]  [<ffffffff81138af3>] __writepage+0x13/0x40
[20980.219954]  [<ffffffff8113951a>] write_cache_pages+0x22a/0x460
[20980.219958]  [<ffffffff81138ae0>] ? mapping_tagged+0x20/0x20
[20980.219963]  [<ffffffff8113979a>] generic_writepages+0x4a/0x70
[20980.219967]  [<ffffffff8113a70e>] do_writepages+0x1e/0x40
[20980.219971]  [<ffffffff811bd8ab>] __writeback_single_inode+0x3b/0x160
[20980.219974]  [<ffffffff811be935>] writeback_sb_inodes+0x195/0x380
[20980.219978]  [<ffffffff811bebbf>] __writeback_inodes_wb+0x9f/0xd0
[20980.219982]  [<ffffffff811bee33>] wb_writeback+0x243/0x2c0
[20980.219986]  [<ffffffff811bfff8>] wb_do_writeback+0x158/0x200
[20980.219989]  [<ffffffff811c012b>] bdi_writeback_thread+0x8b/0x210
[20980.219993]  [<ffffffff811c00a0>] ? wb_do_writeback+0x200/0x200
[20980.219996]  [<ffffffff8107d370>] kthread+0xc0/0xd0
[20980.219999]  [<ffffffff8107d2b0>] ? kthread_create_on_node+0x120/0x120
[20980.220004]  [<ffffffff816d3fac>] ret_from_fork+0x7c/0xb0
[20980.220007]  [<ffffffff8107d2b0>] ? kthread_create_on_node+0x120/0x120



```
Any ideas? I've seen lots of reports on this issue, but they all say that kernel 3.4 fixed it. I'm on kernel 3.8 and it's still an issue.

---

### Post by oldfred on 2013-06-29
One user posted this:

>  So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!

So it seems with Asrock any Asmedia ports are not configured correctly. 
Is your USB using that?



---

### Post by naviathan on 2013-06-29
Considering the ASMedia ports are SATA ports, not USB ports, no I'm not connecting them to the ASMedia ports. Although I do use those SATA ports. They're fine for hard drives, it's optical drives I had issues with.

---

