---
title: "[Samsung ATIV 9 Lite NP905S3G-K01] Graphic Problems / GUI locks up"
date: 2015-06-14
forum: Hardware
---

### Post by stefon on 2015-06-14
Hi @All...

I have a problem with the Samsung Notebook Samsung ATIV 9 Lite NP905S3G-K01. The system, or better, the GUI crashes and I have to reboot the computer. I can reproduce the crashes by starting for example two instances of cpuburn, two browser tabs with youtube and just waiting half an hour to one hour. 
Not the whole system crashes, but the GUI side. I know this, because I installed the openssh-server on the notebook and I observed the notebook via another computer. The SSH connection was usable after the GUI crash. Strangely enough I could not kill the lighdm process or restart it.  

The notebook has the AMD/ATI] Temash [Radeon HD 8250/8280G] graphic chip. I'm using ubuntu 15.04 and had the Radeon driver in use. But I had the same problems (have a look at the attachement for details). Now I'm using the fglrx drivers. 

The kernel logs this after system crash:
```

[ 7920.793691] INFO: task kwin_x11:1924 blocked for more than 120 seconds.
[ 7920.793706]       Tainted: P           OE  3.19.0-15-generic #15-Ubuntu[ 7920.793710] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 7920.793716] kwin_x11        D ffff88007b723c58     0  1924   1838 0x00000000
[ 7920.793728]  ffff88007b723c58 ffff880138d6e220 0000000000014200 ffff88007b723fd8
[ 7920.793736]  0000000000014200 ffff880085dc9d70 ffff880138d6e220 ffff88007b723c38
[ 7920.793744]  ffff880139371b60 7fffffffffffffff ffff880138d6e220 0000000000000002
[ 7920.793753] Call Trace:
[ 7920.793772]  [<ffffffff817c49c9>] schedule+0x29/0x70
[ 7920.793782]  [<ffffffff817c7fac>] schedule_timeout+0x20c/0x280
[ 7920.793966]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 7920.793982]  [<ffffffff8109ed3d>] ? ttwu_do_activate.constprop.94+0x5d/0x70
[ 7920.794109]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 7920.794121]  [<ffffffff817c6ef8>] __down+0x78/0xe0
[ 7920.794130]  [<ffffffff810bcd24>] down+0x44/0x50
[ 7920.794239]  [<ffffffffc03d000e>] KCL_SEMAPHORE_DownUninterruptible+0xe/0x10 [fglrx]
[ 7920.794368]  [<ffffffffc0412a9a>] firegl_cmmqs_CWDDE_32+0x16a/0x480 [fglrx]
[ 7920.794497]  [<ffffffffc041153e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
[ 7920.794506]  [<ffffffff8107e697>] ? capable+0x17/0x20
[ 7920.794633]  [<ffffffffc04114b0>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
[ 7920.794748]  [<ffffffffc03df698>] ? firegl_ioctl+0x1f8/0x260 [fglrx]
[ 7920.794856]  [<ffffffffc03cd1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
[ 7920.794864]  [<ffffffff81207b40>] ? do_vfs_ioctl+0x2e0/0x4e0
[ 7920.794871]  [<ffffffff817c445c>] ? __schedule+0x39c/0x8e0
[ 7920.794878]  [<ffffffff81207dc1>] ? SyS_ioctl+0x81/0xa0
[ 7920.794886]  [<ffffffff817c934d>] ? system_call_fastpath+0x16/0x1b
[ 7920.794903] INFO: task plasmashell:2025 blocked for more than 120 seconds.
[ 7920.794909]       Tainted: P           OE  3.19.0-15-generic #15-Ubuntu
[ 7920.794912] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 7920.794916] plasmashell     D ffff880072a7bc58     0  2025   1780 0x00000000
[ 7920.794925]  ffff880072a7bc58 ffff880085e65850 0000000000014200 ffff880072a7bfd8
[ 7920.794932]  0000000000014200 ffffffff81c1a580 ffff880085e65850 0000000000000296
[ 7920.794939]  ffff880139371b60 7fffffffffffffff ffff880085e65850 0000000000000002
[ 7920.794947] Call Trace:
[ 7920.794956]  [<ffffffff817c49c9>] schedule+0x29/0x70
[ 7920.794963]  [<ffffffff817c7fac>] schedule_timeout+0x20c/0x280
[ 7920.795090]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 7920.795279]  [<ffffffffc049c73e>] ? _ZN2OS20leaveCriticalSectionEPv+0x5e/0x70 [fglrx]
[ 7920.795405]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 7920.795416]  [<ffffffff817c6ef8>] __down+0x78/0xe0
[ 7920.795423]  [<ffffffff810bcd24>] down+0x44/0x50
[ 7920.795529]  [<ffffffffc03d000e>] KCL_SEMAPHORE_DownUninterruptible+0xe/0x10 [fglrx]
[ 7920.795678]  [<ffffffffc0412a9a>] firegl_cmmqs_CWDDE_32+0x16a/0x480 [fglrx]
[ 7920.795807]  [<ffffffffc041153e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
[ 7920.795816]  [<ffffffff8107e697>] ? capable+0x17/0x20
[ 7920.795944]  [<ffffffffc04114b0>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
[ 7920.796054]  [<ffffffffc03df698>] ? firegl_ioctl+0x1f8/0x260 [fglrx]
[ 7920.796143]  [<ffffffffc03cd1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
[ 7920.796158]  [<ffffffff81207b40>] ? do_vfs_ioctl+0x2e0/0x4e0
[ 7920.796168]  [<ffffffff810f2af6>] ? SyS_futex+0x76/0x170
[ 7920.796173]  [<ffffffff81207dc1>] ? SyS_ioctl+0x81/0xa0
[ 7920.796180]  [<ffffffff817c934d>] ? system_call_fastpath+0x16/0x1b
[ 7923.373498] <6>[fglrx] ASIC hang happened
[ 7923.373521] CPU: 3 PID: 891 Comm: Xorg Tainted: P           OE  3.19.0-15-generic #15-Ubuntu
[ 7923.373527] Hardware name: SAMSUNG ELECTRONICS CO., LTD. 905S3G/906S3G/915S3G/NP905S3G-K01DE, BIOS P03RBV.061.130704.FL 07/04/2013
[ 7923.373533]  00000001001d1285 ffff880139ac3bc8 ffffffff817c2205 00000000003dda45
[ 7923.373544]  0000000000000000 ffff880139ac3bd8 ffffffffc03d592e 00000001001d1284
[ 7923.373552]  ffffffffc03e517c 0000000000000000 ffffffffc04a551e ffff880139ac3c48
[ 7923.373561] Call Trace:
[ 7923.373580]  [<ffffffff817c2205>] dump_stack+0x45/0x57
[ 7923.373761]  [<ffffffffc03d592e>] KCL_DEBUG_OsDump+0xe/0x10 [fglrx]
[ 7923.373955]  [<ffffffffc03e517c>] firegl_hardwareHangRecovery+0x1c/0x30 [fglrx]
[ 7923.374159]  [<ffffffffc04a551e>] ? _ZN4Asic9WaitUntil15ResetASICIfHungEv+0x1e/0x30 [fglrx]
[ 7923.374354]  [<ffffffffc04a5489>] ? _ZN4Asic9WaitUntil15WaitForCompleteEv+0xb9/0x130 [fglrx]
[ 7923.374545]  [<ffffffffc04a1d95>] ? _ZN4Asic19PM4ElapsedTimeStampEj14_LARGE_INTEGER12_QS_CP_RING_+0xd5/0x160 [fglrx]
[ 7923.374756]  [<ffffffffc04c0332>] ? _ZNK6AsicCI19insertEventWriteEOPE12_QS_CP_RING_RPjjRmR14_LARGE_INTEGERj+0xb2/0x170 [fglrx]
[ 7923.374953]  [<ffffffffc04aa059>] ? _ZN15ExecutableUnits35flush_all_and_invalidate_HDP_cachesE12_QS_CP_RING_+0xc9/0xf0 [fglrx]
[ 7923.375149]  [<ffffffffc04a9f3e>] ? _ZN15ExecutableUnits8ringIdleE12_QS_CP_RING_+0x5e/0xb0 [fglrx]
[ 7923.375318]  [<ffffffffc0480b0d>] ? _Z17uQSPm4SynchronizemP18_QS_SYNC_PACKET_IN+0x4d/0x50 [fglrx]
[ 7923.375485]  [<ffffffffc047b808>] ? _Z8uCWDDEQCmjjPvjS_+0x648/0x1240 [fglrx]
[ 7923.375648]  [<ffffffffc0471a6a>] ? CMMQS_uCWDDEQC+0xa/0x10 [fglrx]
[ 7923.375778]  [<ffffffffc0412c9f>] ? firegl_cmmqs_CWDDE_32+0x36f/0x480 [fglrx]
[ 7923.375908]  [<ffffffffc041153e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
[ 7923.375919]  [<ffffffff8107e697>] ? capable+0x17/0x20
[ 7923.376048]  [<ffffffffc04114b0>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
[ 7923.376165]  [<ffffffffc03df698>] ? firegl_ioctl+0x1f8/0x260 [fglrx]
[ 7923.376175]  [<ffffffff810dee1c>] ? __hrtimer_start_range_ns+0x2dc/0x410
[ 7923.376285]  [<ffffffffc03cd1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
[ 7923.376294]  [<ffffffff81207b40>] ? do_vfs_ioctl+0x2e0/0x4e0
[ 7923.376306]  [<ffffffff816a43e2>] ? __sys_recvmsg+0x42/0x80
[ 7923.376313]  [<ffffffff81207dc1>] ? SyS_ioctl+0x81/0xa0
[ 7923.376323]  [<ffffffff817c934d>] ? system_call_fastpath+0x16/0x1b
[ 7923.376333] pubdev:0xffffffffc0ecab80, num of device:1 , name:fglrx, major 15, minor 20. 
[ 7923.376340] device 0 : 0xffff880138804000 .
[ 7923.376345] Asic ID:0x983d, revision:0x82, MMIOReg:0xffffc90011280000.
[ 7923.376355] FB phys addr: 0xc0000000, MC :0xf00000000, Total FB size :0x20000000.
[ 7923.376362] gart table MC:0xf0fba8000, Physical:0xcfba8000, size:0x457000.
[ 7923.376368] mc_node :FB, total 1 zones
[ 7923.376374]     MC start:0xf00000000, Physical:0xc0000000, size:0x10000000.
[ 7923.376380]     Mapped heap -- Offset:0x0, size:0xfba4000, reference count:46, mapping count:0,
[ 7923.376387]     Mapped heap -- Offset:0x0, size:0x1000000, reference count:1, mapping count:0,
[ 7923.376393]     Mapped heap -- Offset:0xfba4000, size:0x4000, reference count:1, mapping count:0,
[ 7923.376399]     Mapped heap -- Offset:0xfba8000, size:0x458000, reference count:1, mapping count:0,
[ 7923.376407] mc_node :INV_FB, total 1 zones
[ 7923.376412]     MC start:0xf10000000, Physical:0xd0000000, size:0x10000000.
[ 7923.376418]     Mapped heap -- Offset:0xffdd000, size:0x23000, reference count:1, mapping count:0,
[ 7923.376422] mc_node :GART_USWC, total 4 zones
[ 7923.376427]     MC start:0xff978d0000, Physical:0x0, size:0x63000000.
[ 7923.376434]     Mapped heap -- Offset:0xf830000, size:0x1800000, reference count:2, mapping count:0,
[ 7923.376441]     Mapped heap -- Offset:0xe030000, size:0x1800000, reference count:2, mapping count:0,
[ 7923.376447]     Mapped heap -- Offset:0xc830000, size:0x1800000, reference count:2, mapping count:0,
[ 7923.376452]     Mapped heap -- Offset:0xb030000, size:0x1800000, reference count:2, mapping count:0,
[ 7923.376458]     Mapped heap -- Offset:0x9830000, size:0x1800000, reference count:2, mapping count:0,
[ 7923.376464]     Mapped heap -- Offset:0x8030000, size:0x1800000, reference count:2, mapping count:0,
[ 7923.376470]     Mapped heap -- Offset:0x6830000, size:0x1800000, reference count:2, mapping count:0,
[ 7923.376476]     Mapped heap -- Offset:0x2030000, size:0x1800000, reference count:2, mapping count:0,
[ 7923.376481]     Mapped heap -- Offset:0x5030000, size:0x1800000, reference count:2, mapping count:0,
[ 7923.376488]     Mapped heap -- Offset:0x3830000, size:0x1800000, reference count:2, mapping count:0,
[ 7923.376493]     Mapped heap -- Offset:0x30000, size:0x2000000, reference count:21, mapping count:0,
[ 7923.376499] mc_node :GART_CACHEABLE, total 4 zones
[ 7923.376504]     MC start:0xff70400000, Physical:0x0, size:0x274d0000.
[ 7923.376510]     Mapped heap -- Offset:0x6800000, size:0x500000, reference count:2, mapping count:0,
[ 7923.376516]     Mapped heap -- Offset:0x1200000, size:0x100000, reference count:1, mapping count:0,
[ 7923.376522]     Mapped heap -- Offset:0x5f00000, size:0x400000, reference count:1, mapping count:0,
[ 7923.376528]     Mapped heap -- Offset:0x5b00000, size:0x400000, reference count:2, mapping count:0,
[ 7923.376534]     Mapped heap -- Offset:0x5400000, size:0x500000, reference count:1, mapping count:0,
[ 7923.376540]     Mapped heap -- Offset:0x4f00000, size:0x500000, reference count:2, mapping count:0,
[ 7923.376545]     Mapped heap -- Offset:0x4800000, size:0x400000, reference count:1, mapping count:0,
[ 7923.376551]     Mapped heap -- Offset:0x4300000, size:0x500000, reference count:3, mapping count:0,
[ 7923.376557]     Mapped heap -- Offset:0x3e00000, size:0x500000, reference count:7, mapping count:0,
[ 7923.376562]     Mapped heap -- Offset:0x3900000, size:0x500000, reference count:2, mapping count:0,
[ 7923.376568]     Mapped heap -- Offset:0x1d00000, size:0x200000, reference count:2, mapping count:0,
[ 7923.376574]     Mapped heap -- Offset:0x1100000, size:0x100000, reference count:4, mapping count:0,
[ 7923.376579]     Mapped heap -- Offset:0x3400000, size:0x500000, reference count:5, mapping count:0,
[ 7923.376585]     Mapped heap -- Offset:0x2f00000, size:0x500000, reference count:2, mapping count:0,
[ 7923.376591]     Mapped heap -- Offset:0x2a00000, size:0x500000, reference count:2, mapping count:0,
[ 7923.376596]     Mapped heap -- Offset:0x2500000, size:0x500000, reference count:3, mapping count:0,
[ 7923.376602]     Mapped heap -- Offset:0x2000000, size:0x500000, reference count:2, mapping count:0,
[ 7923.376607]     Mapped heap -- Offset:0x1800000, size:0x500000, reference count:2, mapping count:0,
[ 7923.376613]     Mapped heap -- Offset:0x1300000, size:0x500000, reference count:2, mapping count:0,
[ 7923.376619]     Mapped heap -- Offset:0xc00000, size:0x500000, reference count:5, mapping count:0,
[ 7923.376626]     Mapped heap -- Offset:0x700000, size:0x500000, reference count:2, mapping count:0,
[ 7923.376632]     Mapped heap -- Offset:0x200000, size:0x500000, reference count:4, mapping count:0,
[ 7923.376638]     Mapped heap -- Offset:0x0, size:0x200000, reference count:15, mapping count:0,
[ 7923.376643]     Mapped heap -- Offset:0xef000, size:0x11000, reference count:1, mapping count:0,
[ 7923.376648] mc_node :PEER_FB_GART, total 1 zones
[ 7923.376653]     MC start:0xfffa8d0000, Physical:0x0, size:0x1000.
[ 7923.376661] GRBM : 0xa0003028, SRBM : 0x20000a40 .
[ 7923.376669] CP_RB_BASE : 0xff979000, CP_RB_RPTR : 0x2e9a8 , CP_RB_WPTR :0x2eb40.
[ 7923.376676] CP_IB1_BUFSZ:0x76, CP_IB1_BASE_HI:0xff, CP_IB1_BASE_LO:0x984e2000.
[ 7923.376681] last submit IB buffer -- MC :0xff984e2000,phys:0x92ee1000.
[ 7923.376689] Dump the trace queue.
[ 7923.376693] End of dump
[ 8040.801628] INFO: task kwin_x11:1924 blocked for more than 120 seconds.
[ 8040.801643]       Tainted: P           OE  3.19.0-15-generic #15-Ubuntu
[ 8040.801648] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8040.801653] kwin_x11        D ffff88007b723c58     0  1924   1838 0x00000000
[ 8040.801665]  ffff88007b723c58 ffff880138d6e220 0000000000014200 ffff88007b723fd8
[ 8040.801673]  0000000000014200 ffff880085dc9d70 ffff880138d6e220 ffff88007b723c38
[ 8040.801680]  ffff880139371b60 7fffffffffffffff ffff880138d6e220 0000000000000002
[ 8040.801688] Call Trace:
[ 8040.801708]  [<ffffffff817c49c9>] schedule+0x29/0x70
[ 8040.801718]  [<ffffffff817c7fac>] schedule_timeout+0x20c/0x280
[ 8040.801904]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8040.801920]  [<ffffffff8109ed3d>] ? ttwu_do_activate.constprop.94+0x5d/0x70
[ 8040.802047]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8040.802058]  [<ffffffff817c6ef8>] __down+0x78/0xe0
[ 8040.802068]  [<ffffffff810bcd24>] down+0x44/0x50
[ 8040.802176]  [<ffffffffc03d000e>] KCL_SEMAPHORE_DownUninterruptible+0xe/0x10 [fglrx]
[ 8040.802305]  [<ffffffffc0412a9a>] firegl_cmmqs_CWDDE_32+0x16a/0x480 [fglrx]
[ 8040.802435]  [<ffffffffc041153e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
[ 8040.802444]  [<ffffffff8107e697>] ? capable+0x17/0x20
[ 8040.802571]  [<ffffffffc04114b0>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
[ 8040.802686]  [<ffffffffc03df698>] ? firegl_ioctl+0x1f8/0x260 [fglrx]
[ 8040.802793]  [<ffffffffc03cd1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
[ 8040.802802]  [<ffffffff81207b40>] ? do_vfs_ioctl+0x2e0/0x4e0
[ 8040.802809]  [<ffffffff817c445c>] ? __schedule+0x39c/0x8e0
[ 8040.802816]  [<ffffffff81207dc1>] ? SyS_ioctl+0x81/0xa0
[ 8040.802824]  [<ffffffff817c934d>] ? system_call_fastpath+0x16/0x1b
[ 8040.802841] INFO: task plasmashell:2025 blocked for more than 120 seconds.
[ 8040.802846]       Tainted: P           OE  3.19.0-15-generic #15-Ubuntu
[ 8040.802849] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8040.802853] plasmashell     D ffff880072a7bc58     0  2025   1780 0x00000000
[ 8040.802861]  ffff880072a7bc58 ffff880085e65850 0000000000014200 ffff880072a7bfd8
[ 8040.802868]  0000000000014200 ffffffff81c1a580 ffff880085e65850 0000000000000296
[ 8040.802875]  ffff880139371b60 7fffffffffffffff ffff880085e65850 0000000000000002
[ 8040.802882] Call Trace:
[ 8040.802890]  [<ffffffff817c49c9>] schedule+0x29/0x70
[ 8040.802898]  [<ffffffff817c7fac>] schedule_timeout+0x20c/0x280
[ 8040.803023]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8040.803210]  [<ffffffffc049c73e>] ? _ZN2OS20leaveCriticalSectionEPv+0x5e/0x70 [fglrx]
[ 8040.803336]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8040.803347]  [<ffffffff817c6ef8>] __down+0x78/0xe0
[ 8040.803354]  [<ffffffff810bcd24>] down+0x44/0x50
[ 8040.803462]  [<ffffffffc03d000e>] KCL_SEMAPHORE_DownUninterruptible+0xe/0x10 [fglrx]
[ 8040.803576]  [<ffffffffc0412a9a>] firegl_cmmqs_CWDDE_32+0x16a/0x480 [fglrx]
[ 8040.803683]  [<ffffffffc041153e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
[ 8040.803689]  [<ffffffff8107e697>] ? capable+0x17/0x20
[ 8040.803795]  [<ffffffffc04114b0>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
[ 8040.803890]  [<ffffffffc03df698>] ? firegl_ioctl+0x1f8/0x260 [fglrx]
[ 8040.803979]  [<ffffffffc03cd1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
[ 8040.803985]  [<ffffffff81207b40>] ? do_vfs_ioctl+0x2e0/0x4e0
[ 8040.803994]  [<ffffffff810f2af6>] ? SyS_futex+0x76/0x170
[ 8040.803999]  [<ffffffff81207dc1>] ? SyS_ioctl+0x81/0xa0
[ 8040.804006]  [<ffffffff817c934d>] ? system_call_fastpath+0x16/0x1b
[ 8160.809547] INFO: task kwin_x11:1924 blocked for more than 120 seconds.
[ 8160.809561]       Tainted: P           OE  3.19.0-15-generic #15-Ubuntu
[ 8160.809565] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8160.809569] kwin_x11        D ffff88007b723c58     0  1924   1838 0x00000000
[ 8160.809580]  ffff88007b723c58 ffff880138d6e220 0000000000014200 ffff88007b723fd8
[ 8160.809587]  0000000000014200 ffff880085dc9d70 ffff880138d6e220 ffff88007b723c38
[ 8160.809594]  ffff880139371b60 7fffffffffffffff ffff880138d6e220 0000000000000002
[ 8160.809601] Call Trace:
[ 8160.809619]  [<ffffffff817c49c9>] schedule+0x29/0x70
[ 8160.809627]  [<ffffffff817c7fac>] schedule_timeout+0x20c/0x280
[ 8160.809790]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8160.809803]  [<ffffffff8109ed3d>] ? ttwu_do_activate.constprop.94+0x5d/0x70
[ 8160.809908]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8160.809918]  [<ffffffff817c6ef8>] __down+0x78/0xe0
[ 8160.809926]  [<ffffffff810bcd24>] down+0x44/0x50
[ 8160.810016]  [<ffffffffc03d000e>] KCL_SEMAPHORE_DownUninterruptible+0xe/0x10 [fglrx]
[ 8160.810124]  [<ffffffffc0412a9a>] firegl_cmmqs_CWDDE_32+0x16a/0x480 [fglrx]
[ 8160.810232]  [<ffffffffc041153e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
[ 8160.810240]  [<ffffffff8107e697>] ? capable+0x17/0x20
[ 8160.810346]  [<ffffffffc04114b0>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
[ 8160.810442]  [<ffffffffc03df698>] ? firegl_ioctl+0x1f8/0x260 [fglrx]
[ 8160.810531]  [<ffffffffc03cd1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
[ 8160.810538]  [<ffffffff81207b40>] ? do_vfs_ioctl+0x2e0/0x4e0
[ 8160.810544]  [<ffffffff817c445c>] ? __schedule+0x39c/0x8e0
[ 8160.810550]  [<ffffffff81207dc1>] ? SyS_ioctl+0x81/0xa0
[ 8160.810557]  [<ffffffff817c934d>] ? system_call_fastpath+0x16/0x1b
[ 8160.810572] INFO: task plasmashell:2025 blocked for more than 120 seconds.
[ 8160.810576]       Tainted: P           OE  3.19.0-15-generic #15-Ubuntu
[ 8160.810579] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8160.810582] plasmashell     D ffff880072a7bc58     0  2025   1780 0x00000000
[ 8160.810589]  ffff880072a7bc58 ffff880085e65850 0000000000014200 ffff880072a7bfd8
[ 8160.810595]  0000000000014200 ffffffff81c1a580 ffff880085e65850 0000000000000296
[ 8160.810601]  ffff880139371b60 7fffffffffffffff ffff880085e65850 0000000000000002
[ 8160.810607] Call Trace:
[ 8160.810614]  [<ffffffff817c49c9>] schedule+0x29/0x70
[ 8160.810620]  [<ffffffff817c7fac>] schedule_timeout+0x20c/0x280
[ 8160.810725]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8160.810882]  [<ffffffffc049c73e>] ? _ZN2OS20leaveCriticalSectionEPv+0x5e/0x70 [fglrx]
[ 8160.810987]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8160.810996]  [<ffffffff817c6ef8>] __down+0x78/0xe0
[ 8160.811002]  [<ffffffff810bcd24>] down+0x44/0x50
[ 8160.811091]  [<ffffffffc03d000e>] KCL_SEMAPHORE_DownUninterruptible+0xe/0x10 [fglrx]
[ 8160.811197]  [<ffffffffc0412a9a>] firegl_cmmqs_CWDDE_32+0x16a/0x480 [fglrx]
[ 8160.811304]  [<ffffffffc041153e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
[ 8160.811310]  [<ffffffff8107e697>] ? capable+0x17/0x20
[ 8160.811416]  [<ffffffffc04114b0>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
[ 8160.811511]  [<ffffffffc03df698>] ? firegl_ioctl+0x1f8/0x260 [fglrx]
[ 8160.811600]  [<ffffffffc03cd1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
[ 8160.811606]  [<ffffffff81207b40>] ? do_vfs_ioctl+0x2e0/0x4e0
[ 8160.811615]  [<ffffffff810f2af6>] ? SyS_futex+0x76/0x170
[ 8160.811620]  [<ffffffff81207dc1>] ? SyS_ioctl+0x81/0xa0
[ 8160.811627]  [<ffffffff817c934d>] ? system_call_fastpath+0x16/0x1b
[ 8280.817455] INFO: task kwin_x11:1924 blocked for more than 120 seconds.
[ 8280.817469]       Tainted: P           OE  3.19.0-15-generic #15-Ubuntu
[ 8280.817472] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8280.817477] kwin_x11        D ffff88007b723c58     0  1924   1838 0x00000000
[ 8280.817487]  ffff88007b723c58 ffff880138d6e220 0000000000014200 ffff88007b723fd8
[ 8280.817495]  0000000000014200 ffff880085dc9d70 ffff880138d6e220 ffff88007b723c38
[ 8280.817501]  ffff880139371b60 7fffffffffffffff ffff880138d6e220 0000000000000002
[ 8280.817508] Call Trace:
[ 8280.817526]  [<ffffffff817c49c9>] schedule+0x29/0x70
[ 8280.817534]  [<ffffffff817c7fac>] schedule_timeout+0x20c/0x280
[ 8280.817700]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8280.817715]  [<ffffffff8109ed3d>] ? ttwu_do_activate.constprop.94+0x5d/0x70
[ 8280.817820]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8280.817829]  [<ffffffff817c6ef8>] __down+0x78/0xe0
[ 8280.817837]  [<ffffffff810bcd24>] down+0x44/0x50
[ 8280.817928]  [<ffffffffc03d000e>] KCL_SEMAPHORE_DownUninterruptible+0xe/0x10 [fglrx]
[ 8280.818036]  [<ffffffffc0412a9a>] firegl_cmmqs_CWDDE_32+0x16a/0x480 [fglrx]
[ 8280.818144]  [<ffffffffc041153e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
[ 8280.818152]  [<ffffffff8107e697>] ? capable+0x17/0x20
[ 8280.818259]  [<ffffffffc04114b0>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
[ 8280.818355]  [<ffffffffc03df698>] ? firegl_ioctl+0x1f8/0x260 [fglrx]
[ 8280.818446]  [<ffffffffc03cd1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
[ 8280.818455]  [<ffffffff81207b40>] ? do_vfs_ioctl+0x2e0/0x4e0
[ 8280.818461]  [<ffffffff817c445c>] ? __schedule+0x39c/0x8e0
[ 8280.818467]  [<ffffffff81207dc1>] ? SyS_ioctl+0x81/0xa0
[ 8280.818474]  [<ffffffff817c934d>] ? system_call_fastpath+0x16/0x1b
[ 8280.818490] INFO: task plasmashell:2025 blocked for more than 120 seconds.
[ 8280.818494]       Tainted: P           OE  3.19.0-15-generic #15-Ubuntu
[ 8280.818497] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8280.818500] plasmashell     D ffff880072a7bc58     0  2025   1780 0x00000000
[ 8280.818507]  ffff880072a7bc58 ffff880085e65850 0000000000014200 ffff880072a7bfd8
[ 8280.818514]  0000000000014200 ffffffff81c1a580 ffff880085e65850 0000000000000296
[ 8280.818520]  ffff880139371b60 7fffffffffffffff ffff880085e65850 0000000000000002
[ 8280.818526] Call Trace:
[ 8280.818533]  [<ffffffff817c49c9>] schedule+0x29/0x70
[ 8280.818539]  [<ffffffff817c7fac>] schedule_timeout+0x20c/0x280
[ 8280.818647]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8280.818805]  [<ffffffffc049c73e>] ? _ZN2OS20leaveCriticalSectionEPv+0x5e/0x70 [fglrx]
[ 8280.818912]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8280.818921]  [<ffffffff817c6ef8>] __down+0x78/0xe0
[ 8280.818927]  [<ffffffff810bcd24>] down+0x44/0x50
[ 8280.819016]  [<ffffffffc03d000e>] KCL_SEMAPHORE_DownUninterruptible+0xe/0x10 [fglrx]
[ 8280.819124]  [<ffffffffc0412a9a>] firegl_cmmqs_CWDDE_32+0x16a/0x480 [fglrx]
[ 8280.819231]  [<ffffffffc041153e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
[ 8280.819239]  [<ffffffff8107e697>] ? capable+0x17/0x20
[ 8280.819345]  [<ffffffffc04114b0>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
[ 8280.819441]  [<ffffffffc03df698>] ? firegl_ioctl+0x1f8/0x260 [fglrx]
[ 8280.819548]  [<ffffffffc03cd1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
[ 8280.819554]  [<ffffffff81207b40>] ? do_vfs_ioctl+0x2e0/0x4e0
[ 8280.819563]  [<ffffffff810f2af6>] ? SyS_futex+0x76/0x170
[ 8280.819569]  [<ffffffff81207dc1>] ? SyS_ioctl+0x81/0xa0
[ 8280.819576]  [<ffffffff817c934d>] ? system_call_fastpath+0x16/0x1b
[ 8400.825427] INFO: task kwin_x11:1924 blocked for more than 120 seconds.
[ 8400.825441]       Tainted: P           OE  3.19.0-15-generic #15-Ubuntu
[ 8400.825445] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8400.825449] kwin_x11        D ffff88007b723c58     0  1924   1838 0x00000000
[ 8400.825459]  ffff88007b723c58 ffff880138d6e220 0000000000014200 ffff88007b723fd8
[ 8400.825466]  0000000000014200 ffff880085dc9d70 ffff880138d6e220 ffff88007b723c38
[ 8400.825472]  ffff880139371b60 7fffffffffffffff ffff880138d6e220 0000000000000002
[ 8400.825479] Call Trace:
[ 8400.825497]  [<ffffffff817c49c9>] schedule+0x29/0x70
[ 8400.825505]  [<ffffffff817c7fac>] schedule_timeout+0x20c/0x280
[ 8400.825663]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8400.825677]  [<ffffffff8109ed3d>] ? ttwu_do_activate.constprop.94+0x5d/0x70
[ 8400.825782]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8400.825792]  [<ffffffff817c6ef8>] __down+0x78/0xe0
[ 8400.825800]  [<ffffffff810bcd24>] down+0x44/0x50
[ 8400.825890]  [<ffffffffc03d000e>] KCL_SEMAPHORE_DownUninterruptible+0xe/0x10 [fglrx]
[ 8400.825998]  [<ffffffffc0412a9a>] firegl_cmmqs_CWDDE_32+0x16a/0x480 [fglrx]
[ 8400.826105]  [<ffffffffc041153e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
[ 8400.826113]  [<ffffffff8107e697>] ? capable+0x17/0x20
[ 8400.826219]  [<ffffffffc04114b0>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
[ 8400.826314]  [<ffffffffc03df698>] ? firegl_ioctl+0x1f8/0x260 [fglrx]
[ 8400.826403]  [<ffffffffc03cd1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
[ 8400.826411]  [<ffffffff81207b40>] ? do_vfs_ioctl+0x2e0/0x4e0
[ 8400.826417]  [<ffffffff817c445c>] ? __schedule+0x39c/0x8e0
[ 8400.826422]  [<ffffffff81207dc1>] ? SyS_ioctl+0x81/0xa0
[ 8400.826430]  [<ffffffff817c934d>] ? system_call_fastpath+0x16/0x1b
[ 8400.826444] INFO: task plasmashell:2025 blocked for more than 120 seconds.
[ 8400.826448]       Tainted: P           OE  3.19.0-15-generic #15-Ubuntu
[ 8400.826451] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8400.826454] plasmashell     D ffff880072a7bc58     0  2025   1780 0x00000000
[ 8400.826461]  ffff880072a7bc58 ffff880085e65850 0000000000014200 ffff880072a7bfd8
[ 8400.826467]  0000000000014200 ffffffff81c1a580 ffff880085e65850 0000000000000296
[ 8400.826473]  ffff880139371b60 7fffffffffffffff ffff880085e65850 0000000000000002
[ 8400.826479] Call Trace:
[ 8400.826486]  [<ffffffff817c49c9>] schedule+0x29/0x70
[ 8400.826492]  [<ffffffff817c7fac>] schedule_timeout+0x20c/0x280
[ 8400.826597]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8400.826753]  [<ffffffffc049c73e>] ? _ZN2OS20leaveCriticalSectionEPv+0x5e/0x70 [fglrx]
[ 8400.826857]  [<ffffffffc040a0e2>] ? firegl_trace+0x72/0x1e0 [fglrx]
[ 8400.826866]  [<ffffffff817c6ef8>] __down+0x78/0xe0
[ 8400.826872]  [<ffffffff810bcd24>] down+0x44/0x50
[ 8400.826961]  [<ffffffffc03d000e>] KCL_SEMAPHORE_DownUninterruptible+0xe/0x10 [fglrx]
[ 8400.827098]  [<ffffffffc0412a9a>] firegl_cmmqs_CWDDE_32+0x16a/0x480 [fglrx]
[ 8400.827225]  [<ffffffffc041153e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
[ 8400.827233]  [<ffffffff8107e697>] ? capable+0x17/0x20
[ 8400.827359]  [<ffffffffc04114b0>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
[ 8400.827473]  [<ffffffffc03df698>] ? firegl_ioctl+0x1f8/0x260 [fglrx]
[ 8400.827580]  [<ffffffffc03cd1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
[ 8400.827587]  [<ffffffff81207b40>] ? do_vfs_ioctl+0x2e0/0x4e0
[ 8400.827596]  [<ffffffff810f2af6>] ? SyS_futex+0x76/0x170
[ 8400.827602]  [<ffffffff81207dc1>] ? SyS_ioctl+0x81/0xa0
[ 8400.827611]  [<ffffffff817c934d>] ? system_call_fastpath+0x16/0x1b
[FONT=Verdana]
```

If somebody has an idea or can help me to stabilize the system I would be very grateful..
If some information is missing, I would be happy to provide it if i can

your
stefon [/FONT]

---

