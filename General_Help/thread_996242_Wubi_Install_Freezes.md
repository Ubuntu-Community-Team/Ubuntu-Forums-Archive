---
title: "Wubi Install Freezes"
date: 2008-11-28
forum: General Help
---

### Post by rexeasley on 2008-11-28
My installation of Wubi freezes fairly frequently. It's usually when no one is using the computer after it has been running for about a day. The relevant portion of the kernel log follows:
```
Nov 28 06:49:13 rex-desktop kernel: [30801.009744] audit(1227872953.959:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=18927 profile="/usr/sbin/cupsd" namespace="default"
Nov 28 06:51:48 rex-desktop kernel: [30932.175495] npviewer.bin[12760]: segfault at f65b884c rip f6def2eb rsp f1b2ff50 error 4
Nov 28 14:39:32 rex-desktop kernel: [45285.885639] mount.ntfs invoked oom-killer: gfp_mask=0x201d0, order=0, oomkilladj=0
Nov 28 14:44:51 rex-desktop kernel: [45285.885652] Pid: 2683, comm: mount.ntfs Tainted: P        2.6.24-21-generic #1
Nov 28 14:45:46 rex-desktop kernel: [45285.885656] 
Nov 28 14:48:48 rex-desktop kernel: [45285.885657] Call Trace:
Nov 28 14:57:10 rex-desktop kernel: [45285.885726]  [oom_kill_process+0xf6/0x110] oom_kill_process+0xf6/0x110
Nov 28 14:58:50 rex-desktop kernel: [45285.885736]  [out_of_memory+0x15e/0x270] out_of_memory+0x15e/0x270
Nov 28 15:01:48 rex-desktop kernel: [45285.885746]  [__alloc_pages+0x3b9/0x3f0] __alloc_pages+0x3b9/0x3f0
Nov 28 15:05:26 rex-desktop kernel: [45285.885760]  [__do_page_cache_readahead+0xe0/0x210] __do_page_cache_readahead+0xe0/0x210
Nov 28 15:08:48 rex-desktop kernel: [45285.885773]  [ondemand_readahead+0x9c/0x1c0] ondemand_readahead+0x9c/0x1c0
Nov 28 15:13:02 rex-desktop kernel: [45285.885781]  [do_generic_mapping_read+0x235/0x3e0] do_generic_mapping_read+0x235/0x3e0
Nov 28 15:17:38 rex-desktop kernel: [45285.885785]  [file_read_actor+0x0/0x160] file_read_actor+0x0/0x160
Nov 28 15:21:10 rex-desktop kernel: [45285.885796]  [nfs:generic_file_aio_read+0xff/0x1b0] generic_file_aio_read+0xff/0x1b0
Nov 28 15:26:12 rex-desktop kernel: [45285.885812]  [ext3:do_sync_read+0xd9/0xbb0] do_sync_read+0xd9/0x120
Nov 28 15:30:19 rex-desktop kernel: [45285.885824]  [<ffffffff80253bf0>] autoremove_wake_function+0x0/0x30
Nov 28 15:34:29 rex-desktop kernel: [45285.885830]  [do_readv_writev+0x186/0x230] do_readv_writev+0x186/0x230
Nov 28 15:36:52 rex-desktop kernel: [45285.885842]  [thread_return+0x3a/0x57b] thread_return+0x3a/0x57b
Nov 28 15:39:13 rex-desktop kernel: [45285.885852]  [vfs_read+0xed/0x190] vfs_read+0xed/0x190
Nov 28 15:41:46 rex-desktop kernel: [45285.885858]  [sys_pread64+0x84/0xa0] sys_pread64+0x84/0xa0
Nov 28 15:43:42 rex-desktop kernel: [45285.885866]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Nov 28 15:47:33 rex-desktop kernel: [45285.885877] 
Nov 28 15:48:21 rex-desktop kernel: [45285.885878] Mem-info:
Nov 28 15:48:22 rex-desktop kernel: [45285.885880] Node 0 DMA per-cpu:
Nov 28 15:48:22 rex-desktop kernel: [45285.885883] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:22 rex-desktop kernel: [45285.885886] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:22 rex-desktop kernel: [45285.885888] Node 0 DMA32 per-cpu:
Nov 28 15:48:22 rex-desktop kernel: [45285.885890] CPU    0: Hot: hi:  186, btch:  31 usd: 182   Cold: hi:   62, btch:  15 usd:  23
Nov 28 15:48:22 rex-desktop kernel: [45285.885893] CPU    1: Hot: hi:  186, btch:  31 usd: 170   Cold: hi:   62, btch:  15 usd:  18
Nov 28 15:48:22 rex-desktop kernel: [45285.885896] Active:112727 inactive:105685 dirty:0 writeback:0 unstable:0
Nov 28 15:48:22 rex-desktop kernel: [45285.885897]  free:1430 slab:4843 mapped:3170 pagetables:4797 bounce:0
Nov 28 15:48:22 rex-desktop kernel: [45285.885899] Node 0 DMA free:1876kB min:44kB low:52kB high:64kB active:0kB inactive:0kB present:10896kB pages_scanned:0 all_unreclaimable? yes
Nov 28 15:48:22 rex-desktop kernel: [45285.885903] lowmem_reserve[]: 0 931 931 931
Nov 28 15:48:22 rex-desktop kernel: [45285.885906] Node 0 DMA32 free:3844kB min:3876kB low:4844kB high:5812kB active:450908kB inactive:422740kB present:953380kB pages_scanned:1852035 all_unreclaimable? yes
Nov 28 15:48:22 rex-desktop kernel: [45285.885910] lowmem_reserve[]: 0 0 0 0

Nov 28 15:48:22 rex-desktop kernel: [45285.885912] Node 0 DMA: 1*4kB 4*8kB 3*16kB 2*32kB 3*64kB 4*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1876kB
Nov 28 15:48:22 rex-desktop kernel: [45285.885919] Node 0 DMA32: 31*4kB 1*8kB 1*16kB 2*32kB 0*64kB 0*128kB 0*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 3796kB
Nov 28 15:48:22 rex-desktop kernel: [45285.885926] Swap cache: add 535092, delete 535092, find 84530/110955, race 0+0
Nov 28 15:48:22 rex-desktop kernel: [45285.885928] Free swap  = 0kB
Nov 28 15:48:22 rex-desktop kernel: [45285.885929] Total swap = 976552kB
Nov 28 15:48:22 rex-desktop kernel: [45285.885930] Free swap:            0kB
Nov 28 15:48:22 rex-desktop kernel: [45285.893829] 245744 pages of RAM
Nov 28 15:48:22 rex-desktop kernel: [45285.893832] 8888 reserved pages
Nov 28 15:48:22 rex-desktop kernel: [45285.893833] 493 pages shared
Nov 28 15:48:22 rex-desktop kernel: [45285.893835] 0 pages swap cached
Nov 28 15:48:22 rex-desktop kernel: [45285.893837] Out of memory: kill process 6085 (x-session-manag) score 183319 or a child
Nov 28 15:48:22 rex-desktop kernel: [45285.893883] Killed process 6215 (seahorse-agent)
Nov 28 15:48:22 rex-desktop kernel: [45947.712924] mount.ntfs invoked oom-killer: gfp_mask=0x201d0, order=0, oomkilladj=0
Nov 28 15:48:22 rex-desktop kernel: [45947.712936] Pid: 2683, comm: mount.ntfs Tainted: P        2.6.24-21-generic #1
Nov 28 15:48:22 rex-desktop kernel: [45947.712939] 
Nov 28 15:48:22 rex-desktop kernel: [45947.712939] Call Trace:
Nov 28 15:48:23 rex-desktop kernel: [45947.713005]  [oom_kill_process+0xf6/0x110] oom_kill_process+0xf6/0x110
Nov 28 15:48:23 rex-desktop kernel: [45947.713014]  [out_of_memory+0x15e/0x270] out_of_memory+0x15e/0x270
Nov 28 15:48:23 rex-desktop kernel: [45947.713024]  [__alloc_pages+0x3b9/0x3f0] __alloc_pages+0x3b9/0x3f0
Nov 28 15:48:23 rex-desktop kernel: [45947.713038]  [__do_page_cache_readahead+0xe0/0x210] __do_page_cache_readahead+0xe0/0x210
Nov 28 15:48:23 rex-desktop kernel: [45947.713051]  [ondemand_readahead+0x9c/0x1c0] ondemand_readahead+0x9c/0x1c0
Nov 28 15:48:23 rex-desktop kernel: [45947.713059]  [do_generic_mapping_read+0x235/0x3e0] do_generic_mapping_read+0x235/0x3e0
Nov 28 15:48:23 rex-desktop kernel: [45947.713063]  [file_read_actor+0x0/0x160] file_read_actor+0x0/0x160
Nov 28 15:48:23 rex-desktop kernel: [45947.713074]  [nfs:generic_file_aio_read+0xff/0x1b0] generic_file_aio_read+0xff/0x1b0
Nov 28 15:48:23 rex-desktop kernel: [45947.713090]  [ext3:do_sync_read+0xd9/0xbb0] do_sync_read+0xd9/0x120
Nov 28 15:48:24 rex-desktop kernel: [45947.713102]  [<ffffffff80253bf0>] autoremove_wake_function+0x0/0x30
Nov 28 15:48:24 rex-desktop kernel: [45947.713108]  [do_readv_writev+0x186/0x230] do_readv_writev+0x186/0x230
Nov 28 15:48:24 rex-desktop kernel: [45947.713120]  [thread_return+0x3a/0x57b] thread_return+0x3a/0x57b
Nov 28 15:48:24 rex-desktop kernel: [45947.713131]  [vfs_read+0xed/0x190] vfs_read+0xed/0x190
Nov 28 15:48:24 rex-desktop kernel: [45947.713137]  [sys_pread64+0x84/0xa0] sys_pread64+0x84/0xa0
Nov 28 15:48:24 rex-desktop kernel: [45947.713145]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Nov 28 15:48:24 rex-desktop kernel: [45947.713156] 
Nov 28 15:48:24 rex-desktop kernel: [45947.713157] Mem-info:
Nov 28 15:48:24 rex-desktop kernel: [45947.713159] Node 0 DMA per-cpu:
Nov 28 15:48:24 rex-desktop kernel: [45947.713162] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:24 rex-desktop kernel: [45947.713165] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:24 rex-desktop kernel: [45947.713166] Node 0 DMA32 per-cpu:
Nov 28 15:48:24 rex-desktop kernel: [45947.713169] CPU    0: Hot: hi:  186, btch:  31 usd: 173   Cold: hi:   62, btch:  15 usd:  18
Nov 28 15:48:24 rex-desktop kernel: [45947.713171] CPU    1: Hot: hi:  186, btch:  31 usd: 152   Cold: hi:   62, btch:  15 usd:  13
Nov 28 15:48:24 rex-desktop kernel: [45947.713175] Active:105567 inactive:112981 dirty:0 writeback:0 unstable:0
Nov 28 15:48:24 rex-desktop kernel: [45947.713176]  free:1435 slab:4837 mapped:3181 pagetables:4694 bounce:0
Nov 28 15:48:24 rex-desktop kernel: [45947.713178] Node 0 DMA free:1876kB min:44kB low:52kB high:64kB active:0kB inactive:0kB present:10896kB pages_scanned:0 all_unreclaimable? yes
Nov 28 15:48:24 rex-desktop kernel: [45947.713182] lowmem_reserve[]: 0 931 931 931
Nov 28 15:48:24 rex-desktop kernel: [45947.713185] Node 0 DMA32 free:3864kB min:3876kB low:4844kB high:5812kB active:422268kB inactive:451924kB present:953380kB pages_scanned:1440351 all_unreclaimable? yes
Nov 28 15:48:24 rex-desktop kernel: [45947.713189] lowmem_reserve[]: 0 0 0 0
Nov 28 15:48:24 rex-desktop kernel: [45947.713191] Node 0 DMA: 1*4kB 4*8kB 3*16kB 2*32kB 3*64kB 4*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1876kB
Nov 28 15:48:24 rex-desktop kernel: [45947.713197] Node 0 DMA32: 34*4kB 1*8kB 1*16kB 2*32kB 0*64kB 0*128kB 0*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 3808kB
Nov 28 15:48:24 rex-desktop kernel: [45947.713205] Swap cache: add 538019, delete 538019, find 84636/111293, race 0+0
Nov 28 15:48:24 rex-desktop kernel: [45947.713206] Free swap  = 0kB
Nov 28 15:48:24 rex-desktop kernel: [45947.713207] Total swap = 976552kB
Nov 28 15:48:24 rex-desktop kernel: [45947.713208] Free swap:            0kB
Nov 28 15:48:24 rex-desktop kernel: [45947.721094] 245744 pages of RAM
Nov 28 15:48:24 rex-desktop kernel: [45947.721097] 8888 reserved pages
Nov 28 15:48:24 rex-desktop kernel: [45947.721098] 754 pages shared
Nov 28 15:48:24 rex-desktop kernel: [45947.721099] 0 pages swap cached
Nov 28 15:48:24 rex-desktop kernel: [45947.721102] Out of memory: kill process 6085 (x-session-manag) score 174361 or a child
Nov 28 15:48:24 rex-desktop kernel: [45947.721147] Killed process 6223 (gnome-settings-)
Nov 28 15:48:24 rex-desktop kernel: [46198.799894] mount.ntfs invoked oom-killer: gfp_mask=0x201d0, order=0, oomkilladj=0
Nov 28 15:48:24 rex-desktop kernel: [46198.799907] Pid: 2683, comm: mount.ntfs Tainted: P        2.6.24-21-generic #1
Nov 28 15:48:24 rex-desktop kernel: [46198.799909] 
Nov 28 15:48:24 rex-desktop kernel: [46198.799910] Call Trace:
Nov 28 15:48:24 rex-desktop kernel: [46198.799974]  [oom_kill_process+0xf6/0x110] oom_kill_process+0xf6/0x110
Nov 28 15:48:24 rex-desktop kernel: [46198.799986]  [out_of_memory+0x15e/0x270] out_of_memory+0x15e/0x270
Nov 28 15:48:24 rex-desktop kernel: [46198.799996]  [__alloc_pages+0x3b9/0x3f0] __alloc_pages+0x3b9/0x3f0
Nov 28 15:48:24 rex-desktop kernel: [46198.800010]  [__do_page_cache_readahead+0xe0/0x210] __do_page_cache_readahead+0xe0/0x210
Nov 28 15:48:24 rex-desktop kernel: [46198.800023]  [ondemand_readahead+0x9c/0x1c0] ondemand_readahead+0x9c/0x1c0
Nov 28 15:48:24 rex-desktop kernel: [46198.800031]  [do_generic_mapping_read+0x235/0x3e0] do_generic_mapping_read+0x235/0x3e0
Nov 28 15:48:24 rex-desktop kernel: [46198.800035]  [file_read_actor+0x0/0x160] file_read_actor+0x0/0x160
Nov 28 15:48:24 rex-desktop kernel: [46198.800046]  [nfs:generic_file_aio_read+0xff/0x1b0] generic_file_aio_read+0xff/0x1b0
Nov 28 15:48:24 rex-desktop kernel: [46198.800062]  [ext3:do_sync_read+0xd9/0xbb0] do_sync_read+0xd9/0x120
Nov 28 15:48:24 rex-desktop kernel: [46198.800074]  [<ffffffff80253bf0>] autoremove_wake_function+0x0/0x30
Nov 28 15:48:24 rex-desktop kernel: [46198.800080]  [do_readv_writev+0x186/0x230] do_readv_writev+0x186/0x230
Nov 28 15:48:24 rex-desktop kernel: [46198.800092]  [thread_return+0x3a/0x57b] thread_return+0x3a/0x57b
Nov 28 15:48:24 rex-desktop kernel: [46198.800102]  [vfs_read+0xed/0x190] vfs_read+0xed/0x190
Nov 28 15:48:24 rex-desktop kernel: [46198.800108]  [sys_pread64+0x84/0xa0] sys_pread64+0x84/0xa0
Nov 28 15:48:24 rex-desktop kernel: [46198.800116]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Nov 28 15:48:24 rex-desktop kernel: [46198.800127] 
Nov 28 15:48:24 rex-desktop kernel: [46198.800129] Mem-info:
Nov 28 15:48:24 rex-desktop kernel: [46198.800130] Node 0 DMA per-cpu:
Nov 28 15:48:24 rex-desktop kernel: [46198.800133] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:24 rex-desktop kernel: [46198.800136] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:24 rex-desktop kernel: [46198.800138] Node 0 DMA32 per-cpu:
Nov 28 15:48:24 rex-desktop kernel: [46198.800140] CPU    0: Hot: hi:  186, btch:  31 usd: 173   Cold: hi:   62, btch:  15 usd:   9
Nov 28 15:48:24 rex-desktop kernel: [46198.800143] CPU    1: Hot: hi:  186, btch:  31 usd: 163   Cold: hi:   62, btch:  15 usd:  29
Nov 28 15:48:24 rex-desktop kernel: [46198.800147] Active:112241 inactive:106359 dirty:0 writeback:0 unstable:0
Nov 28 15:48:24 rex-desktop kernel: [46198.800149]  free:1422 slab:4831 mapped:3170 pagetables:4574 bounce:0
Nov 28 15:48:24 rex-desktop kernel: [46198.800150] Node 0 DMA free:1876kB min:44kB low:52kB high:64kB active:0kB inactive:0kB present:10896kB pages_scanned:0 all_unreclaimable? yes
Nov 28 15:48:24 rex-desktop kernel: [46198.800154] lowmem_reserve[]: 0 931 931 931
Nov 28 15:48:24 rex-desktop kernel: [46198.800157] Node 0 DMA32 free:3812kB min:3876kB low:4844kB high:5812kB active:448964kB inactive:425436kB present:953380kB pages_scanned:1696969 all_unreclaimable? yes
Nov 28 15:48:24 rex-desktop kernel: [46198.800161] lowmem_reserve[]: 0 0 0 0
Nov 28 15:48:24 rex-desktop kernel: [46198.800163] Node 0 DMA: 1*4kB 4*8kB 3*16kB 2*32kB 3*64kB 4*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1876kB
Nov 28 15:48:24 rex-desktop kernel: [46198.800170] Node 0 DMA32: 27*4kB 1*8kB 1*16kB 2*32kB 0*64kB 0*128kB 0*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 3780kB
Nov 28 15:48:24 rex-desktop kernel: [46198.800177] Swap cache: add 546439, delete 546439, find 85103/112557, race 0+0
Nov 28 15:48:24 rex-desktop kernel: [46198.800178] Free swap  = 0kB
Nov 28 15:48:24 rex-desktop kernel: [46198.800179] Total swap = 976552kB
Nov 28 15:48:24 rex-desktop kernel: [46198.800181] Free swap:            0kB
Nov 28 15:48:24 rex-desktop kernel: [46198.808105] 245744 pages of RAM
Nov 28 15:48:24 rex-desktop kernel: [46198.808108] 8888 reserved pages
Nov 28 15:48:24 rex-desktop kernel: [46198.808109] 607 pages shared
Nov 28 15:48:24 rex-desktop kernel: [46198.808110] 0 pages swap cached
Nov 28 15:48:24 rex-desktop kernel: [46198.808113] Out of memory: kill process 6085 (x-session-manag) score 152981 or a child
Nov 28 15:48:24 rex-desktop kernel: [46198.808162] Killed process 6251 (compiz)
Nov 28 15:48:24 rex-desktop kernel: [46198.810310] mount.ntfs invoked oom-killer: gfp_mask=0x201d0, order=0, oomkilladj=0
Nov 28 15:48:24 rex-desktop kernel: [46198.810316] Pid: 2683, comm: mount.ntfs Tainted: P        2.6.24-21-generic #1
Nov 28 15:48:24 rex-desktop kernel: [46198.810319] 
Nov 28 15:48:24 rex-desktop kernel: [46198.810319] Call Trace:
Nov 28 15:48:24 rex-desktop kernel: [46198.810365]  [oom_kill_process+0xf6/0x110] oom_kill_process+0xf6/0x110
Nov 28 15:48:24 rex-desktop kernel: [46198.810373]  [out_of_memory+0x15e/0x270] out_of_memory+0x15e/0x270
Nov 28 15:48:24 rex-desktop kernel: [46198.810383]  [__alloc_pages+0x3b9/0x3f0] __alloc_pages+0x3b9/0x3f0
Nov 28 15:48:24 rex-desktop kernel: [46198.810396]  [__do_page_cache_readahead+0xe0/0x210] __do_page_cache_readahead+0xe0/0x210
Nov 28 15:48:24 rex-desktop kernel: [46198.810410]  [ondemand_readahead+0x9c/0x1c0] ondemand_readahead+0x9c/0x1c0
Nov 28 15:48:24 rex-desktop kernel: [46198.810498]  [do_generic_mapping_read+0x235/0x3e0] do_generic_mapping_read+0x235/0x3e0
Nov 28 15:48:24 rex-desktop kernel: [46198.810505]  [file_read_actor+0x0/0x160] file_read_actor+0x0/0x160
Nov 28 15:48:24 rex-desktop kernel: [46198.810517]  [nfs:generic_file_aio_read+0xff/0x1b0] generic_file_aio_read+0xff/0x1b0
Nov 28 15:48:24 rex-desktop kernel: [46198.810532]  [ext3:do_sync_read+0xd9/0xbb0] do_sync_read+0xd9/0x120
Nov 28 15:48:24 rex-desktop kernel: [46198.810544]  [<ffffffff80253bf0>] autoremove_wake_function+0x0/0x30
Nov 28 15:48:24 rex-desktop kernel: [46198.810550]  [do_readv_writev+0x186/0x230] do_readv_writev+0x186/0x230
Nov 28 15:48:24 rex-desktop kernel: [46198.810561]  [thread_return+0x3a/0x57b] thread_return+0x3a/0x57b
Nov 28 15:48:24 rex-desktop kernel: [46198.810571]  [vfs_read+0xed/0x190] vfs_read+0xed/0x190
Nov 28 15:48:24 rex-desktop kernel: [46198.810577]  [sys_pread64+0x84/0xa0] sys_pread64+0x84/0xa0
Nov 28 15:48:24 rex-desktop kernel: [46198.810584]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Nov 28 15:48:24 rex-desktop kernel: [46198.810647] 
Nov 28 15:48:24 rex-desktop kernel: [46198.810649] Mem-info:
Nov 28 15:48:24 rex-desktop kernel: [46198.810650] Node 0 DMA per-cpu:
Nov 28 15:48:24 rex-desktop kernel: [46198.810653] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:24 rex-desktop kernel: [46198.810655] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:24 rex-desktop kernel: [46198.810657] Node 0 DMA32 per-cpu:
Nov 28 15:48:24 rex-desktop kernel: [46198.810659] CPU    0: Hot: hi:  186, btch:  31 usd: 171   Cold: hi:   62, btch:  15 usd:  10
Nov 28 15:48:24 rex-desktop kernel: [46198.810662] CPU    1: Hot: hi:  186, btch:  31 usd: 175   Cold: hi:   62, btch:  15 usd:  36
Nov 28 15:48:24 rex-desktop kernel: [46198.810665] Active:112239 inactive:106338 dirty:0 writeback:0 unstable:0
Nov 28 15:48:24 rex-desktop kernel: [46198.810666]  free:1422 slab:4831 mapped:3170 pagetables:4574 bounce:0
Nov 28 15:48:24 rex-desktop kernel: [46198.810668] Node 0 DMA free:1876kB min:44kB low:52kB high:64kB active:0kB inactive:0kB present:10896kB pages_scanned:0 all_unreclaimable? yes
Nov 28 15:48:24 rex-desktop kernel: [46198.810671] lowmem_reserve[]: 0 931 931 931
Nov 28 15:48:24 rex-desktop kernel: [46198.810674] Node 0 DMA32 free:3812kB min:3876kB low:4844kB high:5812kB active:448956kB inactive:425448kB present:953380kB pages_scanned:1697897 all_unreclaimable? yes
Nov 28 15:48:24 rex-desktop kernel: [46198.810678] lowmem_reserve[]: 0 0 0 0
Nov 28 15:48:24 rex-desktop kernel: [46198.810680] Node 0 DMA: 1*4kB 4*8kB 3*16kB 2*32kB 3*64kB 4*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1876kB
Nov 28 15:48:24 rex-desktop kernel: [46198.810686] Node 0 DMA32: 27*4kB 1*8kB 1*16kB 2*32kB 0*64kB 0*128kB 0*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 3780kB
Nov 28 15:48:24 rex-desktop kernel: [46198.810693] Swap cache: add 546472, delete 546447, find 85103/112557, race 0+0
Nov 28 15:48:24 rex-desktop kernel: [46198.810695] Free swap  = 0kB
Nov 28 15:48:24 rex-desktop kernel: [46198.810696] Total swap = 976552kB
Nov 28 15:48:24 rex-desktop kernel: [46198.810697] Free swap:            0kB
Nov 28 15:48:24 rex-desktop kernel: [46198.819048] 245744 pages of RAM
Nov 28 15:48:24 rex-desktop kernel: [46198.819051] 8888 reserved pages
Nov 28 15:48:24 rex-desktop kernel: [46198.819052] 605 pages shared
Nov 28 15:48:24 rex-desktop kernel: [46198.819054] 11 pages swap cached
Nov 28 15:48:24 rex-desktop kernel: [46198.819056] Out of memory: kill process 6085 (x-session-manag) score 152816 or a child
Nov 28 15:48:24 rex-desktop kernel: [46198.819102] Killed process 6253 (gnome-panel)
Nov 28 15:48:24 rex-desktop kernel: [46480.234913] mount.ntfs invoked oom-killer: gfp_mask=0x201d0, order=0, oomkilladj=0
Nov 28 15:48:24 rex-desktop kernel: [46480.234925] Pid: 2683, comm: mount.ntfs Tainted: P        2.6.24-21-generic #1
Nov 28 15:48:24 rex-desktop kernel: [46480.234928] 
Nov 28 15:48:24 rex-desktop kernel: [46480.234929] Call Trace:
Nov 28 15:48:24 rex-desktop kernel: [46480.234994]  [oom_kill_process+0xf6/0x110] oom_kill_process+0xf6/0x110
Nov 28 15:48:24 rex-desktop kernel: [46480.235002]  [out_of_memory+0x15e/0x270] out_of_memory+0x15e/0x270
Nov 28 15:48:24 rex-desktop kernel: [46480.235013]  [__alloc_pages+0x3b9/0x3f0] __alloc_pages+0x3b9/0x3f0
Nov 28 15:48:24 rex-desktop kernel: [46480.235027]  [__do_page_cache_readahead+0xe0/0x210] __do_page_cache_readahead+0xe0/0x210
Nov 28 15:48:24 rex-desktop kernel: [46480.235040]  [ondemand_readahead+0x9c/0x1c0] ondemand_readahead+0x9c/0x1c0
Nov 28 15:48:24 rex-desktop kernel: [46480.235048]  [do_generic_mapping_read+0x235/0x3e0] do_generic_mapping_read+0x235/0x3e0
Nov 28 15:48:24 rex-desktop kernel: [46480.235052]  [file_read_actor+0x0/0x160] file_read_actor+0x0/0x160
Nov 28 15:48:24 rex-desktop kernel: [46480.235063]  [nfs:generic_file_aio_read+0xff/0x1b0] generic_file_aio_read+0xff/0x1b0
Nov 28 15:48:24 rex-desktop kernel: [46480.235078]  [ext3:do_sync_read+0xd9/0xbb0] do_sync_read+0xd9/0x120
Nov 28 15:48:24 rex-desktop kernel: [46480.235090]  [<ffffffff80253bf0>] autoremove_wake_function+0x0/0x30
Nov 28 15:48:24 rex-desktop kernel: [46480.235105]  [thread_return+0x3a/0x57b] thread_return+0x3a/0x57b
Nov 28 15:48:24 rex-desktop kernel: [46480.235115]  [vfs_read+0xed/0x190] vfs_read+0xed/0x190
Nov 28 15:48:24 rex-desktop kernel: [46480.235121]  [sys_pread64+0x84/0xa0] sys_pread64+0x84/0xa0
Nov 28 15:48:24 rex-desktop kernel: [46480.235129]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Nov 28 15:48:24 rex-desktop kernel: [46480.235140] 
Nov 28 15:48:24 rex-desktop kernel: [46480.235141] Mem-info:
Nov 28 15:48:24 rex-desktop kernel: [46480.235143] Node 0 DMA per-cpu:
Nov 28 15:48:24 rex-desktop kernel: [46480.235146] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:24 rex-desktop kernel: [46480.235149] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:24 rex-desktop kernel: [46480.235151] Node 0 DMA32 per-cpu:
Nov 28 15:48:24 rex-desktop kernel: [46480.235153] CPU    0: Hot: hi:  186, btch:  31 usd: 163   Cold: hi:   62, btch:  15 usd:  30
Nov 28 15:48:24 rex-desktop kernel: [46480.235156] CPU    1: Hot: hi:  186, btch:  31 usd: 185   Cold: hi:   62, btch:  15 usd:  20
Nov 28 15:48:24 rex-desktop kernel: [46480.235160] Active:107784 inactive:110919 dirty:0 writeback:0 unstable:0
Nov 28 15:48:24 rex-desktop kernel: [46480.235161]  free:1422 slab:4811 mapped:3170 pagetables:4428 bounce:0
Nov 28 15:48:24 rex-desktop kernel: [46480.235162] Node 0 DMA free:1876kB min:44kB low:52kB high:64kB active:0kB inactive:0kB present:10896kB pages_scanned:0 all_unreclaimable? yes
Nov 28 15:48:24 rex-desktop kernel: [46480.235167] lowmem_reserve[]: 0 931 931 931
Nov 28 15:48:24 rex-desktop kernel: [46480.235169] Node 0 DMA32 free:3812kB min:3876kB low:4844kB high:5812kB active:431136kB inactive:443676kB present:953380kB pages_scanned:1498339 all_unreclaimable? yes
Nov 28 15:48:24 rex-desktop kernel: [46480.235173] lowmem_reserve[]: 0 0 0 0
Nov 28 15:48:24 rex-desktop kernel: [46480.235175] Node 0 DMA: 1*4kB 4*8kB 3*16kB 2*32kB 3*64kB 4*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1876kB
Nov 28 15:48:24 rex-desktop kernel: [46480.235182] Node 0 DMA32: 26*4kB 1*8kB 1*16kB 2*32kB 0*64kB 0*128kB 0*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 3776kB
Nov 28 15:48:24 rex-desktop kernel: [46480.235189] Swap cache: add 557638, delete 557638, find 86317/114673, race 0+0
Nov 28 15:48:24 rex-desktop kernel: [46480.235191] Free swap  = 0kB
Nov 28 15:48:24 rex-desktop kernel: [46480.235192] Total swap = 976552kB
Nov 28 15:48:24 rex-desktop kernel: [46480.235193] Free swap:            0kB
Nov 28 15:48:24 rex-desktop kernel: [46480.243078] 245744 pages of RAM
Nov 28 15:48:24 rex-desktop kernel: [46480.243081] 8888 reserved pages
Nov 28 15:48:24 rex-desktop kernel: [46480.243082] 452 pages shared
Nov 28 15:48:24 rex-desktop kernel: [46480.243083] 0 pages swap cached
Nov 28 15:48:24 rex-desktop kernel: [46480.243085] Out of memory: kill process 6085 (x-session-manag) score 140406 or a child
Nov 28 15:48:24 rex-desktop kernel: [46480.243130] Killed process 6254 (nautilus)
Nov 28 15:48:24 rex-desktop kernel: [46511.708116] mount.ntfs invoked oom-killer: gfp_mask=0x201d0, order=0, oomkilladj=0
Nov 28 15:48:24 rex-desktop kernel: [46511.708129] Pid: 2683, comm: mount.ntfs Tainted: P        2.6.24-21-generic #1
Nov 28 15:48:24 rex-desktop kernel: [46511.708131] 
Nov 28 15:48:24 rex-desktop kernel: [46511.708132] Call Trace:
Nov 28 15:48:24 rex-desktop kernel: [46511.708198]  [oom_kill_process+0xf6/0x110] oom_kill_process+0xf6/0x110
Nov 28 15:48:24 rex-desktop kernel: [46511.708207]  [out_of_memory+0x15e/0x270] out_of_memory+0x15e/0x270
Nov 28 15:48:24 rex-desktop kernel: [46511.708218]  [__alloc_pages+0x3b9/0x3f0] __alloc_pages+0x3b9/0x3f0
Nov 28 15:48:24 rex-desktop kernel: [46511.708232]  [__do_page_cache_readahead+0xe0/0x210] __do_page_cache_readahead+0xe0/0x210
Nov 28 15:48:24 rex-desktop kernel: [46511.708245]  [ondemand_readahead+0x9c/0x1c0] ondemand_readahead+0x9c/0x1c0
Nov 28 15:48:24 rex-desktop kernel: [46511.708253]  [do_generic_mapping_read+0x235/0x3e0] do_generic_mapping_read+0x235/0x3e0
Nov 28 15:48:24 rex-desktop kernel: [46511.708257]  [file_read_actor+0x0/0x160] file_read_actor+0x0/0x160
Nov 28 15:48:24 rex-desktop kernel: [46511.708269]  [nfs:generic_file_aio_read+0xff/0x1b0] generic_file_aio_read+0xff/0x1b0
Nov 28 15:48:24 rex-desktop kernel: [46511.708284]  [ext3:do_sync_read+0xd9/0xbb0] do_sync_read+0xd9/0x120
Nov 28 15:48:24 rex-desktop kernel: [46511.708298]  [<ffffffff80253bf0>] autoremove_wake_function+0x0/0x30
Nov 28 15:48:24 rex-desktop kernel: [46511.708304]  [do_readv_writev+0x186/0x230] do_readv_writev+0x186/0x230
Nov 28 15:48:24 rex-desktop kernel: [46511.708316]  [thread_return+0x3a/0x57b] thread_return+0x3a/0x57b
Nov 28 15:48:24 rex-desktop kernel: [46511.708326]  [vfs_read+0xed/0x190] vfs_read+0xed/0x190
Nov 28 15:48:24 rex-desktop kernel: [46511.708332]  [sys_pread64+0x84/0xa0] sys_pread64+0x84/0xa0
Nov 28 15:48:24 rex-desktop kernel: [46511.708340]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Nov 28 15:48:24 rex-desktop kernel: [46511.708351] 
Nov 28 15:48:24 rex-desktop kernel: [46511.708353] Mem-info:
Nov 28 15:48:24 rex-desktop kernel: [46511.708354] Node 0 DMA per-cpu:
Nov 28 15:48:24 rex-desktop kernel: [46511.708357] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:24 rex-desktop kernel: [46511.708360] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:24 rex-desktop kernel: [46511.708361] Node 0 DMA32 per-cpu:
Nov 28 15:48:24 rex-desktop kernel: [46511.708364] CPU    0: Hot: hi:  186, btch:  31 usd: 179   Cold: hi:   62, btch:  15 usd:  57
Nov 28 15:48:24 rex-desktop kernel: [46511.708366] CPU    1: Hot: hi:  186, btch:  31 usd: 160   Cold: hi:   62, btch:  15 usd:  14
Nov 28 15:48:24 rex-desktop kernel: [46511.708370] Active:111047 inactive:107925 dirty:0 writeback:0 unstable:0
Nov 28 15:48:24 rex-desktop kernel: [46511.708371]  free:1435 slab:4808 mapped:3170 pagetables:4264 bounce:0
Nov 28 15:48:24 rex-desktop kernel: [46511.708373] Node 0 DMA free:1876kB min:44kB low:52kB high:64kB active:0kB inactive:0kB present:10896kB pages_scanned:0 all_unreclaimable? yes
Nov 28 15:48:24 rex-desktop kernel: [46511.708377] lowmem_reserve[]: 0 931 931 931
Nov 28 15:48:24 rex-desktop kernel: [46511.708379] Node 0 DMA32 free:3864kB min:3876kB low:4844kB high:5812kB active:444188kB inactive:431700kB present:953380kB pages_scanned:1595760 all_unreclaimable? yes
Nov 28 15:48:24 rex-desktop kernel: [46511.708384] lowmem_reserve[]: 0 0 0 0
Nov 28 15:48:24 rex-desktop kernel: [46511.708386] Node 0 DMA: 1*4kB 4*8kB 3*16kB 2*32kB 3*64kB 4*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1876kB
Nov 28 15:48:24 rex-desktop kernel: [46511.708392] Node 0 DMA32: 40*4kB 1*8kB 0*16kB 2*32kB 0*64kB 0*128kB 0*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 3816kB
Nov 28 15:48:24 rex-desktop kernel: [46511.708399] Swap cache: add 577308, delete 577308, find 88444/118141, race 0+0
Nov 28 15:48:24 rex-desktop kernel: [46511.708401] Free swap  = 0kB
Nov 28 15:48:24 rex-desktop kernel: [46511.708402] Total swap = 976552kB
Nov 28 15:48:24 rex-desktop kernel: [46511.708403] Free swap:            0kB
Nov 28 15:48:24 rex-desktop kernel: [46511.716234] 245744 pages of RAM
Nov 28 15:48:24 rex-desktop kernel: [46511.716236] 8888 reserved pages
Nov 28 15:48:24 rex-desktop kernel: [46511.716237] 634 pages shared
Nov 28 15:48:24 rex-desktop kernel: [46511.716238] 0 pages swap cached
Nov 28 15:48:24 rex-desktop kernel: [46511.716240] Out of memory: kill process 6085 (x-session-manag) score 103801 or a child
Nov 28 15:48:24 rex-desktop kernel: [46511.716285] Killed process 6326 (bluetooth-apple)
Nov 28 15:48:24 rex-desktop kernel: [48027.255656] mount.ntfs invoked oom-killer: gfp_mask=0x201d0, order=0, oomkilladj=0
Nov 28 15:48:24 rex-desktop kernel: [48027.255670] Pid: 2683, comm: mount.ntfs Tainted: P        2.6.24-21-generic #1
Nov 28 15:48:24 rex-desktop kernel: [48027.255674] 
Nov 28 15:48:24 rex-desktop kernel: [48027.255675] Call Trace:
Nov 28 15:48:24 rex-desktop kernel: [48027.255753]  [oom_kill_process+0xf6/0x110] oom_kill_process+0xf6/0x110
Nov 28 15:48:24 rex-desktop kernel: [48027.255762]  [out_of_memory+0x15e/0x270] out_of_memory+0x15e/0x270
Nov 28 15:48:24 rex-desktop kernel: [48027.255773]  [__alloc_pages+0x3b9/0x3f0] __alloc_pages+0x3b9/0x3f0
Nov 28 15:48:24 rex-desktop kernel: [48027.255786]  [__do_page_cache_readahead+0xe0/0x210] __do_page_cache_readahead+0xe0/0x210
Nov 28 15:48:24 rex-desktop kernel: [48027.255799]  [ondemand_readahead+0x9c/0x1c0] ondemand_readahead+0x9c/0x1c0
Nov 28 15:48:24 rex-desktop kernel: [48027.255808]  [do_generic_mapping_read+0x235/0x3e0] do_generic_mapping_read+0x235/0x3e0
Nov 28 15:48:24 rex-desktop kernel: [48027.255812]  [file_read_actor+0x0/0x160] file_read_actor+0x0/0x160
Nov 28 15:48:24 rex-desktop kernel: [48027.255823]  [nfs:generic_file_aio_read+0xff/0x1b0] generic_file_aio_read+0xff/0x1b0
Nov 28 15:48:24 rex-desktop kernel: [48027.255839]  [ext3:do_sync_read+0xd9/0xbb0] do_sync_read+0xd9/0x120
Nov 28 15:48:24 rex-desktop kernel: [48027.255851]  [<ffffffff80253bf0>] autoremove_wake_function+0x0/0x30
Nov 28 15:48:24 rex-desktop kernel: [48027.255867]  [thread_return+0x3a/0x57b] thread_return+0x3a/0x57b
Nov 28 15:48:24 rex-desktop kernel: [48027.255877]  [vfs_read+0xed/0x190] vfs_read+0xed/0x190
Nov 28 15:48:24 rex-desktop kernel: [48027.255883]  [sys_pread64+0x84/0xa0] sys_pread64+0x84/0xa0
Nov 28 15:48:24 rex-desktop kernel: [48027.255892]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Nov 28 15:48:24 rex-desktop kernel: [48027.255903] 
Nov 28 15:48:24 rex-desktop kernel: [48027.255904] Mem-info:
Nov 28 15:48:24 rex-desktop kernel: [48027.255906] Node 0 DMA per-cpu:
Nov 28 15:48:24 rex-desktop kernel: [48027.255909] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:24 rex-desktop kernel: [48027.255912] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:24 rex-desktop kernel: [48027.255914] Node 0 DMA32 per-cpu:
Nov 28 15:48:24 rex-desktop kernel: [48027.255916] CPU    0: Hot: hi:  186, btch:  31 usd:  94   Cold: hi:   62, btch:  15 usd:  43
Nov 28 15:48:24 rex-desktop kernel: [48027.255919] CPU    1: Hot: hi:  186, btch:  31 usd: 171   Cold: hi:   62, btch:  15 usd:  27
Nov 28 15:48:24 rex-desktop kernel: [48027.255923] Active:110798 inactive:108279 dirty:0 writeback:0 unstable:0
Nov 28 15:48:24 rex-desktop kernel: [48027.255924]  free:1431 slab:4788 mapped:3170 pagetables:4302 bounce:0
Nov 28 15:48:24 rex-desktop kernel: [48027.255926] Node 0 DMA free:1876kB min:44kB low:52kB high:64kB active:0kB inactive:0kB present:10896kB pages_scanned:0 all_unreclaimable? yes
Nov 28 15:48:24 rex-desktop kernel: [48027.255930] lowmem_reserve[]: 0 931 931 931
Nov 28 15:48:24 rex-desktop kernel: [48027.255932] Node 0 DMA32 free:3848kB min:3876kB low:4844kB high:5812kB active:443192kB inactive:433116kB present:953380kB pages_scanned:1451775 all_unreclaimable? yes
Nov 28 15:48:24 rex-desktop kernel: [48027.255937] lowmem_reserve[]: 0 0 0 0
Nov 28 15:48:24 rex-desktop kernel: [48027.255939] Node 0 DMA: 1*4kB 4*8kB 3*16kB 2*32kB 3*64kB 4*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1876kB
Nov 28 15:48:24 rex-desktop kernel: [48027.255945] Node 0 DMA32: 36*4kB 0*8kB 0*16kB 2*32kB 0*64kB 0*128kB 0*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 3792kB
Nov 28 15:48:24 rex-desktop kernel: [48027.255952] Swap cache: add 586385, delete 586385, find 89061/119704, race 0+0
Nov 28 15:48:24 rex-desktop kernel: [48027.255954] Free swap  = 0kB
Nov 28 15:48:24 rex-desktop kernel: [48027.255955] Total swap = 976552kB
Nov 28 15:48:24 rex-desktop kernel: [48027.255956] Free swap:            0kB
Nov 28 15:48:24 rex-desktop kernel: [48027.263838] 245744 pages of RAM
Nov 28 15:48:24 rex-desktop kernel: [48027.263841] 8888 reserved pages
Nov 28 15:48:24 rex-desktop kernel: [48027.263842] 375 pages shared
Nov 28 15:48:24 rex-desktop kernel: [48027.263843] 0 pages swap cached
Nov 28 15:48:24 rex-desktop kernel: [48027.263845] Out of memory: kill process 6085 (x-session-manag) score 106826 or a child
Nov 28 15:48:24 rex-desktop kernel: [48027.263893] Killed process 6329 (update-notifier)
Nov 28 15:48:24 rex-desktop kernel: [48122.894019] cron invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
Nov 28 15:48:24 rex-desktop kernel: [48122.894033] Pid: 5824, comm: cron Tainted: P        2.6.24-21-generic #1
Nov 28 15:48:24 rex-desktop kernel: [48122.894035] 
Nov 28 15:48:24 rex-desktop kernel: [48122.894036] Call Trace:
Nov 28 15:48:24 rex-desktop kernel: [48122.894110]  [oom_kill_process+0xf6/0x110] oom_kill_process+0xf6/0x110
Nov 28 15:48:24 rex-desktop kernel: [48122.894122]  [out_of_memory+0x15e/0x270] out_of_memory+0x15e/0x270
Nov 28 15:48:24 rex-desktop kernel: [48122.894130]  [<ffffffff80253bf0>] autoremove_wake_function+0x0/0x30
Nov 28 15:48:24 rex-desktop kernel: [48122.894138]  [__alloc_pages+0x3b9/0x3f0] __alloc_pages+0x3b9/0x3f0
Nov 28 15:48:24 rex-desktop kernel: [48122.894151]  [__do_page_cache_readahead+0xe0/0x210] __do_page_cache_readahead+0xe0/0x210
Nov 28 15:48:24 rex-desktop kernel: [48122.894164]  [nfs:filemap_fault+0x28e/0x570] filemap_fault+0x28e/0x390
Nov 28 15:48:24 rex-desktop kernel: [48122.894174]  [__do_fault+0x6a/0x430] __do_fault+0x6a/0x430
Nov 28 15:48:24 rex-desktop kernel: [48122.894187]  [handle_mm_fault+0x1b2/0x7b0] handle_mm_fault+0x1b2/0x7b0
Nov 28 15:48:24 rex-desktop kernel: [48122.894203]  [do_page_fault+0x1ab/0x840] do_page_fault+0x1ab/0x840
Nov 28 15:48:24 rex-desktop kernel: [48122.894219]  [sys_newstat+0x36/0x50] sys_newstat+0x36/0x50
Nov 28 15:48:24 rex-desktop kernel: [48122.894229]  [error_exit+0x0/0x51] error_exit+0x0/0x51
Nov 28 15:48:24 rex-desktop kernel: [48122.894244] 
Nov 28 15:48:24 rex-desktop kernel: [48122.894246] Mem-info:
Nov 28 15:48:24 rex-desktop kernel: [48122.894248] Node 0 DMA per-cpu:
Nov 28 15:48:24 rex-desktop kernel: [48122.894250] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:24 rex-desktop kernel: [48122.894253] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:24 rex-desktop kernel: [48122.894255] Node 0 DMA32 per-cpu:
Nov 28 15:48:24 rex-desktop kernel: [48122.894257] CPU    0: Hot: hi:  186, btch:  31 usd: 163   Cold: hi:   62, btch:  15 usd:  20
Nov 28 15:48:24 rex-desktop kernel: [48122.894260] CPU    1: Hot: hi:  186, btch:  31 usd: 152   Cold: hi:   62, btch:  15 usd:  17
Nov 28 15:48:24 rex-desktop kernel: [48122.894264] Active:109250 inactive:109972 dirty:0 writeback:0 unstable:0
Nov 28 15:48:24 rex-desktop kernel: [48122.894266]  free:1431 slab:4735 mapped:3170 pagetables:4117 bounce:0
Nov 28 15:48:24 rex-desktop kernel: [48122.894267] Node 0 DMA free:1876kB min:44kB low:52kB high:64kB active:0kB inactive:0kB present:10896kB pages_scanned:0 all_unreclaimable? yes
Nov 28 15:48:24 rex-desktop kernel: [48122.894271] lowmem_reserve[]: 0 931 931 931
Nov 28 15:48:24 rex-desktop kernel: [48122.894274] Node 0 DMA32 free:3848kB min:3876kB low:4844kB high:5812kB active:437000kB inactive:439888kB present:953380kB pages_scanned:1379350 all_unreclaimable? yes
Nov 28 15:48:24 rex-desktop kernel: [48122.894278] lowmem_reserve[]: 0 0 0 0
Nov 28 15:48:24 rex-desktop kernel: [48122.894280] Node 0 DMA: 1*4kB 4*8kB 3*16kB 2*32kB 3*64kB 4*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1876kB
Nov 28 15:48:24 rex-desktop kernel: [48122.894287] Node 0 DMA32: 44*4kB 1*8kB 1*16kB 1*32kB 0*64kB 0*128kB 0*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 3816kB
Nov 28 15:48:24 rex-desktop kernel: [48122.894294] Swap cache: add 591813, delete 591813, find 89719/120728, race 0+0
Nov 28 15:48:24 rex-desktop kernel: [48122.894295] Free swap  = 0kB
Nov 28 15:48:24 rex-desktop kernel: [48122.894296] Total swap = 976552kB
Nov 28 15:48:24 rex-desktop kernel: [48122.894297] Free swap:            0kB
Nov 28 15:48:24 rex-desktop kernel: [48122.903478] 245744 pages of RAM
Nov 28 15:48:24 rex-desktop kernel: [48122.903482] 8888 reserved pages
Nov 28 15:48:24 rex-desktop kernel: [48122.903483] 419 pages shared
Nov 28 15:48:24 rex-desktop kernel: [48122.903484] 0 pages swap cached
Nov 28 15:48:24 rex-desktop kernel: [48122.903487] Out of memory: kill process 6085 (x-session-manag) score 89640 or a child
Nov 28 15:48:24 rex-desktop kernel: [48122.903545] Killed process 6333 (evolution-alarm)
Nov 28 15:48:24 rex-desktop kernel: [48546.497441] dbus-daemon invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
Nov 28 15:48:24 rex-desktop kernel: [48546.497455] Pid: 6222, comm: dbus-daemon Tainted: P        2.6.24-21-generic #1
Nov 28 15:48:24 rex-desktop kernel: [48546.497460] 
Nov 28 15:48:24 rex-desktop kernel: [48546.497461] Call Trace:
Nov 28 15:48:24 rex-desktop kernel: [48546.497528]  [oom_kill_process+0xf6/0x110] oom_kill_process+0xf6/0x110
Nov 28 15:48:24 rex-desktop kernel: [48546.497538]  [out_of_memory+0x15e/0x270] out_of_memory+0x15e/0x270
Nov 28 15:48:24 rex-desktop kernel: [48546.497548]  [__alloc_pages+0x3b9/0x3f0] __alloc_pages+0x3b9/0x3f0
Nov 28 15:48:24 rex-desktop kernel: [48546.497561]  [__do_page_cache_readahead+0xe0/0x210] __do_page_cache_readahead+0xe0/0x210
Nov 28 15:48:24 rex-desktop kernel: [48546.497574]  [nfs:filemap_fault+0x28e/0x570] filemap_fault+0x28e/0x390
Nov 28 15:48:24 rex-desktop kernel: [48546.497584]  [__do_fault+0x6a/0x430] __do_fault+0x6a/0x430
Nov 28 15:48:24 rex-desktop kernel: [48546.497596]  [handle_mm_fault+0x1b2/0x7b0] handle_mm_fault+0x1b2/0x7b0
Nov 28 15:48:24 rex-desktop kernel: [48546.497611]  [do_page_fault+0x1ab/0x840] do_page_fault+0x1ab/0x840
Nov 28 15:48:24 rex-desktop kernel: [48546.497618]  [do_readv_writev+0x186/0x230] do_readv_writev+0x186/0x230
Nov 28 15:48:24 rex-desktop kernel: [48546.497629]  [d_kill+0x48/0x70] d_kill+0x48/0x70
Nov 28 15:48:25 rex-desktop kernel: [48546.497633]  [sunrpc:dput+0xab/0x1c0] dput+0xab/0x140
Nov 28 15:48:25 rex-desktop kernel: [48546.497643]  [error_exit+0x0/0x51] error_exit+0x0/0x51
Nov 28 15:48:25 rex-desktop kernel: [48546.497657] 
Nov 28 15:48:25 rex-desktop kernel: [48546.497659] Mem-info:
Nov 28 15:48:25 rex-desktop kernel: [48546.497660] Node 0 DMA per-cpu:
Nov 28 15:48:25 rex-desktop kernel: [48546.497663] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:25 rex-desktop kernel: [48546.497666] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Nov 28 15:48:25 rex-desktop kernel: [48546.497668] Node 0 DMA32 per-cpu:
Nov 28 15:48:25 rex-desktop kernel: [48546.497670] CPU    0: Hot: hi:  186, btch:  31 usd: 179   Cold: hi:   62, btch:  15 usd:  58
Nov 28 15:48:25 rex-desktop kernel: [48546.497673] CPU    1: Hot: hi:  186, btch:  31 usd: 171   Cold: hi:   62, btch:  15 usd:   7
Nov 28 15:48:25 rex-desktop kernel: [48546.497677] Active:90890 inactive:128456 dirty:0 writeback:0 unstable:0
Nov 28 15:48:25 rex-desktop kernel: [48546.497678]  free:1438 slab:4724 mapped:3170 pagetables:3983 bounce:0
Nov 28 15:48:25 rex-desktop kernel: [48546.497679] Node 0 DMA free:1876kB min:44kB low:52kB high:64kB active:0kB inactive:0kB present:10896kB pages_scanned:0 all_unreclaimable? yes
Nov 28 15:48:25 rex-desktop kernel: [48546.497683] lowmem_reserve[]: 0 931 931 931
Nov 28 15:48:25 rex-desktop kernel: [48546.497686] Node 0 DMA32 free:3876kB min:3876kB low:4844kB high:5812kB active:363560kB inactive:513824kB present:953380kB pages_scanned:2144118 all_unreclaimable? yes
Nov 28 15:48:25 rex-desktop kernel: [48546.497690] lowmem_reserve[]: 0 0 0 0
Nov 28 15:48:25 rex-desktop kernel: [48546.497692] Node 0 DMA: 1*4kB 4*8kB 3*16kB 2*32kB 3*64kB 4*128kB 2*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 1876kB
Nov 28 15:48:25 rex-desktop kernel: [48546.497699] Node 0 DMA32: 43*4kB 1*8kB 1*16kB 1*32kB 0*64kB 0*128kB 0*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 3812kB
Nov 28 15:48:25 rex-desktop kernel: [48546.497705] Swap cache: add 594909, delete 594909, find 89740/121041, race 0+0
Nov 28 15:48:25 rex-desktop kernel: [48546.497707] Free swap  = 0kB
Nov 28 15:48:25 rex-desktop kernel: [48546.497708] Total swap = 976552kB
Nov 28 15:48:25 rex-desktop kernel: [48546.497709] Free swap:            0kB
Nov 28 15:48:25 rex-desktop kernel: [48546.505773] 245744 pages of RAM
Nov 28 15:48:25 rex-desktop kernel: [48546.505776] 8888 reserved pages
Nov 28 15:48:25 rex-desktop kernel: [48546.505777] 680 pages shared
Nov 28 15:48:25 rex-desktop kernel: [48546.505778] 0 pages swap cached
Nov 28 15:48:25 rex-desktop kernel: [48546.505780] Out of memory: kill process 6668 (firefox) score 61956 or a child
Nov 28 15:48:25 rex-desktop kernel: [48546.505824] Killed process 6668 (firefox)
Nov 28 16:14:13 rex-desktop kernel: [49569.320878] hald-addon-stor invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
Nov 28 16:14:52 rex-desktop kernel: [49569.320891] Pid: 5647, comm: hald-addon-stor Tainted: P        2.6.24-21-generic #1
Nov 28 16:17:58 rex-desktop kernel: [49569.320895] 


```

When I get to the computer, ctrl+alt+backspace does nothing and I have to reboot with Magic SysRq.

---

### Post by ago on 2008-12-01
Out of memory: kill process 6668 (firefox) score 61956 or a child

You have some process (firefox) leaking memory

---

