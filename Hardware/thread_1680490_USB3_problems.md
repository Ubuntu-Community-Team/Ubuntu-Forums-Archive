---
title: "USB3 problems"
date: 2011-02-02
forum: Hardware
---

### Post by jethro1138 on 2011-02-02
Hey there,

I know USB3 is supposedly supported with current Linux kernels. I just got a motherboard that has USB3 ports and figured, hey, since I have a USB3 harddrive dock, lets give it a shot.

Except it completely doesn't work. It gets detected, but then errors start showing up, and you can't actually access any of the drives. 

Has anyone got USB3 working, specifically on Ubuntu 10.00 x86_64? The motherboard is a Gigabyte GA-X58-USB3. Here's my /var/log/messages when I plug the thing in and try to mkfs on /dev/sdd1:

```

Feb  2 14:30:20 dragon kernel: [  110.900434] usb 9-2: new SuperSpeed USB device using xhci_hcd and address 2
Feb  2 14:30:20 dragon kernel: [  110.921882] xhci_hcd 0000:01:00.0: WARN: short transfer on control ep
Feb  2 14:30:20 dragon kernel: [  110.922257] xhci_hcd 0000:01:00.0: WARN: short transfer on control ep
Feb  2 14:30:20 dragon kernel: [  110.922633] xhci_hcd 0000:01:00.0: WARN: short transfer on control ep
Feb  2 14:30:20 dragon kernel: [  110.922972] xhci_hcd 0000:01:00.0: WARN: short transfer on control ep
Feb  2 14:30:20 dragon kernel: [  111.015539] Initializing USB Mass Storage driver...
Feb  2 14:30:20 dragon kernel: [  111.016044] scsi6 : usb-storage 9-2:1.0
Feb  2 14:30:20 dragon kernel: [  111.016401] usbcore: registered new interface driver usb-storage
Feb  2 14:30:20 dragon kernel: [  111.016405] USB Mass Storage support registered.
Feb  2 14:30:21 dragon kernel: [  112.007711] scsi 6:0:0:0: Direct-Access     Jmicron  Corp.            0000 PQ: 0 ANSI: 2 CCS
Feb  2 14:30:21 dragon kernel: [  112.008627] sd 6:0:0:0: Attached scsi generic sg4 type 0
Feb  2 14:30:21 dragon kernel: [  112.008969] sd 6:0:0:0: [sdd] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Feb  2 14:30:21 dragon kernel: [  112.009146] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
Feb  2 14:30:21 dragon kernel: [  112.009876] sd 6:0:0:0: [sdd] Write Protect is off
Feb  2 14:30:21 dragon kernel: [  112.010689] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
Feb  2 14:30:21 dragon kernel: [  112.011211]  sdd: sdd1
Feb  2 14:30:21 dragon kernel: [  112.030642] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
Feb  2 14:30:21 dragon kernel: [  112.031193] sd 6:0:0:0: [sdd] Attached SCSI disk
Feb  2 14:30:48 dragon kernel: [  138.819343] lo: Disabled Privacy Extensions
Feb  2 14:31:11 dragon kernel: [  161.114868] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
Feb  2 14:31:11 dragon kernel: [  161.115836] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
Feb  2 14:31:11 dragon kernel: [  161.121875] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
Feb  2 14:31:11 dragon kernel: [  161.127614] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
Feb  2 14:31:11 dragon kernel: [  161.227730] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
Feb  2 14:32:55 dragon kernel: [  265.294467] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
Feb  2 14:32:55 dragon kernel: [  265.295012]  sdd: sdd1
Feb  2 14:32:55 dragon kernel: [  265.316705] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
Feb  2 14:32:55 dragon kernel: [  265.375901] xhci_hcd 0000:01:00.0: WARN: Stalled endpoint
Feb  2 14:33:05 dragon kernel: [  275.689879] xhci_hcd 0000:01:00.0: WARN: transfer error on endpoint
Feb  2 14:33:56 dragon kernel: [  325.647535] xhci_hcd 0000:01:00.0: Timeout while waiting for a slot
Feb  2 14:34:46 dragon kernel: [  375.683096] xhci_hcd 0000:01:00.0: Timeout while waiting for a slot
Feb  2 14:35:36 dragon kernel: [  425.829724] xhci_hcd 0000:01:00.0: Timeout while waiting for reset device command
Feb  2 14:36:26 dragon kernel: [  475.927775] xhci_hcd 0000:01:00.0: Timeout while waiting for reset device command
Feb  2 14:36:31 dragon kernel: [  480.123489] scsi_eh_6     D 000000010000029e     0  2192      2 0x00000000
Feb  2 14:36:31 dragon kernel: [  480.123495]  ffff8803499fbc40 0000000000000046 ffffffffffffffff 0000000000015980
Feb  2 14:36:31 dragon kernel: [  480.123500]  ffff8803499fbfd8 0000000000015980 ffff8803499fbfd8 ffff88034e6a16e0
Feb  2 14:36:31 dragon kernel: [  480.123504]  0000000000015980 0000000000015980 ffff8803499fbfd8 0000000000015980
Feb  2 14:36:31 dragon kernel: [  480.123508] Call Trace:
Feb  2 14:36:31 dragon kernel: [  480.123517]  [<ffffffff81588c7d>] schedule_timeout+0x22d/0x310
Feb  2 14:36:31 dragon kernel: [  480.123522]  [<ffffffff8158885b>] wait_for_common+0xdb/0x180
Feb  2 14:36:31 dragon kernel: [  480.123526]  [<ffffffff81056a00>] ? default_wake_function+0x0/0x20
Feb  2 14:36:31 dragon kernel: [  480.123530]  [<ffffffff815889dd>] wait_for_completion+0x1d/0x20
Feb  2 14:36:31 dragon kernel: [  480.123536]  [<ffffffffa02c4ac7>] command_abort+0x97/0xc0 [usb_storage]
Feb  2 14:36:31 dragon kernel: [  480.123541]  [<ffffffff813b126b>] scsi_eh_abort_cmds+0x6b/0x1a0
Feb  2 14:36:31 dragon kernel: [  480.123545]  [<ffffffff813b227b>] scsi_unjam_host+0xdb/0x220
Feb  2 14:36:31 dragon kernel: [  480.123549]  [<ffffffff813b2500>] scsi_error_handler+0x140/0x190
Feb  2 14:36:31 dragon kernel: [  480.123552]  [<ffffffff813b23c0>] ? scsi_error_handler+0x0/0x190
Feb  2 14:36:31 dragon kernel: [  480.123557]  [<ffffffff8107f266>] kthread+0x96/0xa0
Feb  2 14:36:31 dragon kernel: [  480.123561]  [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
Feb  2 14:36:31 dragon kernel: [  480.123565]  [<ffffffff8107f1d0>] ? kthread+0x0/0xa0
Feb  2 14:36:31 dragon kernel: [  480.123568]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
Feb  2 14:36:31 dragon kernel: [  480.123584] badblocks     D 00000000fffff6c4     0  2573   2571 0x00000004
Feb  2 14:36:31 dragon kernel: [  480.123589]  ffff88032e06db98 0000000000000082 ffff880300000000 0000000000015980
Feb  2 14:36:31 dragon kernel: [  480.123593]  ffff88032e06dfd8 0000000000015980 ffff88032e06dfd8 ffff88034b1896e0
Feb  2 14:36:31 dragon kernel: [  480.123597]  0000000000015980 0000000000015980 ffff88032e06dfd8 0000000000015980
Feb  2 14:36:31 dragon kernel: [  480.123601] Call Trace:
Feb  2 14:36:31 dragon kernel: [  480.123605]  [<ffffffff81588693>] io_schedule+0x73/0xc0
Feb  2 14:36:31 dragon kernel: [  480.123611]  [<ffffffff81185f9f>] dio_await_completion+0x5f/0xd0
Feb  2 14:36:31 dragon kernel: [  480.123615]  [<ffffffff811863d3>] direct_io_worker+0x2e3/0x380
Feb  2 14:36:31 dragon kernel: [  480.123620]  [<ffffffff811867c0>] __blockdev_direct_IO_newtrunc+0x260/0x330
Feb  2 14:36:31 dragon kernel: [  480.123624]  [<ffffffff81182e50>] ? blkdev_get_blocks+0x0/0xc0
Feb  2 14:36:31 dragon kernel: [  480.123628]  [<ffffffff810664d7>] ? current_fs_time+0x27/0x30
Feb  2 14:36:31 dragon kernel: [  480.123632]  [<ffffffff81184077>] blkdev_direct_IO+0x57/0x60
Feb  2 14:36:31 dragon kernel: [  480.123636]  [<ffffffff81182e50>] ? blkdev_get_blocks+0x0/0xc0
Feb  2 14:36:31 dragon kernel: [  480.123640]  [<ffffffff81102d35>] generic_file_aio_read+0x215/0x230
Feb  2 14:36:31 dragon kernel: [  480.123644]  [<ffffffff811030d9>] ? filemap_fault+0xb9/0x450
Feb  2 14:36:31 dragon kernel: [  480.123648]  [<ffffffff81152d3a>] do_sync_read+0xda/0x120
Feb  2 14:36:31 dragon kernel: [  480.123653]  [<ffffffff81120fe9>] ? handle_mm_fault+0x1b9/0x440
Feb  2 14:36:31 dragon kernel: [  480.123659]  [<ffffffff81290a48>] ? apparmor_file_permission+0x18/0x20
Feb  2 14:36:31 dragon kernel: [  480.123664]  [<ffffffff8125ff16>] ? security_file_permission+0x16/0x20
Feb  2 14:36:31 dragon kernel: [  480.123668]  [<ffffffff811535b5>] vfs_read+0xb5/0x1a0
Feb  2 14:36:31 dragon kernel: [  480.123671]  [<ffffffff811536f1>] sys_read+0x51/0x80
Feb  2 14:36:31 dragon kernel: [  480.123676]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
Feb  2 14:37:17 dragon kernel: [  526.044053] xhci_hcd 0000:01:00.0: Timeout while waiting for reset device command
Feb  2 14:38:07 dragon kernel: [  576.184694] xhci_hcd 0000:01:00.0: Timeout while waiting for reset device command
Feb  2 14:38:31 dragon kernel: [  599.793083] scsi_eh_6     D 000000010000029e     0  2192      2 0x00000000
Feb  2 14:38:31 dragon kernel: [  599.793088]  ffff8803499fbc40 0000000000000046 ffffffffffffffff 0000000000015980
Feb  2 14:38:31 dragon kernel: [  599.793093]  ffff8803499fbfd8 0000000000015980 ffff8803499fbfd8 ffff88034e6a16e0
Feb  2 14:38:31 dragon kernel: [  599.793097]  0000000000015980 0000000000015980 ffff8803499fbfd8 0000000000015980
Feb  2 14:38:31 dragon kernel: [  599.793102] Call Trace:
Feb  2 14:38:31 dragon kernel: [  599.793110]  [<ffffffff81588c7d>] schedule_timeout+0x22d/0x310
Feb  2 14:38:31 dragon kernel: [  599.793115]  [<ffffffff8158885b>] wait_for_common+0xdb/0x180
Feb  2 14:38:31 dragon kernel: [  599.793119]  [<ffffffff81056a00>] ? default_wake_function+0x0/0x20
Feb  2 14:38:31 dragon kernel: [  599.793123]  [<ffffffff815889dd>] wait_for_completion+0x1d/0x20
Feb  2 14:38:31 dragon kernel: [  599.793130]  [<ffffffffa02c4ac7>] command_abort+0x97/0xc0 [usb_storage]
Feb  2 14:38:31 dragon kernel: [  599.793135]  [<ffffffff813b126b>] scsi_eh_abort_cmds+0x6b/0x1a0
Feb  2 14:38:31 dragon kernel: [  599.793138]  [<ffffffff813b227b>] scsi_unjam_host+0xdb/0x220
Feb  2 14:38:31 dragon kernel: [  599.793142]  [<ffffffff813b2500>] scsi_error_handler+0x140/0x190
Feb  2 14:38:31 dragon kernel: [  599.793145]  [<ffffffff813b23c0>] ? scsi_error_handler+0x0/0x190
Feb  2 14:38:31 dragon kernel: [  599.793150]  [<ffffffff8107f266>] kthread+0x96/0xa0
Feb  2 14:38:31 dragon kernel: [  599.793154]  [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
Feb  2 14:38:31 dragon kernel: [  599.793158]  [<ffffffff8107f1d0>] ? kthread+0x0/0xa0
Feb  2 14:38:31 dragon kernel: [  599.793161]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
Feb  2 14:38:31 dragon kernel: [  599.793178] badblocks     D 00000000fffff6c4     0  2573   2571 0x00000004
Feb  2 14:38:31 dragon kernel: [  599.793182]  ffff88032e06db98 0000000000000082 ffff880300000000 0000000000015980
Feb  2 14:38:31 dragon kernel: [  599.793186]  ffff88032e06dfd8 0000000000015980 ffff88032e06dfd8 ffff88034b1896e0
Feb  2 14:38:31 dragon kernel: [  599.793190]  0000000000015980 0000000000015980 ffff88032e06dfd8 0000000000015980
Feb  2 14:38:31 dragon kernel: [  599.793194] Call Trace:
Feb  2 14:38:31 dragon kernel: [  599.793198]  [<ffffffff81588693>] io_schedule+0x73/0xc0
Feb  2 14:38:31 dragon kernel: [  599.793204]  [<ffffffff81185f9f>] dio_await_completion+0x5f/0xd0
Feb  2 14:38:31 dragon kernel: [  599.793208]  [<ffffffff811863d3>] direct_io_worker+0x2e3/0x380
Feb  2 14:38:31 dragon kernel: [  599.793213]  [<ffffffff811867c0>] __blockdev_direct_IO_newtrunc+0x260/0x330
Feb  2 14:38:31 dragon kernel: [  599.793217]  [<ffffffff81182e50>] ? blkdev_get_blocks+0x0/0xc0
Feb  2 14:38:31 dragon kernel: [  599.793221]  [<ffffffff810664d7>] ? current_fs_time+0x27/0x30
Feb  2 14:38:31 dragon kernel: [  599.793225]  [<ffffffff81184077>] blkdev_direct_IO+0x57/0x60
Feb  2 14:38:31 dragon kernel: [  599.793229]  [<ffffffff81182e50>] ? blkdev_get_blocks+0x0/0xc0
Feb  2 14:38:31 dragon kernel: [  599.793234]  [<ffffffff81102d35>] generic_file_aio_read+0x215/0x230
Feb  2 14:38:31 dragon kernel: [  599.793237]  [<ffffffff811030d9>] ? filemap_fault+0xb9/0x450
Feb  2 14:38:31 dragon kernel: [  599.793241]  [<ffffffff81152d3a>] do_sync_read+0xda/0x120
Feb  2 14:38:31 dragon kernel: [  599.793247]  [<ffffffff81120fe9>] ? handle_mm_fault+0x1b9/0x440
Feb  2 14:38:31 dragon kernel: [  599.793252]  [<ffffffff81290a48>] ? apparmor_file_permission+0x18/0x20
Feb  2 14:38:31 dragon kernel: [  599.793257]  [<ffffffff8125ff16>] ? security_file_permission+0x16/0x20
Feb  2 14:38:31 dragon kernel: [  599.793261]  [<ffffffff811535b5>] vfs_read+0xb5/0x1a0
Feb  2 14:38:31 dragon kernel: [  599.793264]  [<ffffffff811536f1>] sys_read+0x51/0x80
Feb  2 14:38:31 dragon kernel: [  599.793269]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
Feb  2 14:38:57 dragon kernel: [  626.324624] xhci_hcd 0000:01:00.0: Timeout while waiting for reset device command
Feb  2 14:39:47 dragon kernel: [  676.313840] xhci_hcd 0000:01:00.0: Timeout while waiting for reset device command
Feb  2 14:40:31 dragon kernel: [  719.478815] scsi_eh_6     D 000000010000029e     0  2192      2 0x00000000
Feb  2 14:40:31 dragon kernel: [  719.478820]  ffff8803499fbc40 0000000000000046 ffffffffffffffff 0000000000015980
Feb  2 14:40:31 dragon kernel: [  719.478825]  ffff8803499fbfd8 0000000000015980 ffff8803499fbfd8 ffff88034e6a16e0
Feb  2 14:40:31 dragon kernel: [  719.478829]  0000000000015980 0000000000015980 ffff8803499fbfd8 0000000000015980
Feb  2 14:40:31 dragon kernel: [  719.478833] Call Trace:
Feb  2 14:40:31 dragon kernel: [  719.478842]  [<ffffffff81588c7d>] schedule_timeout+0x22d/0x310
Feb  2 14:40:31 dragon kernel: [  719.478847]  [<ffffffff8158885b>] wait_for_common+0xdb/0x180
Feb  2 14:40:31 dragon kernel: [  719.478851]  [<ffffffff81056a00>] ? default_wake_function+0x0/0x20
Feb  2 14:40:31 dragon kernel: [  719.478855]  [<ffffffff815889dd>] wait_for_completion+0x1d/0x20
Feb  2 14:40:31 dragon kernel: [  719.478861]  [<ffffffffa02c4ac7>] command_abort+0x97/0xc0 [usb_storage]
Feb  2 14:40:31 dragon kernel: [  719.478866]  [<ffffffff813b126b>] scsi_eh_abort_cmds+0x6b/0x1a0
Feb  2 14:40:31 dragon kernel: [  719.478870]  [<ffffffff813b227b>] scsi_unjam_host+0xdb/0x220
Feb  2 14:40:31 dragon kernel: [  719.478874]  [<ffffffff813b2500>] scsi_error_handler+0x140/0x190
Feb  2 14:40:31 dragon kernel: [  719.478877]  [<ffffffff813b23c0>] ? scsi_error_handler+0x0/0x190
Feb  2 14:40:31 dragon kernel: [  719.478881]  [<ffffffff8107f266>] kthread+0x96/0xa0
Feb  2 14:40:31 dragon kernel: [  719.478886]  [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
Feb  2 14:40:31 dragon kernel: [  719.478890]  [<ffffffff8107f1d0>] ? kthread+0x0/0xa0
Feb  2 14:40:31 dragon kernel: [  719.478893]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
Feb  2 14:40:31 dragon kernel: [  719.478909] badblocks     D 00000000fffff6c4     0  2573   2571 0x00000004
Feb  2 14:40:31 dragon kernel: [  719.478914]  ffff88032e06db98 0000000000000082 ffff880300000000 0000000000015980
Feb  2 14:40:31 dragon kernel: [  719.478918]  ffff88032e06dfd8 0000000000015980 ffff88032e06dfd8 ffff88034b1896e0
Feb  2 14:40:31 dragon kernel: [  719.478922]  0000000000015980 0000000000015980 ffff88032e06dfd8 0000000000015980
Feb  2 14:40:31 dragon kernel: [  719.478926] Call Trace:
Feb  2 14:40:31 dragon kernel: [  719.478930]  [<ffffffff81588693>] io_schedule+0x73/0xc0
Feb  2 14:40:31 dragon kernel: [  719.478936]  [<ffffffff81185f9f>] dio_await_completion+0x5f/0xd0
Feb  2 14:40:31 dragon kernel: [  719.478940]  [<ffffffff811863d3>] direct_io_worker+0x2e3/0x380
Feb  2 14:40:31 dragon kernel: [  719.478944]  [<ffffffff811867c0>] __blockdev_direct_IO_newtrunc+0x260/0x330
Feb  2 14:40:31 dragon kernel: [  719.478949]  [<ffffffff81182e50>] ? blkdev_get_blocks+0x0/0xc0
Feb  2 14:40:31 dragon kernel: [  719.478953]  [<ffffffff810664d7>] ? current_fs_time+0x27/0x30
Feb  2 14:40:31 dragon kernel: [  719.478957]  [<ffffffff81184077>] blkdev_direct_IO+0x57/0x60
Feb  2 14:40:31 dragon kernel: [  719.478960]  [<ffffffff81182e50>] ? blkdev_get_blocks+0x0/0xc0
Feb  2 14:40:31 dragon kernel: [  719.478965]  [<ffffffff81102d35>] generic_file_aio_read+0x215/0x230
Feb  2 14:40:31 dragon kernel: [  719.478969]  [<ffffffff811030d9>] ? filemap_fault+0xb9/0x450
Feb  2 14:40:31 dragon kernel: [  719.478973]  [<ffffffff81152d3a>] do_sync_read+0xda/0x120
Feb  2 14:40:31 dragon kernel: [  719.478978]  [<ffffffff81120fe9>] ? handle_mm_fault+0x1b9/0x440
Feb  2 14:40:31 dragon kernel: [  719.478983]  [<ffffffff81290a48>] ? apparmor_file_permission+0x18/0x20
Feb  2 14:40:31 dragon kernel: [  719.478989]  [<ffffffff8125ff16>] ? security_file_permission+0x16/0x20
Feb  2 14:40:31 dragon kernel: [  719.478992]  [<ffffffff811535b5>] vfs_read+0xb5/0x1a0
Feb  2 14:40:31 dragon kernel: [  719.478995]  [<ffffffff811536f1>] sys_read+0x51/0x80
Feb  2 14:40:31 dragon kernel: [  719.479001]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
Feb  2 14:40:38 dragon kernel: [  726.450761] xhci_hcd 0000:01:00.0: Timeout while waiting for reset device command
Feb  2 14:41:28 dragon kernel: [  776.585408] xhci_hcd 0000:01:00.0: Timeout while waiting for reset device command
Feb  2 14:42:18 dragon kernel: [  826.718164] xhci_hcd 0000:01:00.0: Timeout while waiting for reset device command
Feb  2 14:42:18 dragon kernel: [  826.938455] usb 9-2: USB disconnect, address 2

```

---

### Post by fjgaude on 2011-02-02
I wonder, does the drive work in a USB2 slot?

I have a USB3 MB but have no USB3 device to try to see if Ubuntu 10.10 works with it. I would think that it does. You are using 10.10, and not 10.04?

---

### Post by jethro1138 on 2011-02-02
> **fjgaude said:**
> I wonder, does the drive work in a USB2 slot?

I have a USB3 MB but have no USB3 device to try to see if Ubuntu 10.10 works with it. I would think that it does. You are using 10.10, and not 10.04?

Oh yeah, thing works perfectly in a USB2 port. It starts the errors on a USB3 port even without a drive in the dock! 

This is the only USB3 capable machine I have, and the only USB3 device... I even flashed the BIOS to the latest beta version which "increases USB3 support" to no avail. I'm considering dropping a temporary drive in there and booting Windows 7 just to see if it works. Course I don't know where the equivalent logs would be...

---

### Post by fjgaude on 2011-02-03
I'm using Ubuntu 10.10 and my logs don't show anything unusual with the USB3 ports. I have the Gigabyte GA-H55N-USB3 motherboard. One of these days I'll get a USB3 device to see if all is okay.

Let us know what you find with your situation.

---

