---
title: "USB flash drive cannot be mount"
date: 2012-05-22
forum: Hardware
---

### Post by anatolik on 2012-05-22
Hi,

I bought a no-name USB flash drive (64Gb) and trying to use it. It works fine on macbookpro - I was able to format it and cop a few files there.

I try to use it on my Ubuntu 12.04
> $ uname -a
Linux anatol 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

all packages up-to-date as of now.

It seems that there is a deadlock in kernel that prevents using my flash drive. How to resolve it? Is it a known issue? Do you need more info from me?

Here is a log from dmesg:

> [  175.076020] usb 1-8: new high-speed USB device number 5 using ehci_hcd
[  175.345895] Initializing USB Mass Storage driver...
[  175.346032] scsi8 : usb-storage 1-8:1.0
[  175.346123] usbcore: registered new interface driver usb-storage
[  175.346125] USB Mass Storage support registered.
[  175.355055] usbcore: registered new interface driver uas
[  176.345935] scsi 8:0:0:0: Direct-Access     Generic  Flash Disk       8.00 PQ: 0 ANSI: 2
[  176.346618] sd 8:0:0:0: Attached scsi generic sg2 type 0
[  176.349047] sd 8:0:0:0: [sdc] 131072000 512-byte logical blocks: (67.1 GB/62.5 GiB)
[  176.349541] sd 8:0:0:0: [sdc] Write Protect is off
[  176.349544] sd 8:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  176.350041] sd 8:0:0:0: [sdc] No Caching mode page present
[  176.350044] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  176.352665] sd 8:0:0:0: [sdc] No Caching mode page present
[  176.352668] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  206.992021] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  237.968034] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  269.008020] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  299.984043] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  330.960021] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  360.704025] INFO: task kworker/u:8:65 blocked for more than 120 seconds.
[  360.704030] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  360.704034] kworker/u:8     D ffffffff81806240     0    65      2 0x00000000
[  360.704039]  ffff880421521830 0000000000000046 0000000000000000 00000000e61fa32f
[  360.704045]  ffff880421521fd8 ffff880421521fd8 ffff880421521fd8 0000000000013780
[  360.704049]  ffff8804255e96f0 ffff880421518000 ffff880421521810 ffff88043fc94040
[  360.704054] Call Trace:
[  360.704066]  [<ffffffff811171b0>] ? __lock_page+0x70/0x70
[  360.704071]  [<ffffffff8165a88f>] schedule+0x3f/0x60
[  360.704074]  [<ffffffff8165a93f>] io_schedule+0x8f/0xd0
[  360.704077]  [<ffffffff811171be>] sleep_on_page+0xe/0x20
[  360.704080]  [<ffffffff8165b00a>] __wait_on_bit_lock+0x5a/0xc0
[  360.704084]  [<ffffffff811171a7>] __lock_page+0x67/0x70
[  360.704088]  [<ffffffff8108b030>] ? autoremove_wake_function+0x40/0x40
[  360.704092]  [<ffffffff81118270>] do_read_cache_page+0x160/0x180
[  360.704098]  [<ffffffff81157ad3>] ? alloc_pages_current+0xa3/0x110
[  360.704103]  [<ffffffff811af3a0>] ? blkdev_write_begin+0x30/0x30
[  360.704107]  [<ffffffff811182d9>] read_cache_page_async+0x19/0x20
[  360.704110]  [<ffffffff811182ee>] read_cache_page+0xe/0x20
[  360.704115]  [<ffffffff811e3b3d>] read_dev_sector+0x2d/0x90
[  360.704119]  [<ffffffff811ea23c>] read_lba+0xbc/0x120
[  360.704122]  [<ffffffff811ea6fd>] is_gpt_valid+0x8d/0x210
[  360.704125]  [<ffffffff811ea9f8>] find_valid_gpt+0x178/0x2a0
[  360.704129]  [<ffffffff811af3a0>] ? blkdev_write_begin+0x30/0x30
[  360.704132]  [<ffffffff811eab20>] ? find_valid_gpt+0x2a0/0x2a0
[  360.704135]  [<ffffffff811eaba2>] efi_partition+0x82/0x3b0
[  360.704139]  [<ffffffff811e4d87>] ? adfspart_check_ICS+0xb7/0x2d0
[  360.704144]  [<ffffffff81316614>] ? snprintf+0x34/0x40
[  360.704147]  [<ffffffff811eab20>] ? find_valid_gpt+0x2a0/0x2a0
[  360.704151]  [<ffffffff811e42b8>] check_partition+0xf8/0x200
[  360.704155]  [<ffffffff811e4a27>] rescan_partitions+0xb7/0x2b0
[  360.704158]  [<ffffffff811b04bb>] __blkdev_get+0x37b/0x460
[  360.704162]  [<ffffffff8108abc7>] ? bit_waitqueue+0x17/0xc0
[  360.704166]  [<ffffffff810922f0>] ? async_schedule+0x20/0x20
[  360.704169]  [<ffffffff811b05fe>] blkdev_get+0x5e/0x1e0
[  360.704172]  [<ffffffff810922f0>] ? async_schedule+0x20/0x20
[  360.704177]  [<ffffffff812fb152>] register_disk+0x162/0x180
[  360.704180]  [<ffffffff810922f0>] ? async_schedule+0x20/0x20
[  360.704184]  [<ffffffff812fb224>] add_disk+0xb4/0x230
[  360.704189]  [<ffffffff814458bb>] sd_probe_async+0x11b/0x1d0
[  360.704192]  [<ffffffff8109236f>] async_run_entry_fn+0x7f/0x180
[  360.704197]  [<ffffffff81084f5a>] process_one_work+0x11a/0x480
[  360.704201]  [<ffffffff81085d04>] worker_thread+0x164/0x370
[  360.704205]  [<ffffffff81085ba0>] ? manage_workers.isra.29+0x130/0x130
[  360.704208]  [<ffffffff8108a55c>] kthread+0x8c/0xa0
[  360.704213]  [<ffffffff81666ef4>] kernel_thread_helper+0x4/0x10
[  360.704216]  [<ffffffff8108a4d0>] ? flush_kthread_worker+0xa0/0xa0
[  360.704219]  [<ffffffff81666ef0>] ? gs_change+0x13/0x13
[  361.936018] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  362.156146] sd 8:0:0:0: [sdc] Media Changed
[  362.156149] sd 8:0:0:0: [sdc]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_SENSE
[  362.156154] sd 8:0:0:0: [sdc]  Sense Key : Unit Attention [current] 
[  362.156159] Info fld=0x0
[  362.156161] sd 8:0:0:0: [sdc]  Add. Sense: Not ready to ready change, medium may have changed
[  362.156167] sd 8:0:0:0: [sdc] CDB: Read(10): 28 00 07 cf ff f8 00 00 01 00
[  362.156177] end_request: I/O error, dev sdc, sector 131071992
[  362.156181] quiet_error: 27 callbacks suppressed
[  362.156184] Buffer I/O error on device sdc, logical block 16383999
[  362.156220] Alternate GPT is invalid, using primary GPT.
[  362.156240]  sdc: sdc1 sdc2
[  362.160271] sd 8:0:0:0: [sdc] No Caching mode page present
[  362.160274] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  362.160278] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[  362.161015] sd 8:0:0:0: [sdc] No Caching mode page present
[  362.161018] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  362.163265] sd 8:0:0:0: [sdc] No Caching mode page present
[  362.163269] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  392.912018] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  424.016016] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  454.992017] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  485.968018] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  516.944018] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  547.920019] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  548.140082] sd 8:0:0:0: [sdc] Media Changed
[  548.140085] sd 8:0:0:0: [sdc]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_SENSE
[  548.140090] sd 8:0:0:0: [sdc]  Sense Key : Unit Attention [current] 
[  548.140096] Info fld=0x0
[  548.140097] sd 8:0:0:0: [sdc]  Add. Sense: Not ready to ready change, medium may have changed
[  548.140104] sd 8:0:0:0: [sdc] CDB: Read(10): 28 00 07 cf ff f8 00 00 01 00
[  548.140114] end_request: I/O error, dev sdc, sector 131071992
[  548.140118] Buffer I/O error on device sdc, logical block 16383999
[  548.140163] Alternate GPT is invalid, using primary GPT.
[  548.140182]  sdc: sdc1 sdc2
[  548.142957] sd 8:0:0:0: [sdc] No Caching mode page present
[  548.142962] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  548.145204] sd 8:0:0:0: [sdc] No Caching mode page present
[  548.145208] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  578.896016] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  610.000018] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  640.976019] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  671.952019] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  702.928019] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  720.704067] INFO: task lshw:2544 blocked for more than 120 seconds.
[  720.704072] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  720.704075] lshw            D ffffffff81806240     0  2544   2543 0x00000000
[  720.704085]  ffff8803b3129dd8 0000000000000082 ffff8803b3129f28 ffff880423cff000
[  720.704090]  ffff8803b3129fd8 ffff8803b3129fd8 ffff8803b3129fd8 0000000000013780
[  720.704093]  ffffffff81c0d020 ffff8803b08096f0 ffff88042157f820 ffff880422912718
[  720.704097] Call Trace:
[  720.704106]  [<ffffffff8165a88f>] schedule+0x3f/0x60
[  720.704109]  [<ffffffff8165b697>] __mutex_lock_slowpath+0xd7/0x150
[  720.704112]  [<ffffffff8165b2aa>] mutex_lock+0x2a/0x50
[  720.704116]  [<ffffffff811affdf>] blkdev_put+0x2f/0x160
[  720.704119]  [<ffffffff811b0135>] blkdev_close+0x25/0x30
[  720.704123]  [<ffffffff8117910e>] __fput+0xbe/0x210
[  720.704125]  [<ffffffff81179285>] fput+0x25/0x30
[  720.704130]  [<ffffffff81175ea6>] filp_close+0x66/0x90
[  720.704132]  [<ffffffff81175f82>] sys_close+0xb2/0x120
[  720.704136]  [<ffffffff81664d82>] system_call_fastpath+0x16/0x1b
[  720.704139] INFO: task blkid:2763 blocked for more than 120 seconds.
[  720.704140] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  720.704142] blkid           D ffffffff81806240     0  2763   2502 0x00000004
[  720.704146]  ffff8804255a5798 0000000000000086 0000000000000000 000000001e20a096
[  720.704149]  ffff8804255a5fd8 ffff8804255a5fd8 ffff8804255a5fd8 0000000000013780
[  720.704153]  ffff8804255d16f0 ffff8804049d96f0 ffff8804255a5778 ffff88043fc54040
[  720.704157] Call Trace:
[  720.704161]  [<ffffffff811171b0>] ? __lock_page+0x70/0x70
[  720.704164]  [<ffffffff8165a88f>] schedule+0x3f/0x60
[  720.704166]  [<ffffffff8165a93f>] io_schedule+0x8f/0xd0
[  720.704169]  [<ffffffff811171be>] sleep_on_page+0xe/0x20
[  720.704171]  [<ffffffff8165b00a>] __wait_on_bit_lock+0x5a/0xc0
[  720.704174]  [<ffffffff811171a7>] __lock_page+0x67/0x70
[  720.704178]  [<ffffffff8108b030>] ? autoremove_wake_function+0x40/0x40
[  720.704181]  [<ffffffff81118270>] do_read_cache_page+0x160/0x180
[  720.704185]  [<ffffffff81157ad3>] ? alloc_pages_current+0xa3/0x110
[  720.704188]  [<ffffffff811af3a0>] ? blkdev_write_begin+0x30/0x30
[  720.704191]  [<ffffffff811182d9>] read_cache_page_async+0x19/0x20
[  720.704194]  [<ffffffff811182ee>] read_cache_page+0xe/0x20
[  720.704199]  [<ffffffff811e3b3d>] read_dev_sector+0x2d/0x90
[  720.704201]  [<ffffffff811ea23c>] read_lba+0xbc/0x120
[  720.704204]  [<ffffffff811ea6fd>] is_gpt_valid+0x8d/0x210
[  720.704206]  [<ffffffff811ea9f8>] find_valid_gpt+0x178/0x2a0
[  720.704209]  [<ffffffff811af3a0>] ? blkdev_write_begin+0x30/0x30
[  720.704212]  [<ffffffff811eab20>] ? find_valid_gpt+0x2a0/0x2a0
[  720.704214]  [<ffffffff811eaba2>] efi_partition+0x82/0x3b0
[  720.704217]  [<ffffffff811e4d87>] ? adfspart_check_ICS+0xb7/0x2d0
[  720.704222]  [<ffffffff81316614>] ? snprintf+0x34/0x40
[  720.704225]  [<ffffffff811eab20>] ? find_valid_gpt+0x2a0/0x2a0
[  720.704227]  [<ffffffff811e42b8>] check_partition+0xf8/0x200
[  720.704230]  [<ffffffff811e4a27>] rescan_partitions+0xb7/0x2b0
[  720.704233]  [<ffffffff811b055c>] __blkdev_get+0x41c/0x460
[  720.704236]  [<ffffffff811b05fe>] blkdev_get+0x5e/0x1e0
[  720.704239]  [<ffffffff811b07dd>] blkdev_open+0x5d/0x80
[  720.704242]  [<ffffffff81175a30>] __dentry_open+0x290/0x360
[  720.704245]  [<ffffffff811b0780>] ? blkdev_get+0x1e0/0x1e0
[  720.704248]  [<ffffffff8129c8dc>] ? security_inode_permission+0x1c/0x30
[  720.704252]  [<ffffffff8118367a>] ? inode_permission+0x4a/0x110
[  720.704254]  [<ffffffff811760ad>] vfs_open+0x3d/0x40
[  720.704257]  [<ffffffff81176f80>] nameidata_to_filp+0x40/0x50
[  720.704259]  [<ffffffff81185eb8>] do_last+0x3f8/0x730
[  720.704262]  [<ffffffff81187591>] path_openat+0xd1/0x3f0
[  720.704265]  [<ffffffff8113b079>] ? __pte_alloc+0xa9/0x160
[  720.704268]  [<ffffffff811879d2>] do_filp_open+0x42/0xa0
[  720.704272]  [<ffffffff81318e11>] ? strncpy_from_user+0x31/0x40
[  720.704274]  [<ffffffff81182d1a>] ? do_getname+0x10a/0x180
[  720.704277]  [<ffffffff8165c79e>] ? _raw_spin_lock+0xe/0x20
[  720.704280]  [<ffffffff81194c77>] ? alloc_fd+0xf7/0x150
[  720.704283]  [<ffffffff8117707d>] do_sys_open+0xed/0x220
[  720.704285]  [<ffffffff811771d0>] sys_open+0x20/0x30
[  720.704288]  [<ffffffff81664d82>] system_call_fastpath+0x16/0x1b
[  733.968018] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  734.188133] sd 8:0:0:0: [sdc] Media Changed
[  734.188136] sd 8:0:0:0: [sdc]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_SENSE
[  734.188141] sd 8:0:0:0: [sdc]  Sense Key : Unit Attention [current] 
[  734.188146] Info fld=0x0
[  734.188148] sd 8:0:0:0: [sdc]  Add. Sense: Not ready to ready change, medium may have changed
[  734.188154] sd 8:0:0:0: [sdc] CDB: Read(10): 28 00 07 cf ff f8 00 00 01 00
[  734.188164] end_request: I/O error, dev sdc, sector 131071992
[  734.188169] Buffer I/O error on device sdc, logical block 16383999
[  734.188210] Alternate GPT is invalid, using primary GPT.
[  734.188234]  sdc: sdc1 sdc2
[  734.193259] sd 8:0:0:0: [sdc] No Caching mode page present
[  734.193264] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  734.195507] sd 8:0:0:0: [sdc] No Caching mode page present
[  734.195511] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  764.944024] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  795.984024] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  826.960034] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  857.936028] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  888.912021] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  920.016022] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  920.236066] sd 8:0:0:0: [sdc] Media Changed
[  920.236070] sd 8:0:0:0: [sdc]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_SENSE
[  920.236074] sd 8:0:0:0: [sdc]  Sense Key : Unit Attention [current] 
[  920.236079] Info fld=0x0
[  920.236081] sd 8:0:0:0: [sdc]  Add. Sense: Not ready to ready change, medium may have changed
[  920.236088] sd 8:0:0:0: [sdc] CDB: Read(10): 28 00 07 cf ff f8 00 00 01 00
[  920.236097] end_request: I/O error, dev sdc, sector 131071992
[  920.236103] Buffer I/O error on device sdc, logical block 16383999
[  920.236177] Alternate GPT is invalid, using primary GPT.
[  920.236207]  sdc: sdc1 sdc2
[  920.238933] sd 8:0:0:0: [sdc] No Caching mode page present
[  920.238936] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  920.241182] sd 8:0:0:0: [sdc] No Caching mode page present
[  920.241186] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[  950.992020] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[  981.968025] usb 1-8: reset high-speed USB device number 5 using ehci_hcd
[ 1012.944022] usb 1-8: reset high-speed USB device number 5 using ehci_hcd

---

### Post by anatolik on 2012-05-30
It seems that this was a hardware problem. I returned the USB flash drive and bought another one (SanDisk Cruzer). The new drive works without any issues on my Linux box.

---

