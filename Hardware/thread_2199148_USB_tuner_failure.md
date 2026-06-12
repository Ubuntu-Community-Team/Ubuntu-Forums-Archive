---
title: "USB tuner failure?"
date: 2014-01-12
forum: Hardware
---

### Post by mma8x on 2014-01-12
Kubuntu version 13.10, have been struggling with mythtv (0.27) and tuner cards since my ATI wonder crapped out.  I'm currently trying to use 2 hauppauge HVR-850 usb tuners.  I can get them intermittently working, but they seem to fail randomly.  Here's a recent syslog output:

```
Jan 12 11:07:09 MythBox whoopsie[1191]: online
Jan 12 11:07:10 MythBox whoopsie[1191]: online
Jan 12 11:07:11 MythBox kernel: [66933.276832] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
Jan 12 11:07:11 MythBox kernel: [66933.276910] xc5000: firmware read 12401 bytes.
Jan 12 11:07:11 MythBox kernel: [66933.276912] xc5000: firmware uploading...
Jan 12 11:07:14 MythBox kernel: [66936.218669] xc5000: firmware upload complete...
Jan 12 11:07:54 MythBox kernel: [66975.656991] DVBRead: page allocation failure: order:4, mode:0x10c0d0
Jan 12 11:07:54 MythBox kernel: [66975.656999] CPU: 0 PID: 10964 Comm: DVBRead Not tainted 3.11.0-15-generic #23-Ubuntu
Jan 12 11:07:54 MythBox kernel: [66975.657001] Hardware name: ECS H55H-3.8L/H55H-3.8L, BIOS 080015  05/21/2010
Jan 12 11:07:54 MythBox kernel: [66975.657003]  0000000000000000 ffff88004ec75a30 ffffffff816e7335 000000000010c0d0
Jan 12 11:07:54 MythBox kernel: [66975.657007]  ffff88004ec75ab8 ffffffff811442e0 00000000ffffffff ffff88013bff9b38
Jan 12 11:07:54 MythBox kernel: [66975.657009]  000000000000000e ffff88004ec75a88 ffffffff00000040 0000000000000003
Jan 12 11:07:54 MythBox kernel: [66975.657012] Call Trace:
Jan 12 11:07:54 MythBox kernel: [66975.657022]  [<ffffffff816e7335>] dump_stack+0x45/0x56
Jan 12 11:07:54 MythBox kernel: [66975.657028]  [<ffffffff811442e0>] warn_alloc_failed+0xf0/0x140
Jan 12 11:07:54 MythBox kernel: [66975.657032]  [<ffffffff81148215>] __alloc_pages_nodemask+0x725/0x920
Jan 12 11:07:54 MythBox kernel: [66975.657037]  [<ffffffff81183c69>] alloc_pages_current+0xa9/0x160
Jan 12 11:07:54 MythBox kernel: [66975.657040]  [<ffffffff811433fe>] __get_free_pages+0xe/0x50
Jan 12 11:07:54 MythBox kernel: [66975.657045]  [<ffffffff8118ce1e>] kmalloc_order_trace+0x2e/0xa0
Jan 12 11:07:54 MythBox kernel: [66975.657056]  [<ffffffffa035e72f>] start_urb_transfer+0x6f/0x1d0 [au0828]
Jan 12 11:07:54 MythBox kernel: [66975.657061]  [<ffffffffa035e955>] au0828_dvb_start_feed+0xc5/0xf0 [au0828]
Jan 12 11:07:54 MythBox kernel: [66975.657072]  [<ffffffffa037fbe6>] dmx_ts_feed_start_filtering+0x66/0x110 [dvb_core]
Jan 12 11:07:54 MythBox kernel: [66975.657077]  [<ffffffffa037c18e>] dvb_dmxdev_start_feed.isra.0+0xae/0x100 [dvb_core]
Jan 12 11:07:54 MythBox kernel: [66975.657083]  [<ffffffffa037d3b0>] dvb_dmxdev_filter_start+0x90/0x3e0 [dvb_core]
Jan 12 11:07:54 MythBox kernel: [66975.657088]  [<ffffffffa037dc38>] dvb_demux_do_ioctl+0x538/0x690 [dvb_core]
Jan 12 11:07:54 MythBox kernel: [66975.657093]  [<ffffffffa037ba85>] dvb_usercopy+0x115/0x190 [dvb_core]
Jan 12 11:07:54 MythBox kernel: [66975.657098]  [<ffffffffa037d700>] ? dvb_dmxdev_filter_start+0x3e0/0x3e0 [dvb_core]
Jan 12 11:07:54 MythBox kernel: [66975.657102]  [<ffffffff811b719a>] ? do_filp_open+0x3a/0x90
Jan 12 11:07:54 MythBox kernel: [66975.657106]  [<ffffffffa037bdd5>] dvb_demux_ioctl+0x15/0x20 [dvb_core]
Jan 12 11:07:54 MythBox kernel: [66975.657109]  [<ffffffff811b9045>] do_vfs_ioctl+0x2e5/0x4d0
Jan 12 11:07:54 MythBox kernel: [66975.657112]  [<ffffffff811b63b2>] ? final_putname+0x22/0x50
Jan 12 11:07:54 MythBox whoopsie[1191]: online
Jan 12 11:07:54 MythBox kernel: [66975.657114]  [<ffffffff811b65b9>] ? putname+0x29/0x40
Jan 12 11:07:54 MythBox kernel: [66975.657118]  [<ffffffff811a649b>] ? do_sys_open+0x1bb/0x270
Jan 12 11:07:54 MythBox kernel: [66975.657120]  [<ffffffff811b92b1>] SyS_ioctl+0x81/0xa0
Jan 12 11:07:54 MythBox kernel: [66975.657125]  [<ffffffff816f721d>] system_call_fastpath+0x1a/0x1f
Jan 12 11:07:54 MythBox kernel: [66975.657127] Mem-Info:
Jan 12 11:07:54 MythBox kernel: [66975.657129] Node 0 DMA per-cpu:
Jan 12 11:07:54 MythBox kernel: [66975.657131] CPU    0: hi:    0, btch:   1 usd:   0
Jan 12 11:07:54 MythBox kernel: [66975.657133] CPU    1: hi:    0, btch:   1 usd:   0
Jan 12 11:07:54 MythBox kernel: [66975.657134] CPU    2: hi:    0, btch:   1 usd:   0
Jan 12 11:07:54 MythBox kernel: [66975.657136] CPU    3: hi:    0, btch:   1 usd:   0
Jan 12 11:07:54 MythBox kernel: [66975.657137] Node 0 DMA32 per-cpu:
Jan 12 11:07:54 MythBox kernel: [66975.657140] CPU    0: hi:  186, btch:  31 usd:   0
Jan 12 11:07:54 MythBox kernel: [66975.657141] CPU    1: hi:  186, btch:  31 usd:   0
Jan 12 11:07:54 MythBox kernel: [66975.657143] CPU    2: hi:  186, btch:  31 usd:   0
Jan 12 11:07:54 MythBox kernel: [66975.657145] CPU    3: hi:  186, btch:  31 usd:   0
Jan 12 11:07:54 MythBox kernel: [66975.657146] Node 0 Normal per-cpu:
Jan 12 11:07:54 MythBox kernel: [66975.657147] CPU    0: hi:  186, btch:  31 usd:   0
Jan 12 11:07:54 MythBox kernel: [66975.657149] CPU    1: hi:  186, btch:  31 usd:   0
Jan 12 11:07:54 MythBox kernel: [66975.657150] CPU    2: hi:  186, btch:  31 usd:   0
Jan 12 11:07:54 MythBox kernel: [66975.657152] CPU    3: hi:  186, btch:  31 usd:   0
Jan 12 11:07:54 MythBox kernel: [66975.657155] active_anon:117656 inactive_anon:119436 isolated_anon:0
Jan 12 11:07:54 MythBox kernel: [66975.657155]  active_file:179011 inactive_file:396471 isolated_file:0
Jan 12 11:07:54 MythBox kernel: [66975.657155]  unevictable:0 dirty:2315 writeback:0 unstable:0
Jan 12 11:07:54 MythBox kernel: [66975.657155]  free:63183 slab_reclaimable:31175 slab_unreclaimable:9432
Jan 12 11:07:54 MythBox kernel: [66975.657155]  mapped:56418 shmem:37835 pagetables:12828 bounce:0
Jan 12 11:07:54 MythBox kernel: [66975.657155]  free_cma:0
Jan 12 11:07:54 MythBox kernel: [66975.657159] Node 0 DMA free:14996kB min:284kB low:352kB high:424kB active_anon:32kB inactive_anon:164kB active_file:4kB inactive_file:12kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15992kB managed:15908kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:124kB slab_unreclaimable:72kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Jan 12 11:07:54 MythBox kernel: [66975.657165] lowmem_reserve[]: 0 2775 3672 3672
Jan 12 11:07:54 MythBox kernel: [66975.657169] Node 0 DMA32 free:200360kB min:50868kB low:63584kB high:76300kB active_anon:291356kB inactive_anon:273052kB active_file:535536kB inactive_file:1399832kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:2924032kB managed:2845452kB mlocked:0kB dirty:7672kB writeback:0kB mapped:110052kB shmem:124148kB slab_reclaimable:94140kB slab_unreclaimable:12324kB kernel_stack:2144kB pagetables:30220kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Jan 12 11:07:54 MythBox kernel: [66975.657174] lowmem_reserve[]: 0 0 896 896
Jan 12 11:07:54 MythBox kernel: [66975.657177] Node 0 Normal free:37376kB min:16424kB low:20528kB high:24636kB active_anon:179236kB inactive_anon:204528kB active_file:180504kB inactive_file:186040kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:983040kB managed:917860kB mlocked:0kB dirty:1588kB writeback:0kB mapped:115620kB shmem:27192kB slab_reclaimable:30436kB slab_unreclaimable:25332kB kernel_stack:3184kB pagetables:21092kB unstable:0kB bounce:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Jan 12 11:07:54 MythBox kernel: [66975.657183] lowmem_reserve[]: 0 0 0 0
Jan 12 11:07:54 MythBox kernel: [66975.657185] Node 0 DMA: 7*4kB (UEM) 5*8kB (UEM) 5*16kB (UEM) 4*32kB (UEM) 4*64kB (EM) 1*128kB (U) 2*256kB (UE) 3*512kB (UEM) 2*1024kB (EM) 3*2048kB (EMR) 1*4096kB (M) = 14996kB
Jan 12 11:07:54 MythBox kernel: [66975.657198] Node 0 DMA32: 376*4kB (UM) 8856*8kB (UEM) 7752*16kB (UM) 3*32kB (M) 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 1*4096kB (R) = 200576kB
Jan 12 11:07:54 MythBox kernel: [66975.657208] Node 0 Normal: 7299*4kB (UEM) 517*8kB (UM) 4*16kB (U) 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 1*4096kB (R) = 37492kB
Jan 12 11:07:54 MythBox kernel: [66975.657218] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
Jan 12 11:07:54 MythBox kernel: [66975.657220] 652227 total pagecache pages
Jan 12 11:07:54 MythBox kernel: [66975.657222] 38905 pages in swap cache
Jan 12 11:07:54 MythBox kernel: [66975.657223] Swap cache stats: add 240963, delete 202058, find 68604/77300
Jan 12 11:07:54 MythBox kernel: [66975.657224] Free swap  = 3417668kB
Jan 12 11:07:54 MythBox kernel: [66975.657225] Total swap = 3921916kB
Jan 12 11:07:54 MythBox kernel: [66975.672033] 999423 pages RAM
Jan 12 11:07:54 MythBox kernel: [66975.672036] 54618 pages reserved
Jan 12 11:07:54 MythBox kernel: [66975.672037] 1772225 pages shared
Jan 12 11:07:54 MythBox kernel: [66975.672038] 272104 pages non-shared
Jan 12 11:09:01 MythBox CRON[10988]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Jan 12 11:09:23 MythBox whoopsie[1191]: online
Jan 12 11:09:24 MythBox whoopsie[1191]: online
Jan 12 11:10:27 MythBox kernel: [67129.469595] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
Jan 12 11:10:27 MythBox kernel: [67129.469647] xc5000: firmware read 12401 bytes.
Jan 12 11:10:27 MythBox kernel: [67129.469649] xc5000: firmware uploading...
Jan 12 11:10:30 MythBox kernel: [67132.403580] xc5000: firmware upload complete...
Jan 12 11:16:04 MythBox whoopsie[1191]: online
Jan 12 11:17:05  whoopsie[1191]: last message repeated 2 times

```

And here's mythbackend log:

```
Jan 12 11:00:58 MythBox mythbackend: mythbackend[7184]: I Scheduler scheduler.cpp:2206 (HandleReschedule) Scheduled 5 items in 0.0 = 0.01 match + 0.00 check + 0.00 place
Jan 12 11:06:08 MythBox mythbackend: mythbackend[7184]: I SSDP mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 9
Jan 12 11:06:10 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1430 (HandleAnnounce) MainServer::ANN Monitor
Jan 12 11:06:10 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1432 (HandleAnnounce) adding: MythBox as a client (events: 0)
Jan 12 11:06:10 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1430 (HandleAnnounce) MainServer::ANN Monitor
Jan 12 11:06:10 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1432 (HandleAnnounce) adding: MythBox as a client (events: 1)
Jan 12 11:06:10 MythBox mythbackend: mythbackend[7184]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Reschedule requested for MATCH 0 1 6 2014-01-13T02:30:00Z EITScanner
Jan 12 11:06:10 MythBox mythbackend: mythbackend[7184]: I Scheduler scheduler.cpp:2206 (HandleReschedule) Scheduled 5 items in 0.0 = 0.01 match + 0.00 check + 0.00 place
Jan 12 11:06:16 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1430 (HandleAnnounce) MainServer::ANN Monitor
Jan 12 11:06:16 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1432 (HandleAnnounce) adding: MythBox as a client (events: 0)
Jan 12 11:06:27 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1430 (HandleAnnounce) MainServer::ANN Playback
Jan 12 11:06:27 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1432 (HandleAnnounce) adding: mythbox as a client (events: 0)
Jan 12 11:06:27 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1548 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Jan 12 11:06:27 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1550 (HandleAnnounce) adding: mythbox as a remote file transfer
Jan 12 11:06:39 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1430 (HandleAnnounce) MainServer::ANN Playback
Jan 12 11:06:39 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1432 (HandleAnnounce) adding: MythBox as a client (events: 0)
Jan 12 11:06:39 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:1048 (HandleStateChange) TVRec[15]: Changing from None to WatchingLiveTV
Jan 12 11:06:39 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:3597 (TuningCheckForHWChange) TVRec[15]: HW Tuner: 15->15
Jan 12 11:06:40 MythBox mythbackend: mythbackend[7184]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 42.0 GB w/freq: 14 min
Jan 12 11:06:40 MythBox mythbackend: mythbackend[7184]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 42.0 GB w/freq: 14 min
Jan 12 11:06:40 MythBox mythbackend: mythbackend[7184]: E TVRecEvent recordinginfo.cpp:928 (InsertProgram) RecordingInfo::InsertProgram(ProgramInfo(1061_20140112160640.mpg): channame(WTVR-HD) startts(Sun Jan 12 16:00:00 2014) endts(Sun Jan 12 16:30:00 2014)#012             recstartts(Sun Jan 12 16:06:40 2014) recendts(Sun Jan 12 16:30:00 2014)#012             title(All In With Laila Ali)): recording already exists...
Jan 12 11:06:44 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:435 (GetKeyframePositions) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframePositions(61,9223372036854775807,#3) out of 8
Jan 12 11:06:44 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:457 (GetKeyframeDurations) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframeDurations(61,9223372036854775807,#3) out of 8
Jan 12 11:06:44 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:435 (GetKeyframePositions) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframePositions(61,9223372036854775807,#3) out of 8
Jan 12 11:06:44 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:457 (GetKeyframeDurations) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframeDurations(61,9223372036854775807,#3) out of 8
Jan 12 11:06:50 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:3597 (TuningCheckForHWChange) TVRec[15]: HW Tuner: 15->15
Jan 12 11:06:51 MythBox mythbackend: mythbackend[7184]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 42.0 GB w/freq: 14 min
Jan 12 11:06:51 MythBox mythbackend: mythbackend[7184]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 42.0 GB w/freq: 14 min
Jan 12 11:06:52 MythBox mythbackend: mythbackend[7184]: E TVRecEvent recordinginfo.cpp:928 (InsertProgram) RecordingInfo::InsertProgram(ProgramInfo(1652_20140112160651.mpg): channame(Bounce ) startts(Sun Jan 12 16:00:00 2014) endts(Sun Jan 12 16:30:00 2014)#012             recstartts(Sun Jan 12 16:06:51 2014) recendts(Sun Jan 12 16:30:00 2014)#012             title(Fat Albert and the Cosby Kids)): recording already exists...
Jan 12 11:06:53 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:435 (GetKeyframePositions) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframePositions(1,9223372036854775807,#1) out of 2
Jan 12 11:06:53 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:457 (GetKeyframeDurations) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframeDurations(1,9223372036854775807,#1) out of 2
Jan 12 11:06:53 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:435 (GetKeyframePositions) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframePositions(1,9223372036854775807,#1) out of 2
Jan 12 11:06:53 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:457 (GetKeyframeDurations) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframeDurations(1,9223372036854775807,#1) out of 2
Jan 12 11:07:01 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:3597 (TuningCheckForHWChange) TVRec[15]: HW Tuner: 15->15
Jan 12 11:07:02 MythBox mythbackend: mythbackend[7184]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 42.0 GB w/freq: 14 min
Jan 12 11:07:02 MythBox mythbackend: mythbackend[7184]: E DVBRead recorders/dtvsignalmonitor.cpp:348 (HandlePMT) DTVSigMon[15](/dev/dvb/adapter0/frontend0): Wrong PMT; pmt->pn(2) desired(8)
Jan 12 11:07:02 MythBox mythbackend: mythbackend[7184]: E DVBRead recorders/dtvsignalmonitor.cpp:348 (HandlePMT) DTVSigMon[15](/dev/dvb/adapter0/frontend0): Wrong PMT; pmt->pn(3) desired(8)
Jan 12 11:07:02 MythBox mythbackend: mythbackend[7184]: E DVBRead recorders/dtvsignalmonitor.cpp:348 (HandlePMT) DTVSigMon[15](/dev/dvb/adapter0/frontend0): Wrong PMT; pmt->pn(1) desired(8)
Jan 12 11:07:02 MythBox mythbackend: mythbackend[7184]: E DVBRead recorders/dtvsignalmonitor.cpp:348 (HandlePMT) DTVSigMon[15](/dev/dvb/adapter0/frontend0): Wrong PMT; pmt->pn(9) desired(8)
Jan 12 11:07:02 MythBox mythbackend: mythbackend[7184]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 42.0 GB w/freq: 14 min
Jan 12 11:07:02 MythBox mythbackend: mythbackend[7184]: E TVRecEvent recordinginfo.cpp:928 (InsertProgram) RecordingInfo::InsertProgram(ProgramInfo(1428_20140112160702.mpg): channame() startts(Sun Jan 12 16:07:02 2014) endts(Sun Jan 12 16:30:00 2014)#012             recstartts(Sun Jan 12 16:07:02 2014) recendts(Sun Jan 12 16:30:00 2014)#012             title(Unknown)): recording already exists...
Jan 12 11:07:05 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:435 (GetKeyframePositions) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframePositions(2,9223372036854775807,#0) out of 1
Jan 12 11:07:05 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:457 (GetKeyframeDurations) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframeDurations(2,9223372036854775807,#0) out of 1
Jan 12 11:07:05 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:435 (GetKeyframePositions) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframePositions(2,9223372036854775807,#0) out of 1
Jan 12 11:07:05 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:457 (GetKeyframeDurations) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframeDurations(2,9223372036854775807,#0) out of 1
Jan 12 11:07:11 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:1048 (HandleStateChange) TVRec[15]: Changing from WatchingLiveTV to None
Jan 12 11:07:11 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:832 (FinishedRecording) TVRec[15]: FinishedRecording(1428_2014-01-12T16:07:03Z) damaged recq:<RecordingQuality overall_score="0" key="1428_2014-01-12T16:07:03Z" countinuity_error_count="25" packet_count="272">#012    <Gap start="2014-01-12T16:07:05Z" end="2014-01-12T16:30:00Z" duration="1374" />#012</RecordingQuality>
Jan 12 11:07:11 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1430 (HandleAnnounce) MainServer::ANN Playback
Jan 12 11:07:11 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1432 (HandleAnnounce) adding: MythBox as a client (events: 0)
Jan 12 11:07:11 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:1048 (HandleStateChange) TVRec[17]: Changing from None to WatchingLiveTV
Jan 12 11:07:11 MythBox mythbackend: mythbackend[7184]: I TVRecEvent mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 12
Jan 12 11:07:11 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:3597 (TuningCheckForHWChange) TVRec[17]: HW Tuner: 17->17
Jan 12 11:07:11 MythBox mythbackend: mythbackend[7184]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 42.0 GB w/freq: 14 min
Jan 12 11:07:16 MythBox mythbackend: mythbackend[7184]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 42.0 GB w/freq: 14 min
Jan 12 11:07:19 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:435 (GetKeyframePositions) RecBase[17](/dev/dvb/adapter1/frontend0): GetKeyframePositions(2,9223372036854775807,#0) out of 1
Jan 12 11:07:19 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:457 (GetKeyframeDurations) RecBase[17](/dev/dvb/adapter1/frontend0): GetKeyframeDurations(2,9223372036854775807,#0) out of 1
Jan 12 11:07:20 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:435 (GetKeyframePositions) RecBase[17](/dev/dvb/adapter1/frontend0): GetKeyframePositions(2,9223372036854775807,#0) out of 1
Jan 12 11:07:20 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:457 (GetKeyframeDurations) RecBase[17](/dev/dvb/adapter1/frontend0): GetKeyframeDurations(2,9223372036854775807,#0) out of 1
Jan 12 11:07:21 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:1048 (HandleStateChange) TVRec[17]: Changing from WatchingLiveTV to None
Jan 12 11:07:21 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:832 (FinishedRecording) TVRec[17]: FinishedRecording(3428_2014-01-12T16:07:16Z) damaged recq:<RecordingQuality overall_score="0" key="3428_2014-01-12T16:07:16Z" countinuity_error_count="18" packet_count="215">#012    <Gap start="2014-01-12T16:07:21Z" end="2014-01-12T16:30:00Z" duration="1358" />#012</RecordingQuality>
Jan 12 11:07:21 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1430 (HandleAnnounce) MainServer::ANN Playback
Jan 12 11:07:21 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1432 (HandleAnnounce) adding: MythBox as a client (events: 0)
Jan 12 11:07:21 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:1048 (HandleStateChange) TVRec[15]: Changing from None to WatchingLiveTV
Jan 12 11:07:21 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:3597 (TuningCheckForHWChange) TVRec[15]: HW Tuner: 15->15
Jan 12 11:07:21 MythBox mythbackend: mythbackend[7184]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 42.0 GB w/freq: 14 min
Jan 12 11:07:21 MythBox mythbackend: mythbackend[7184]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 42.0 GB w/freq: 14 min
Jan 12 11:07:21 MythBox mythbackend: mythbackend[7184]: E TVRecEvent recordinginfo.cpp:928 (InsertProgram) RecordingInfo::InsertProgram(ProgramInfo(1429_20140112160721.mpg): channame() startts(Sun Jan 12 16:07:21 2014) endts(Sun Jan 12 16:30:00 2014)#012             recstartts(Sun Jan 12 16:07:21 2014) recendts(Sun Jan 12 16:30:00 2014)#012             title(Unknown)): recording already exists...
Jan 12 11:07:29 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:435 (GetKeyframePositions) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframePositions(2,9223372036854775807,#0) out of 1
Jan 12 11:07:29 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:457 (GetKeyframeDurations) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframeDurations(2,9223372036854775807,#0) out of 1
Jan 12 11:07:29 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:435 (GetKeyframePositions) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframePositions(2,9223372036854775807,#0) out of 1
Jan 12 11:07:29 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:457 (GetKeyframeDurations) RecBase[15](/dev/dvb/adapter0/frontend0): GetKeyframeDurations(2,9223372036854775807,#0) out of 1
Jan 12 11:07:31 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:1048 (HandleStateChange) TVRec[15]: Changing from WatchingLiveTV to None
Jan 12 11:07:31 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:832 (FinishedRecording) TVRec[15]: FinishedRecording(1429_2014-01-12T16:07:22Z) damaged recq:<RecordingQuality overall_score="0" key="1429_2014-01-12T16:07:22Z" countinuity_error_count="10" packet_count="28">#012    <Gap start="2014-01-12T16:07:31Z" end="2014-01-12T16:30:00Z" duration="1348" />#012</RecordingQuality>
Jan 12 11:07:31 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1430 (HandleAnnounce) MainServer::ANN Playback
Jan 12 11:07:31 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1432 (HandleAnnounce) adding: MythBox as a client (events: 0)
Jan 12 11:07:31 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:1048 (HandleStateChange) TVRec[17]: Changing from None to WatchingLiveTV
Jan 12 11:07:31 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:3597 (TuningCheckForHWChange) TVRec[17]: HW Tuner: 17->17
Jan 12 11:07:31 MythBox mythbackend: mythbackend[7184]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 42.0 GB w/freq: 14 min
Jan 12 11:07:32 MythBox mythbackend: mythbackend[7184]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 42.0 GB w/freq: 14 min
Jan 12 11:07:34 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:435 (GetKeyframePositions) RecBase[17](/dev/dvb/adapter1/frontend0): GetKeyframePositions(2,9223372036854775807,#0) out of 1
Jan 12 11:07:34 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:457 (GetKeyframeDurations) RecBase[17](/dev/dvb/adapter1/frontend0): GetKeyframeDurations(2,9223372036854775807,#0) out of 1
Jan 12 11:07:34 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:435 (GetKeyframePositions) RecBase[17](/dev/dvb/adapter1/frontend0): GetKeyframePositions(2,9223372036854775807,#0) out of 1
Jan 12 11:07:34 MythBox mythbackend: mythbackend[7184]: I ProcessRequest recorders/recorderbase.cpp:457 (GetKeyframeDurations) RecBase[17](/dev/dvb/adapter1/frontend0): GetKeyframeDurations(2,9223372036854775807,#0) out of 1
Jan 12 11:07:53 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:1048 (HandleStateChange) TVRec[17]: Changing from WatchingLiveTV to None
Jan 12 11:07:53 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:832 (FinishedRecording) TVRec[17]: FinishedRecording(3429_2014-01-12T16:07:32Z) damaged recq:<RecordingQuality overall_score="0" key="3429_2014-01-12T16:07:32Z" countinuity_error_count="0" packet_count="141">#012    <Gap start="2014-01-12T16:07:52Z" end="2014-01-12T16:30:00Z" duration="1327" />#012</RecordingQuality>
Jan 12 11:07:53 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1430 (HandleAnnounce) MainServer::ANN Playback
Jan 12 11:07:53 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1432 (HandleAnnounce) adding: MythBox as a client (events: 0)
Jan 12 11:07:53 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:1048 (HandleStateChange) TVRec[15]: Changing from None to WatchingLiveTV
Jan 12 11:07:53 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:3597 (TuningCheckForHWChange) TVRec[15]: HW Tuner: 15->15
Jan 12 11:07:54 MythBox mythbackend: mythbackend[7184]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 42.0 GB w/freq: 14 min
Jan 12 11:07:54 MythBox mythbackend: mythbackend[7184]: E DVBRead recorders/dvbstreamhandler.cpp:633 (Open) PIDInfo(/dev/dvb/adapter0/frontend0): Failed to set TS filter (pid 0x0)
Jan 12 11:08:02 MythBox mythbackend: mythbackend[7184]: E ProcessRequest tv_rec.cpp:2889 (PauseRecorder) TVRec[15]: PauseRecorder() called with no recorder
Jan 12 11:08:02 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:3597 (TuningCheckForHWChange) TVRec[15]: HW Tuner: 15->15
Jan 12 11:08:02 MythBox mythbackend: mythbackend[7184]: N CoreContext autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 42.0 GB w/freq: 14 min
Jan 12 11:08:04 MythBox mythbackend: mythbackend[7184]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Reschedule requested for MATCH 0 0 0 2014-01-13T14:30:00Z EITScanner
Jan 12 11:08:04 MythBox mythbackend: mythbackend[7184]: I Scheduler scheduler.cpp:2206 (HandleReschedule) Scheduled 5 items in 0.0 = 0.00 match + 0.00 check + 0.00 place
Jan 12 11:08:10 MythBox mythbackend: mythbackend[7184]: I TVRecEvent tv_rec.cpp:1048 (HandleStateChange) TVRec[15]: Changing from WatchingLiveTV to None
Jan 12 11:08:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1061 at 2014-01-12T16:06:40Z => "All In With Laila Ali"
Jan 12 11:08:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 15 MB for 1061 at 2014-01-12T16:06:41Z => "All In With Laila Ali"
Jan 12 11:08:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1652 at 2014-01-12T16:06:51Z => "Fat Albert and the Cosby Kids"
Jan 12 11:08:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 2 MB for 1652 at 2014-01-12T16:06:52Z => "Fat Albert and the Cosby Kids"
Jan 12 11:08:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1428 at 2014-01-12T16:07:02Z => Unknown
Jan 12 11:08:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1428 at 2014-01-12T16:07:03Z => Unknown
Jan 12 11:08:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 3428 at 2014-01-12T16:07:11Z => Unknown
Jan 12 11:08:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 3428 at 2014-01-12T16:07:16Z => Unknown
Jan 12 11:08:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1429 at 2014-01-12T16:07:21Z => Unknown
Jan 12 11:08:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1429 at 2014-01-12T16:07:22Z => Unknown
Jan 12 11:08:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 3429 at 2014-01-12T16:07:31Z => Unknown
Jan 12 11:09:35 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1430 (HandleAnnounce) MainServer::ANN Monitor
Jan 12 11:09:35 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1432 (HandleAnnounce) adding: MythBox as a client (events: 0)
Jan 12 11:09:35 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1430 (HandleAnnounce) MainServer::ANN Monitor
Jan 12 11:09:35 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1432 (HandleAnnounce) adding: MythBox as a client (events: 1)
Jan 12 11:09:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 40.0 GB w/freq: 15 min
Jan 12 11:09:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1082 at 2014-01-07T15:14:06Z => "Mirror Mirror"
Jan 12 11:09:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1351 at 2014-01-08T07:00:00Z => "Family Guy"
Jan 12 11:09:52 MythBox mythbackend: mythbackend[7184]: E DeleteThread mainserver.cpp:2295 (OpenAndUnlink) Error deleting '/var/lib/mythtv/livetv/1082_20140107151406.mpg' could not open #012#011#011#011eno: Permission denied (13)
Jan 12 11:09:52 MythBox mythbackend: mythbackend[7184]: E DeleteThread mainserver.cpp:2273 (DeleteFile) Delete Error '/var/lib/mythtv/livetv/1082_20140107151406.mpg'#012#011#011#011eno: Permission denied (13)
Jan 12 11:09:52 MythBox mythbackend: mythbackend[7184]: E DeleteThread mainserver.cpp:2053 (DoDeleteThread) Error deleting file: /var/lib/mythtv/livetv/1082_20140107151406.mpg. Keeping metadata in database.
Jan 12 11:09:52 MythBox mythbackend: mythbackend[7184]: E DeleteThread mainserver.cpp:2295 (OpenAndUnlink) Error deleting '/var/lib/mythtv/livetv/1351_20140108070000.mpg' could not open #012#011#011#011eno: Permission denied (13)
Jan 12 11:09:52 MythBox mythbackend: mythbackend[7184]: E DeleteThread mainserver.cpp:2273 (DeleteFile) Delete Error '/var/lib/mythtv/livetv/1351_20140108070000.mpg'#012#011#011#011eno: Permission denied (13)
Jan 12 11:09:52 MythBox mythbackend: mythbackend[7184]: E DeleteThread mainserver.cpp:2053 (DoDeleteThread) Error deleting file: /var/lib/mythtv/livetv/1351_20140108070000.mpg. Keeping metadata in database.
Jan 12 11:10:13 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1430 (HandleAnnounce) MainServer::ANN Monitor
Jan 12 11:10:13 MythBox mythbackend: mythbackend[7184]: I ProcessRequest mainserver.cpp:1432 (HandleAnnounce) adding: MythBox as a client (events: 0)
Jan 12 11:10:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 3 MB for 3429 at 2014-01-12T16:07:32Z => Unknown
Jan 12 11:10:49 MythBox mythbackend: mythbackend[7184]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 1063 at 2014-01-12T16:08:02Z => "Face the Nation
```

Lastly, scan output for either card is:

```
mythuser@MythBox:~$ scan -a 1 /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB 
scanning /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
main:2745: FATAL: failed to open '/dev/dvb/adapter1/frontend0': 16 Device or resource busy

```

Mythtv-seup terminal output:

```
2014-01-12 11:21:57.255203 I  Using protocol version 77
2014-01-12 11:21:59.873665 I  Trying to stop backend
2014-01-12 11:21:59.873749 I  Locking input devices
2014-01-12 11:21:59.873756 N  Suspending idle timer
2014-01-12 11:21:59.948786 I  Unlocking input devices
2014-01-12 11:21:59.948803 N  Resuming idle timer
2014-01-12 11:22:04.223111 E  Can't open DVB frontend (/dev/dvb/adapter0/frontend0) for /dev/dvb/adapter0/frontend0.
2014-01-12 11:22:04.223245 E  Can't open DVB frontend (/dev/dvb/adapter0/frontend0) for /dev/dvb/adapter0/frontend0.
2014-01-12 11:22:04.223620 E  Can't open DVB frontend (/dev/dvb/adapter0/frontend0) for /dev/dvb/adapter0/frontend0.
2014-01-12 11:22:04.223736 E  Can't open DVB frontend (/dev/dvb/adapter0/frontend0) for /dev/dvb/adapter0/frontend0.
2014-01-12 11:22:04.224343 W  DiSEqCDevTree: No device tree for cardid 15
2014-01-12 11:22:04.224585 E  ProbeAudioInputs() -> couldn't open device
2014-01-12 11:22:04.224606 E  ProbeAudioInputs() -> couldn't open device
2014-01-12 11:22:04.653418 E  Can't open DVB frontend (/dev/dvb/adapter0/frontend0) for /dev/dvb/adapter0/frontend0.
2014-01-12 11:22:04.653538 E  Can't open DVB frontend (/dev/dvb/adapter0/frontend0) for /dev/dvb/adapter0/frontend0.
2014-01-12 11:22:04.653916 E  Can't open DVB frontend (/dev/dvb/adapter0/frontend0) for /dev/dvb/adapter0/frontend0.
2014-01-12 11:22:04.654032 E  Can't open DVB frontend (/dev/dvb/adapter0/frontend0) for /dev/dvb/adapter0/frontend0.
2014-01-12 11:22:04.654623 W  DiSEqCDevTree: No device tree for cardid 15
2014-01-12 11:22:04.654821 E  ProbeAudioInputs() -> couldn't open device

```

In mythtv-setup under the capture cards, when I try to open them it says "unknown error".

Totally at a loss here...

---

