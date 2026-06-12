---
title: "Third USB 3 external drive not being mouned (memory/kernal issue)  on 16.10?"
date: 2016-12-01
forum: Hardware
---

### Post by zeus.jay on 2016-12-01
Hi Everyone I find myself in an odd situation using 16.10

When connecting USB drives, either via the usb port or via a USB 3 hub. I find I can only connect two drives, They get detected perfectly and auto mounted fine.

However when connecting a third drive nothing happens.

This is my output of dmesg. I've searched for errors online but nothing so far. The closest I found was this

[https://bugzilla.kernel.org/show_bug.cgi?id=115361](https://bugzilla.kernel.org/show_bug.cgi?id=115361)

but this was for a 4.6 RC Kernal

 ```
   [  233.705030] usb 4-2.1.4: new SuperSpeed USB device number 7 using xhci_hcd
    [  233.725706] usb 4-2.1.4: New USB device found, idVendor=0bc2, idProduct=3322
    [  233.725707] usb 4-2.1.4: New USB device strings: Mfr=2, Product=3, SerialNumber=1
    [  233.725708] usb 4-2.1.4: Product: Expansion Desk
    [  233.725709] usb 4-2.1.4: Manufacturer: Seagate
    [  233.725710] usb 4-2.1.4: SerialNumber: NA8ELXQN
    [  233.729792] kworker/1:3: page allocation failure: order:0, mode:0x2604001(GFP_NOIO|GFP_DMA|__GFP_COMP|__GFP_NOTRACK)
    [  233.729794] CPU: 1 PID: 213 Comm: kworker/1:3 Tainted: P           OE   4.8.0-28-generic #30-Ubuntu
    [  233.729795] Hardware name: LENOVO 2349SVL/2349SVL, BIOS G1ETB1WW (2.71 ) 08/08/2016
    [  233.729799] Workqueue: usb_hub_wq hub_event
    [  233.729801]  0000000000000286 0000000018bdd6b7 ffff8ab4e033b150 ffffffff95c2fae2
    [  233.729803]  0000000000000000 0000000000000000 ffff8ab4e033b1e0 ffffffff959aa3f1
    [  233.729804]  02604001959bbb59 0000000000000000 0000000000000040 0000000000000012
    [  233.729806] Call Trace:
    [  233.729810]  [<ffffffff95c2fae2>] dump_stack+0x63/0x81
    [  233.729811]  [<ffffffff959aa3f1>] warn_alloc_failed+0x101/0x160
    [  233.729813]  [<ffffffff95c45af8>] ? find_next_bit+0x18/0x20
    [  233.729814]  [<ffffffff959aa6d1>] __alloc_pages_slowpath+0x201/0xa60
    [  233.729816]  [<ffffffff959ab1e5>] __alloc_pages_nodemask+0x2b5/0x300
    [  233.729818]  [<ffffffff959fec25>] alloc_pages_current+0x95/0x140
    [  233.729819]  [<ffffffff95a08699>] new_slab+0x419/0x6e0
    [  233.729820]  [<ffffffff95a0a210>] ___slab_alloc+0x3a0/0x4b0
    [  233.729822]  [<ffffffff95eaf1db>] ? xhci_segment_alloc.isra.25+0xfb/0x140
    [  233.729824]  [<ffffffff95c3485f>] ? radix_tree_node_alloc+0x4f/0x90
    [  233.729825]  [<ffffffff95a0a340>] __slab_alloc+0x20/0x40
    [  233.729826]  [<ffffffff95a0bdf2>] __kmalloc+0x182/0x1e0
    [  233.729827]  [<ffffffff95eaf1db>] ? xhci_segment_alloc.isra.25+0xfb/0x140
    [  233.729829]  [<ffffffff95eaf1db>] xhci_segment_alloc.isra.25+0xfb/0x140
    [  233.729830]  [<ffffffff95eaf263>] xhci_alloc_segments_for_ring+0x43/0x100
    [  233.729832]  [<ffffffff95eaf3de>] xhci_ring_alloc.constprop.32+0xbe/0x140
    [  233.729833]  [<ffffffff95eb0a9f>] xhci_alloc_stream_info+0x1df/0x3e0
    [  233.729835]  [<ffffffff95eb0820>] ? xhci_alloc_command+0x100/0x140
    [  233.729836]  [<ffffffff95eac0e7>] xhci_alloc_streams+0x447/0x840
    [  233.729837]  [<ffffffff95eabca0>] ? xhci_check_bandwidth+0x370/0x370
    [  233.729838]  [<ffffffff95e66d27>] usb_alloc_streams+0xb7/0x110
    [  233.729842]  [<ffffffffc183a918>] uas_configure_endpoints+0x148/0x170 [uas]
    [  233.729844]  [<ffffffffc183b455>] uas_probe+0x3a5/0x550 [uas]
    [  233.729846]  [<ffffffff95e70439>] usb_probe_interface+0x159/0x2d0
    [  233.729848]  [<ffffffff95d9dfb3>] driver_probe_device+0x223/0x430
    [  233.729849]  [<ffffffff95d9e33c>] __device_attach_driver+0x8c/0x100
    [  233.729850]  [<ffffffff95d9e2b0>] ? __driver_attach+0xf0/0xf0
    [  233.729851]  [<ffffffff95d9bb67>] bus_for_each_drv+0x67/0xb0
    [  233.729852]  [<ffffffff95d9dc1d>] __device_attach+0xdd/0x160
    [  233.729854]  [<ffffffff95d9e3f3>] device_initial_probe+0x13/0x20
    [  233.729855]  [<ffffffff95d9cdd2>] bus_probe_device+0x92/0xa0
    [  233.729855]  [<ffffffff95d9a9d4>] device_add+0x494/0x660
    [  233.729856]  [<ffffffff95e5fd7c>] ? usb_enable_lpm+0xdc/0x100
    [  233.729858]  [<ffffffff95e6e37c>] usb_set_configuration+0x5ec/0x930
    [  233.729860]  [<ffffffff95e7954e>] generic_probe+0x2e/0x80
    [  233.729861]  [<ffffffff95e7029e>] usb_probe_device+0x2e/0x70
    [  233.729862]  [<ffffffff95d9dfb3>] driver_probe_device+0x223/0x430
    [  233.729863]  [<ffffffff95d9e33c>] __device_attach_driver+0x8c/0x100
    [  233.729864]  [<ffffffff95d9e2b0>] ? __driver_attach+0xf0/0xf0
    [  233.729865]  [<ffffffff95d9bb67>] bus_for_each_drv+0x67/0xb0
    [  233.729866]  [<ffffffff95d9dc1d>] __device_attach+0xdd/0x160
    [  233.729867]  [<ffffffff95d9e3f3>] device_initial_probe+0x13/0x20
    [  233.729868]  [<ffffffff95d9cdd2>] bus_probe_device+0x92/0xa0
    [  233.729869]  [<ffffffff95d9a9d4>] device_add+0x494/0x660
    [  233.729871]  [<ffffffff95d64e00>] ? perf_trace_urandom_read+0xb0/0x100
    [  233.729872]  [<ffffffff95e63465>] usb_new_device+0x275/0x490
    [  233.729873]  [<ffffffff95e64a3e>] hub_port_connect+0x50e/0x9d0
    [  233.729874]  [<ffffffff95e65858>] hub_event+0x958/0xb10
    [  233.729876]  [<ffffffff958b3ff9>] ? sched_clock_cpu+0x99/0xb0
    [  233.729877]  [<ffffffff958bcec3>] ? put_prev_entity+0x33/0x3e0
    [  233.729879]  [<ffffffff9589d85c>] process_one_work+0x1fc/0x4b0   
    [  233.729880]  [<ffffffff9589db5b>] worker_thread+0x4b/0x500
    [  233.729881]  [<ffffffff9589db10>] ? process_one_work+0x4b0/0x4b0
    [  233.729882]  [<ffffffff9589db10>] ? process_one_work+0x4b0/0x4b0
    [  233.729883]  [<ffffffff958a3e58>] kthread+0xd8/0xf0
    [  233.729886]  [<ffffffff9609a25f>] ret_from_fork+0x1f/0x40
    [  233.729887]  [<ffffffff958a3d80>] ? kthread_create_on_node+0x1e0/0x1e0
    [  233.729888] Mem-Info:
    [  233.729890] active_anon:315540 inactive_anon:56656 isolated_anon:0
                active_file:156526 inactive_file:175127 isolated_file:0
                unevictable:16 dirty:527 writeback:0 unstable:0
                slab_reclaimable:57963 slab_unreclaimable:19955
                mapped:99479 shmem:14573 pagetables:10274 bounce:0
                free:3207710 free_pcp:671 free_cma:0
    [  233.729893] Node 0 active_anon:1262160kB inactive_anon:226624kB active_file:626104kB inactive_file:700508kB unevictable:64kB isolated(anon):0kB isolated(file):0kB mapped:397916kB dirty:2108kB writeback:0kB shmem:0kB shmem_thp: 0kB shmem_pmdmapped: 270336kB anon_thp: 58292kB writeback_tmp:0kB unstable:0kB pages_scanned:0 all_unreclaimable? no
    [  233.729894] Node 0 DMA free:64kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB writepending:0kB present:15984kB managed:15900kB mlocked:0kB slab_reclaimable:0kB slab_unreclaimable:15836kB kernel_stack:0kB pagetables:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB
    [  233.729896] lowmem_reserve[]: 0 2670 15684 15684 15684
    [  233.729898] Node 0 DMA32 free:2779760kB min:11492kB low:14364kB high:17236kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB writepending:0kB present:2846280kB managed:2780712kB mlocked:0kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:0kB bounce:0kB free_pcp:916kB local_pcp:0kB free_cma:0kB
    [  233.729900] lowmem_reserve[]: 0 0 13013 13013 13013
    [  233.729902] Node 0 Normal free:10051016kB min:56020kB low:70024kB high:84028kB active_anon:1262160kB inactive_anon:226624kB active_file:626104kB inactive_file:700508kB unevictable:64kB writepending:2108kB present:13604864kB managed:13329440kB mlocked:64kB slab_reclaimable:231852kB slab_unreclaimable:63984kB kernel_stack:11472kB pagetables:41096kB bounce:0kB free_pcp:1768kB local_pcp:520kB free_cma:0kB
    [  233.729904] lowmem_reserve[]: 0 0 0 0 0
    [  233.729906] Node 0 DMA: 0*4kB 0*8kB 0*16kB 0*32kB 1*64kB (U) 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 64kB
    [  233.729911] Node 0 DMA32: 2*4kB (M) 3*8kB (UM) 1*16kB (M) 2*32kB (M) 2*64kB (M) 1*128kB (M) 3*256kB (UM) 3*512kB (UM) 4*1024kB (UM) 4*2048kB (UM) 675*4096kB (M) = 2779760kB
    [  233.729917] Node 0 Normal: 70*4kB (UM) 80*8kB (UM) 103*16kB (UM) 66*32kB (UM) 43*64kB (UM) 17*128kB (UME) 52*256kB (UME) 46*512kB (UME) 30*1024kB (U) 22*2048kB (UM) 2424*4096kB (UM) = 10050952kB
    [  233.729925] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
    [  233.729925] 346224 total pagecache pages
    [  233.729926] 0 pages in swap cache 
    [  233.729927] Swap cache stats: add 0, delete 0, find 0/0
    [  233.729927] Free swap  = 8388604kB
    [  233.729927] Total swap = 8388604kB
    [  233.729928] 4116782 pages RAM
    [  233.729928] 0 pages HighMem/MovableOnly
    [  233.729928] 85269 pages reserved
    [  233.729929] 0 pages cma reserved
    [  233.729929] 0 pages hwpoisoned
    [  233.729931] SLUB: Unable to allocate memory on node -1, gfp=0x2408001(GFP_NOIO|GFP_DMA|__GFP_ZERO)
    [  233.729931]   cache: dma-kmalloc-1024, object size: 1024, buffer size: 1024, default order: 3, min order: 0
    [  233.729932]   node 0: slabs: 484, objs: 15488, free: 0
    [  233.730768] uas: probe of 4-2.1.4:1.0 failed with error -12
```

---

### Post by zeus.jay on 2016-12-03
Mmm Seems it might be a known Kernel bug..

[https://bugzilla.kernel.org/show_bug.cgi?id=177551](https://bugzilla.kernel.org/show_bug.cgi?id=177551)

---

