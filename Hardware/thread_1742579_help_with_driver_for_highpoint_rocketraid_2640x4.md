---
title: "help with driver for highpoint rocketraid 2640x4"
date: 2011-04-29
forum: Hardware
---

### Post by dtemp132 on 2011-04-29
Trying to install Highpoint Rocketrad 2640x4 driver on 8.04 LTS server, I get the following problem when trying to load the driver. Driver seems to make install correctly, and the KO file below actually exists. Any suggestions would be welcome, thanks in advance! Running kernel 2.6.24-29-generic i686.

I think it's saying it doesn't think the device is installed... I'm very sure the device is installed and visible to the system. I've configured a volume in its menu that is displayed before the OS loads.

$ sudo modprobe rr26xx
[sudo] password for dtemp: 
FATAL: Error inserting rr26xx (/lib/modules/2.6.24-29-generic/kernel/drivers/scsi/rr26xx/rr26xx.ko): No such device

---

### Post by kaiseiken on 2011-12-19
I have the same problem with this driver.  dmesg output reveals that I have run out of memory.

[INDENT][254019.256238] rr62x:RocketRAID 62x SATA controller driver v1.1 (Dec 19 2011 10:58:04)
[254019.256273] pci 0000:05:00.0: setting latency timer to 64
[254019.256920] rr62x:adapter at PCI 5:0:0, IRQ 35
[254019.258020] insmod: page allocation failure: order:9, mode:0x20
[254019.258024] Pid: 14789, comm: insmod Tainted #1
[254019.258027] Call Trace:
[254019.258036]  [<ffffffff810d50fb>] warn_alloc_failed+0xeb/0x130
[254019.258042]  [<ffffffff810df83c>] ? wakeup_kswapd+0x10c/0x140
[254019.258046]  [<ffffffff810d626c>] __alloc_pages_nodemask+0x48c/0x770
[254019.258050]  [<ffffffff810d6562>] __get_free_pages+0x12/0x50
[254019.258063]  [<ffffffffa0003319>] hpt_detect+0x7c9/0x8a0 [rr62x]
[254019.258072]  [<ffffffff8183f561>] ? notifier_call_chain+0x51/0x80
[254019.258082]  [<ffffffffa003706b>] init_this_scsi_driver+0x6b/0xf9 [rr62x]
[254019.258085]  [<ffffffffa0037000>] ? 0xffffffffa0036fff
[254019.258090]  [<ffffffff810001ce>] do_one_initcall+0x3e/0x170
[254019.258096]  [<ffffffff81080c78>] sys_init_module+0x88/0x1e0
[254019.258100]  [<ffffffff818433fb>] system_call_fastpath+0x16/0x1b
[254019.258102] Mem-Info:
[254019.258104] DMA per-cpu:
[254019.258107] CPU    0: hi:    0, btch:   1 usd:   0
[254019.258109] CPU    1: hi:    0, btch:   1 usd:   0
[254019.258111] CPU    2: hi:    0, btch:   1 usd:   0
[254019.258114] CPU    3: hi:    0, btch:   1 usd:   0
[254019.258116] CPU    4: hi:    0, btch:   1 usd:   0
[254019.258118] CPU    5: hi:    0, btch:   1 usd:   0
[254019.258121] CPU    6: hi:    0, btch:   1 usd:   0
[254019.258123] CPU    7: hi:    0, btch:   1 usd:   0
[254019.258125] CPU    8: hi:    0, btch:   1 usd:   0
[254019.258128] CPU    9: hi:    0, btch:   1 usd:   0
[254019.258142] CPU   10: hi:    0, btch:   1 usd:   0
[254019.258145] CPU   11: hi:    0, btch:   1 usd:   0
[254019.258148] CPU   12: hi:    0, btch:   1 usd:   0
[254019.258151] CPU   13: hi:    0, btch:   1 usd:   0
[254019.258155] CPU   14: hi:    0, btch:   1 usd:   0
[254019.258158] CPU   15: hi:    0, btch:   1 usd:   0
[254019.258161] DMA32 per-cpu:
[254019.258165] CPU    0: hi:  186, btch:  31 usd: 169
[254019.258167] CPU    1: hi:  186, btch:  31 usd: 168
[254019.258170] CPU    2: hi:  186, btch:  31 usd: 171
[254019.258172] CPU    3: hi:  186, btch:  31 usd: 167
[254019.258174] CPU    4: hi:  186, btch:  31 usd: 169
[254019.258177] CPU    5: hi:  186, btch:  31 usd: 152
[254019.258179] CPU    6: hi:  186, btch:  31 usd: 111
[254019.258181] CPU    7: hi:  186, btch:  31 usd: 184
[254019.258184] CPU    8: hi:  186, btch:  31 usd: 159
[254019.258186] CPU    9: hi:  186, btch:  31 usd:  77
[254019.258189] CPU   10: hi:  186, btch:  31 usd: 163
[254019.258191] CPU   11: hi:  186, btch:  31 usd: 162
[254019.258194] CPU   12: hi:  186, btch:  31 usd:  47
[254019.258196] CPU   13: hi:  186, btch:  31 usd:  60
[254019.258198] CPU   14: hi:  186, btch:  31 usd:  85
[254019.258201] CPU   15: hi:  186, btch:  31 usd:  92
[254019.258203] Normal per-cpu:
[254019.258205] CPU    0: hi:  186, btch:  31 usd:  95
[254019.258207] CPU    1: hi:  186, btch:  31 usd: 141
[254019.258209] CPU    2: hi:  186, btch:  31 usd:  51
[254019.258212] CPU    3: hi:  186, btch:  31 usd: 157
[254019.258214] CPU    4: hi:  186, btch:  31 usd:  89
[254019.258217] CPU    5: hi:  186, btch:  31 usd: 175
[254019.258219] CPU    6: hi:  186, btch:  31 usd:  16
[254019.258221] CPU    7: hi:  186, btch:  31 usd: 181
[254019.258224] CPU    8: hi:  186, btch:  31 usd: 156
[254019.258226] CPU    9: hi:  186, btch:  31 usd:  98
[254019.258228] CPU   10: hi:  186, btch:  31 usd:  34
[254019.258231] CPU   11: hi:  186, btch:  31 usd: 112
[254019.258233] CPU   12: hi:  186, btch:  31 usd:  84
[254019.258235] CPU   13: hi:  186, btch:  31 usd: 166
[254019.258238] CPU   14: hi:  186, btch:  31 usd: 143
[254019.258240] CPU   15: hi:  186, btch:  31 usd:  99
[254019.258246] active_anon:543716 inactive_anon:110367 isolated_anon:51
[254019.258247]  active_file:1543258 inactive_file:1382980 isolated_file:0
[254019.258249]  unevictable:0 dirty:871 writeback:0 unstable:0
[254019.258250]  free:148650 slab_reclaimable:307820 slab_unreclaimable:47707
[254019.258251]  mapped:31118 shmem:98 pagetables:7250 bounce:0
[254019.258259] DMA free:15892kB min:12kB low:12kB high:16kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15684kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:16kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
[254019.258265] lowmem_reserve[]: 0 3243 16121 16121
[254019.258274] DMA32 free:191196kB min:3264kB low:4080kB high:4896kB active_anon:342536kB inactive_anon:70864kB active_file:1071848kB inactive_file:1082720kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:3321540kB mlocked:0kB dirty:8kB writeback:0kB mapped:2456kB shmem:0kB slab_reclaimable:523160kB slab_unreclaimable:6004kB kernel_stack:432kB pagetables:1848kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[254019.258282] lowmem_reserve[]: 0 0 12877 12877
[254019.258291] Normal free:387512kB min:12972kB low:16212kB high:19456kB active_anon:1832328kB inactive_anon:370604kB active_file:5101184kB inactive_file:4449200kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:13186560kB mlocked:0kB dirty:3476kB writeback:0kB mapped:122016kB shmem:392kB slab_reclaimable:708120kB slab_unreclaimable:184808kB kernel_stack:4096kB pagetables:27152kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:32 all_unreclaimable? no
[254019.258298] lowmem_reserve[]: 0 0 0 0
[254019.258302] DMA: 1*4kB 0*8kB 1*16kB 0*32kB 2*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 3*4096kB = 15892kB
[254019.258311] DMA32: 16745*4kB 2847*8kB 1622*16kB 417*32kB 207*64kB 164*128kB 93*256kB 6*512kB 1*1024kB 0*2048kB 0*4096kB = 191196kB
[254019.258321] Normal: 9796*4kB 6523*8kB 4151*16kB 1168*32kB 598*64kB 207*128kB 140*256kB 170*512kB 5*1024kB 0*2048kB 0*4096kB = 387928kB
[254019.258331] 2947667 total pagecache pages
[254019.258333] 21374 pages in swap cache
[254019.258335] Swap cache stats: add 80671, delete 59297, find 50792/53318
[254019.258338] Free swap  = 31148936kB
[254019.258339] Total swap = 31254452kB
[254019.317191] 4194288 pages RAM
[254019.317194] 88102 pages reserved
[254019.317196] 913093 pages shared
[254019.317197] 3118975 pages non-shared
[254019.317201] rr62x:out of memory
[/INDENT]

---

### Post by kaiseiken on 2011-12-19
**Update:** Downgraded to 2.6.39 kernel, compiled and attempted to load the same driver. Initially it looks like it loaded fine, then I get a Killed message and the whole machine locks up.  Looking at dmesg, I get the following output:

[INDENT][  351.603035] rr62x:adapter at PCI 5:0:0, IRQ 35
[  351.819088] rr62x:[0 0  ] start port.
[  351.819091] rr62x:[0 0  ] start port hard reset (probe 1).
[  352.018772] rr62x:[0 1  ] start port.
[  352.018774] rr62x:[0 1  ] start port hard reset (probe 1).
[  354.992732] rr62x:[0 0  ] start port soft reset (probe 1).
[  355.754363] rr62x:[0 1  ] start port soft reset (probe 1).
[  356.460148] rr62x:[0 0  ] pmp attached: vendor 1095 device 3726.
[  356.582946] rr62x:[0 1  ] pmp attached: vendor 1095 device 3726.
[  362.686358] rr62x:[0 0 0] start device soft reset.
[  363.456093] rr62x:[0 1 0] start device soft reset.
[  364.114405] rr62x:[0 0 1] start device soft reset.
[  364.772605] rr62x:[0 1 1] start device soft reset.
[  365.472664] rr62x:[0 0  ] port started successfully.
[  365.472667] rr62x:[0 0 0] device probed successfully.
[  365.505523] rr62x:[0 0 1] device probed successfully.
[  365.583474] rr62x:[0 1  ] port started successfully.
[  365.583477] rr62x:[0 1 0] device probed successfully.
[  365.614331] rr62x:[0 1 1] device probed successfully.
[  365.654459] scsi8 : rr62x
[  365.654566] BUG: unable to handle kernel paging request at 0000000000040004
[  365.654824] IP: [<ffffffffa000107b>] hpt_queuecommand+0xcb/0xc80 [rr62x]
[  365.654986] PGD 429849067 PUD 4254de067 PMD 0
[  365.655222] Oops: 0000 [#1] SMP
[  365.655410] last sysfs file: /sys/devices/pci0000:00/0000:00:06.0/0000:05:00.0/host8/scsi_host/host8/uevent
[  365.655581] CPU 2
[  365.655627] Modules linked in: rr62x(P+)
[  365.655922]
[  365.656027] Pid: 4530, comm: modprobe Tainted: P            2.6.39 #1 Dell Inc. PowerEdge R710/00NH4P
[  365.656332] RIP: 0010:[<ffffffffa000107b>]  [<ffffffffa000107b>] hpt_queuecommand+0xcb/0xc80 [rr62x]
[  365.656556] RSP: 0018:ffff880402137948  EFLAGS: 00010202
[  365.656665] RAX: 0000000000040004 RBX: ffff880425c04000 RCX: ffff8804021a00f0
[  365.656779] RDX: ffff8803ebb05a00 RSI: 0000000000000000 RDI: ffff8804021a00d8
[  365.656889] RBP: ffff8804021379a8 R08: 0000000000000000 R09: 0000000000000000
[  365.657004] R10: 0000000000000000 R11: 0000000000000000 R12: ffff8803ebb05800
[  365.657114] R13: ffff8804021a0000 R14: ffff8804021a00d8 R15: ffff8804263cee00
[  365.657226] FS:  00007fd436bd1700(0000) GS:ffff88042f240000(0000) knlGS:0000000000000000
[  365.657394] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  365.657503] CR2: 0000000000040004 CR3: 000000042919a000 CR4: 00000000000006e0
[  365.657614] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  365.657724] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  365.657833] Process modprobe (pid: 4530, threadinfo ffff880402136000, task ffff88042cdf65c0)
[  365.658008] Stack:
[  365.658109]  ffff880402137998 ffffffff81054788 ffff88042b8aa760 0000000000000086
[  365.658443]  ffff88042b8aa760 ffff8803ea920000 ffff880425c04000 ffff8804263cee00
[  365.658775]  ffff880425c04000 0000000000000000 ffff8803ea920350 ffff880425c03848
[  365.659107] Call Trace:
[  365.659217]  [<ffffffff81054788>] ? mod_timer+0x168/0x2c0
[  365.659334]  [<ffffffff81426d7f>] scsi_dispatch_cmd+0xcf/0x230
[  365.659444]  [<ffffffff8142d2ea>] scsi_request_fn+0x3ba/0x4d0
[  365.659556]  [<ffffffff81347736>] __blk_run_queue+0x16/0x20
[  365.659665]  [<ffffffff813511ae>] blk_execute_rq_nowait+0x5e/0xa0
[  365.659774]  [<ffffffff81351250>] blk_execute_rq+0x60/0xb0
[  365.659882]  [<ffffffff8134bdab>] ? blk_rq_bio_prep+0x2b/0xc0
[  365.659993]  [<ffffffff81350e26>] ? blk_rq_map_kern+0xd6/0x150
[  365.660102]  [<ffffffff8142e757>] scsi_execute+0xf7/0x160
[  365.660210]  [<ffffffff8142e93e>] scsi_execute_req+0xae/0x140
[  365.660318]  [<ffffffff8142fac9>] scsi_probe_and_add_lun+0x219/0xbd0
[  365.660433]  [<ffffffff81438d61>] ? spi_target_match+0x51/0xa0
[  365.660543]  [<ffffffff814308fe>] __scsi_scan_target+0xfe/0x630
[  365.660653]  [<ffffffff8135fac1>] ? ida_get_new_above+0x151/0x220
[  365.660767]  [<ffffffff8136010b>] ? idr_pre_get+0x4b/0x90
[  365.660877]  [<ffffffff81430eb7>] scsi_scan_channel+0x87/0xb0
[  365.660990]  [<ffffffff81430fc1>] scsi_scan_host_selected+0xe1/0x140
[  365.661100]  [<ffffffff814310a9>] do_scsi_scan_host+0x89/0x90
[  365.661215]  [<ffffffff81431398>] scsi_scan_host+0x188/0x1d0
[  365.661330]  [<ffffffffa00380b0>] init_this_scsi_driver+0xb0/0x103 [rr62x]
[  365.661440]  [<ffffffffa0038000>] ? 0xffffffffa0037fff
[  365.661554]  [<ffffffff810001ce>] do_one_initcall+0x3e/0x170
[  365.661666]  [<ffffffff8108014b>] sys_init_module+0xbb/0x200
[  365.661778]  [<ffffffff8182f2fb>] system_call_fastpath+0x16/0x1b
[  365.661885] Code: 5e 41 5f c9 c3 0f 1f 00 8b b0 80 00 00 00 4c 89 f7 e8 0a b2 00 00 48 85 c0 49 89 c4 74 25 f6 80 f0 01 00 00 01 74 1c 48 8b 43 50
[  365.663828]  38 a1 76 26 c7 83 e0 00 00 00 00 00 05 05 4c 8b bb 90 00 00
[  365.664921] RIP  [<ffffffffa000107b>] hpt_queuecommand+0xcb/0xc80 [rr62x]
[  365.665080]  RSP <ffff880402137948>
[  365.665184] CR2: 0000000000040004
[  365.665292] ---[ end trace 67323ee4bf10846b ]---
[/INDENT]

---

