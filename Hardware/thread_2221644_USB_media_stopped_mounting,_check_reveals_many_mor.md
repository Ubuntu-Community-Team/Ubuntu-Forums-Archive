---
title: "USB media stopped mounting, check reveals many more errors"
date: 2014-05-03
forum: Hardware
---

### Post by nonkreon on 2014-05-03
Hello,
Last night before I went to bed, my usb media were mounted, readable and writable. Today I woke up and booted up to see none of my usb media were mountable, neither at system start nor hot plugging. Following the general tip in community help wiki I ran dmesg and the following lines catch my interest:
```
[  241.229771] INFO: task kworker/u8:4:134 blocked for more than 120 seconds.
[  241.229782]       Tainted: GF          O 3.13.0-24-generic #46-Ubuntu
[  241.229786] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  241.229792] kworker/u8:4    D ffff88011fc14440     0   134      2 0x00000000
[  241.229808] Workqueue: events_unbound async_run_entry_fn
[  241.229812]  ffff8800cf111a38 0000000000000002 ffff8800cf8eafe0 ffff8800cf111fd8
[  241.229820]  0000000000014440 0000000000014440 ffff8800cf8eafe0 ffff88011fc14cd8
[  241.229827]  ffff88011ffcc1e8 ffff8800cf111ac0 0000000000000002 ffffffff8114df10
[  241.229834] Call Trace:
[  241.229847]  [<ffffffff8114df10>] ? wait_on_page_read+0x60/0x60
[  241.229856]  [<ffffffff8171a1ad>] io_schedule+0x9d/0x140
[  241.229863]  [<ffffffff8114df1e>] sleep_on_page+0xe/0x20
[  241.229869]  [<ffffffff8171a738>] __wait_on_bit_lock+0x48/0xb0
[  241.229876]  [<ffffffff811f23a0>] ? blkdev_write_begin+0x30/0x30
[  241.229882]  [<ffffffff8114e02a>] __lock_page+0x6a/0x70
[  241.229892]  [<ffffffff810aaed0>] ? autoremove_wake_function+0x40/0x40
[  241.229897]  [<ffffffff811f23b8>] ? blkdev_readpage+0x18/0x20
[  241.229903]  [<ffffffff8114ee40>] do_read_cache_page+0x100/0x1a0
[  241.229910]  [<ffffffff8114ef19>] read_cache_page+0x19/0x30
[  241.229918]  [<ffffffff8134386d>] read_dev_sector+0x2d/0x90
[  241.229924]  [<ffffffff813445f0>] ? check_partition+0x240/0x240
[  241.229930]  [<ffffffff81344660>] adfspart_check_ICS+0x70/0x280
[  241.229938]  [<ffffffff81368bd9>] ? snprintf+0x39/0x40
[  241.229944]  [<ffffffff813445f0>] ? check_partition+0x240/0x240
[  241.229950]  [<ffffffff813444b8>] check_partition+0x108/0x240
[  241.229957]  [<ffffffff813440e4>] rescan_partitions+0xb4/0x2c0
[  241.229962]  [<ffffffff811f3714>] __blkdev_get+0x384/0x4c0
[  241.229968]  [<ffffffff811f3a15>] blkdev_get+0x1c5/0x340
[  241.229974]  [<ffffffff811d34f0>] ? unlock_new_inode+0x50/0x70
[  241.229978]  [<ffffffff811f2263>] ? bdget+0x133/0x150
[  241.229985]  [<ffffffff81341981>] add_disk+0x3a1/0x4b0
[  241.229991]  [<ffffffff8149b9b4>] ? __pm_runtime_use_autosuspend+0x54/0xa0
[  241.229999]  [<ffffffff814eb345>] sd_probe_async+0x135/0x200
[  241.230004]  [<ffffffff81091517>] async_run_entry_fn+0x37/0x130
[  241.230011]  [<ffffffff810838a2>] process_one_work+0x182/0x450
[  241.230017]  [<ffffffff81084641>] worker_thread+0x121/0x410
[  241.230023]  [<ffffffff81084520>] ? rescuer_thread+0x3e0/0x3e0
[  241.230030]  [<ffffffff8108b312>] kthread+0xd2/0xf0
[  241.230036]  [<ffffffff8108b240>] ? kthread_create_on_node+0x1d0/0x1d0
[  241.230043]  [<ffffffff8172637c>] ret_from_fork+0x7c/0xb0
[  241.230049]  [<ffffffff8108b240>] ? kthread_create_on_node+0x1d0/0x1d0
[  241.230111] INFO: task udisksd:3004 blocked for more than 120 seconds.
[  241.230116]       Tainted: GF          O 3.13.0-24-generic #46-Ubuntu
[  241.230118] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  241.230122] udisksd         D ffff88011fd14440     0  3004      1 0x00000000
[  241.230128]  ffff8800a4b6db30 0000000000000002 ffff8800a5b517f0 ffff8800a4b6dfd8
[  241.230135]  0000000000014440 0000000000014440 ffff8800a5b517f0 ffff88011b029d58
[  241.230142]  ffff88011b029d5c ffff8800a5b517f0 00000000ffffffff ffff88011b029d60
[  241.230148] Call Trace:
[  241.230155]  [<ffffffff8171a3a9>] schedule_preempt_disabled+0x29/0x70
[  241.230161]  [<ffffffff8171c215>] __mutex_lock_slowpath+0x135/0x1b0
[  241.230166]  [<ffffffff8171c2af>] mutex_lock+0x1f/0x2f
[  241.230171]  [<ffffffff811f33f3>] __blkdev_get+0x63/0x4c0
[  241.230177]  [<ffffffff811f3a15>] blkdev_get+0x1c5/0x340
[  241.230182]  [<ffffffff811f216e>] ? bdget+0x3e/0x150
[  241.230187]  [<ffffffff811f3c3b>] blkdev_open+0x5b/0x80
[  241.230192]  [<ffffffff811b6997>] do_dentry_open+0x1c7/0x2e0
[  241.230198]  [<ffffffff811f3be0>] ? blkdev_get_by_dev+0x50/0x50
[  241.230203]  [<ffffffff811b6d39>] vfs_open+0x49/0x50
[  241.230209]  [<ffffffff811c6c61>] do_last+0x561/0x1200
[  241.230216]  [<ffffffff8130e23b>] ? apparmor_file_alloc_security+0x5b/0x180
[  241.230222]  [<ffffffff811c8d7b>] path_openat+0xbb/0x620
[  241.230229]  [<ffffffff811ca13a>] do_filp_open+0x3a/0x90
[  241.230236]  [<ffffffff811d6f27>] ? __alloc_fd+0xa7/0x130
[  241.230242]  [<ffffffff811b8859>] do_sys_open+0x129/0x280
[  241.230249]  [<ffffffff81020d35>] ? syscall_trace_enter+0x145/0x250
[  241.230255]  [<ffffffff811b89ce>] SyS_open+0x1e/0x20
[  241.230260]  [<ffffffff8172663f>] tracesys+0xe1/0xe6
[  241.230269] INFO: task hdparm:3091 blocked for more than 120 seconds.
[  241.230273]       Tainted: GF          O 3.13.0-24-generic #46-Ubuntu
[  241.230276] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  241.230279] hdparm          D ffff88011fd14440     0  3091   3060 0x00000000
[  241.230284]  ffff8800a003db30 0000000000000002 ffff8800a0040000 ffff8800a003dfd8
[  241.230291]  0000000000014440 0000000000014440 ffff8800a0040000 ffff88011b029d58
[  241.230297]  ffff88011b029d5c ffff8800a0040000 00000000ffffffff ffff88011b029d60
[  241.230305] Call Trace:
[  241.230312]  [<ffffffff8171a3a9>] schedule_preempt_disabled+0x29/0x70
[  241.230317]  [<ffffffff8171c215>] __mutex_lock_slowpath+0x135/0x1b0
[  241.230323]  [<ffffffff8171c2af>] mutex_lock+0x1f/0x2f
[  241.230328]  [<ffffffff811f33f3>] __blkdev_get+0x63/0x4c0
[  241.230333]  [<ffffffff811f3a15>] blkdev_get+0x1c5/0x340
[  241.230339]  [<ffffffff811f3c3b>] blkdev_open+0x5b/0x80
[  241.230344]  [<ffffffff811b6997>] do_dentry_open+0x1c7/0x2e0
[  241.230349]  [<ffffffff811f3be0>] ? blkdev_get_by_dev+0x50/0x50
[  241.230354]  [<ffffffff811b6d39>] vfs_open+0x49/0x50
[  241.230359]  [<ffffffff811c6c61>] do_last+0x561/0x1200
[  241.230365]  [<ffffffff8130e23b>] ? apparmor_file_alloc_security+0x5b/0x180
[  241.230372]  [<ffffffff811c8d7b>] path_openat+0xbb/0x620
[  241.230380]  [<ffffffff8115683a>] ? __free_pages+0x5a/0x60
[  241.230386]  [<ffffffff811ca13a>] do_filp_open+0x3a/0x90
[  241.230392]  [<ffffffff811d6f27>] ? __alloc_fd+0xa7/0x130
[  241.230398]  [<ffffffff811b8859>] do_sys_open+0x129/0x280
[  241.230404]  [<ffffffff81020d35>] ? syscall_trace_enter+0x145/0x250
[  241.230409]  [<ffffffff811b89ce>] SyS_open+0x1e/0x20
[  241.230415]  [<ffffffff8172663f>] tracesys+0xe1/0xe6
[  241.230436] INFO: task hddtemp:3219 blocked for more than 120 seconds.
[  241.230440]       Tainted: GF          O 3.13.0-24-generic #46-Ubuntu
[  241.230443] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  241.230445] hddtemp         D ffff88011fc14440     0  3219   3006 0x00000000
[  241.230451]  ffff88009cd37b30 0000000000000002 ffff88009cc1c7d0 ffff88009cd37fd8
[  241.230457]  0000000000014440 0000000000014440 ffff88009cc1c7d0 ffff88011b029d58
[  241.230463]  ffff88011b029d5c ffff88009cc1c7d0 00000000ffffffff ffff88011b029d60
[  241.230469] Call Trace:
[  241.230475]  [<ffffffff8171a3a9>] schedule_preempt_disabled+0x29/0x70
[  241.230481]  [<ffffffff8171c215>] __mutex_lock_slowpath+0x135/0x1b0
[  241.230487]  [<ffffffff8171c2af>] mutex_lock+0x1f/0x2f
[  241.230492]  [<ffffffff811f33f3>] __blkdev_get+0x63/0x4c0
[  241.230497]  [<ffffffff811f3a15>] blkdev_get+0x1c5/0x340
[  241.230502]  [<ffffffff811f3c3b>] blkdev_open+0x5b/0x80
[  241.230507]  [<ffffffff811b6997>] do_dentry_open+0x1c7/0x2e0
[  241.230512]  [<ffffffff811f3be0>] ? blkdev_get_by_dev+0x50/0x50
[  241.230517]  [<ffffffff811b6d39>] vfs_open+0x49/0x50
[  241.230522]  [<ffffffff811c6c61>] do_last+0x561/0x1200
[  241.230528]  [<ffffffff8130e23b>] ? apparmor_file_alloc_security+0x5b/0x180
[  241.230535]  [<ffffffff811c8d7b>] path_openat+0xbb/0x620
[  241.230541]  [<ffffffff8117d38d>] ? vma_link+0x7d/0xc0
[  241.230548]  [<ffffffff811ca13a>] do_filp_open+0x3a/0x90
[  241.230554]  [<ffffffff811d6f27>] ? __alloc_fd+0xa7/0x130
[  241.230559]  [<ffffffff811b8859>] do_sys_open+0x129/0x280
[  241.230565]  [<ffffffff81020d35>] ? syscall_trace_enter+0x145/0x250
[  241.230571]  [<ffffffff811b89ce>] SyS_open+0x1e/0x20
[  241.230576]  [<ffffffff8172663f>] tracesys+0xe1/0xe6
[  241.230580] INFO: task udisks-daemon:3230 blocked for more than 120 seconds.
[  241.230584]       Tainted: GF          O 3.13.0-24-generic #46-Ubuntu
[  241.230587] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  241.230589] udisks-daemon   D ffff88011fd14440     0  3230      1 0x00000000
[  241.230594]  ffff88009cdb3b30 0000000000000002 ffff88009ccb0000 ffff88009cdb3fd8
[  241.230600]  0000000000014440 0000000000014440 ffff88009ccb0000 ffff88011b029d58
[  241.230607]  ffff88011b029d5c ffff88009ccb0000 00000000ffffffff ffff88011b029d60
[  241.230613] Call Trace:
[  241.230619]  [<ffffffff8171a3a9>] schedule_preempt_disabled+0x29/0x70
[  241.230625]  [<ffffffff8171c215>] __mutex_lock_slowpath+0x135/0x1b0
[  241.230630]  [<ffffffff8171c2af>] mutex_lock+0x1f/0x2f
[  241.230635]  [<ffffffff811f33f3>] __blkdev_get+0x63/0x4c0
[  241.230641]  [<ffffffff811f3a15>] blkdev_get+0x1c5/0x340
[  241.230646]  [<ffffffff811f3c3b>] blkdev_open+0x5b/0x80
[  241.230651]  [<ffffffff811b6997>] do_dentry_open+0x1c7/0x2e0
[  241.230656]  [<ffffffff811f3be0>] ? blkdev_get_by_dev+0x50/0x50
[  241.230661]  [<ffffffff811b6d39>] vfs_open+0x49/0x50
[  241.230666]  [<ffffffff811c6c61>] do_last+0x561/0x1200
[  241.230672]  [<ffffffff8130e23b>] ? apparmor_file_alloc_security+0x5b/0x180
[  241.230678]  [<ffffffff811c8d7b>] path_openat+0xbb/0x620
[  241.230685]  [<ffffffff81174ae5>] ? tlb_finish_mmu+0x55/0x60
[  241.230690]  [<ffffffff811ca13a>] do_filp_open+0x3a/0x90
[  241.230697]  [<ffffffff811d6f27>] ? __alloc_fd+0xa7/0x130
[  241.230702]  [<ffffffff811b8859>] do_sys_open+0x129/0x280
[  241.230708]  [<ffffffff81020d35>] ? syscall_trace_enter+0x145/0x250
[  241.230714]  [<ffffffff811b89ce>] SyS_open+0x1e/0x20
[  241.230719]  [<ffffffff8172663f>] tracesys+0xe1/0xe6
[  245.853803] usb 2-4: reset high-speed USB device number 3 using ehci-pci
[  245.986467] sd 7:0:0:0: [sdc] Unhandled error code
[  245.986478] sd 7:0:0:0: [sdc]  
[  245.986482] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[  245.986487] sd 7:0:0:0: [sdc] CDB: 
[  245.986490] Read(10): 28 00 00 00 00 00 00 00 08 00
[  245.986510] end_request: I/O error, dev sdc, sector 0
[  245.986517] Buffer I/O error on device sdc, logical block 0

```
Why the sudden errors out of nowhere?

Thanks in advance,

---

