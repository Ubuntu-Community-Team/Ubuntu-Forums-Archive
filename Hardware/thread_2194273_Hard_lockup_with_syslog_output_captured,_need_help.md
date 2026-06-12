---
title: "Hard lockup with syslog output captured, need help diagnosing"
date: 2013-12-17
forum: Hardware
---

### Post by brynn.west on 2013-12-17
Hello all,

I have not had many issues with my build till now.. My system has started randomly locking up, sometimes while playing music or watching movies, sometimes just browsing on firefox. The lock ups are usually hard (no mouse feedback, no key responce, sometimes wonky video but not always), sometimes I can Ctl+Alt+F1 into a terminal, and sometimes it dumps terminal output to my screen.

So, the lock-ups are relativly varried, but I have been able to capture output from /var/log/syslog (below) by using ssh. The output is representative of other crashes I've had and captured, even when the manifestation of the crash is different.

I recently did a full reinstall of 12.04 LTS and the problems persist. I suspect hardware at this point. I have run memtest overnight with no errors. My HDD seem to check out via SMART. I'm looking for help with future diagnostics to do and if folk here can narrow down my issue.

A side note, I can run Ubuntu 12.04 for long periods with no crash via a live CD. No idea if that is helpful... **Spoke too soon, just had a crash (dump to screen) when using a live CD.**

**Hardware Specs:**

Motherboard: [ASUS M5A88-V EVO AM3+ AMD 880G SATA 6Gb/s USB 3.0 HDMI ATX AMD Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131733R")
CPU: [AMD Phenom II X4 965 Black Edition Deneb 3.4GHz Socket AM3]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103727")
RAM: [G.SKILL Ripjaws X Series 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231428")
PSU: [OCZ ZT Series 650W Fully-Modular]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817341051")
HDD1 (Ubuntu 12.04 LTS): [Western Digital WD Green WD10EADS 1TB 32MB Cache SATA 3.0Gb/s]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136317")
HDD2 (NTFS formatted storage): [Seagate Barracuda Green ST1500DL003 1.5TB 5900 RPM 64MB Cache SATA 6.0Gb/s]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148725")

**Error Log:**

```
Dec 17 11:36:04 herbox kernel: [ 2205.699071] general protection fault: 0000 [#1] SMP 
Dec 17 11:36:04 herbox kernel: [ 2205.699082] CPU 2 
Dec 17 11:36:04 herbox kernel: [ 2205.699086] Modules linked in: rfcomm bnep bluetooth parport_pc ppdev lp parport kvm snd_hda_codec_hdmi snd_hda_codec_realtek arc4 snd_hda_intel snd_hda_codec radeon rt2800pci ttm rt2800lib crc_ccitt snd_seq_midi snd_rawmidi drm_kms_helper rt2x00pci rt2x00lib drm edac_core snd_hwdep snd_seq_midi_event mac80211 snd_pcm snd_seq joydev cfg80211 snd_timer mac_hid i2c_algo_bit edac_mce_amd snd_seq_device sp5100_tco shpchp psmouse snd k10temp serio_raw soundcore snd_page_alloc eeprom_93cx6 i2c_piix4 wmi microcode asus_atk0110 hid_generic hid_logitech_dj firewire_ohci usbhid firewire_core hid crc_itu_t r8169 pata_atiixp ahci libahci pata_via
Dec 17 11:36:04 herbox kernel: [ 2205.699178] 
Dec 17 11:36:04 herbox kernel: [ 2205.699185] Pid: 925, comm: jbd2/sdb6-8 Not tainted 3.5.0-44-generic #67~precise1-Ubuntu System manufacturer System Product Name/M5A88-V EVO
Dec 17 11:36:04 herbox kernel: [ 2205.699195] RIP: 0010:[<ffffffff81135300>]  [<ffffffff81135300>] pagevec_lru_move_fn+0x40/0x110
Dec 17 11:36:04 herbox kernel: [ 2205.699210] RSP: 0018:ffff880212ff9a00  EFLAGS: 00010246
Dec 17 11:36:04 herbox kernel: [ 2205.699216] RAX: 0000000000000000 RBX: 0000000000000000 RCX: 0000000000000000
Dec 17 11:36:04 herbox kernel: [ 2205.699221] RDX: 0000000000000000 RSI: 0000000000000006 RDI: ffff88021fc90260
Dec 17 11:36:04 herbox kernel: [ 2205.699225] RBP: ffff880212ff9a50 R08: 1200000000000000 R09: a80017b289000000
Dec 17 11:36:04 herbox kernel: [ 2205.699229] R10: 57ffd24d7ceca240 R11: ffff8801cb6bf518 R12: 0000000000000000
Dec 17 11:36:04 herbox kernel: [ 2205.699233] R13: ff7fea0005fd7840 R14: ffff88021fc90260 R15: 0000000000000000
Dec 17 11:36:04 herbox kernel: [ 2205.699239] FS:  00007fad86116740(0000) GS:ffff88021fc80000(0000) knlGS:0000000000000000
Dec 17 11:36:04 herbox kernel: [ 2205.699244] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Dec 17 11:36:04 herbox kernel: [ 2205.699249] CR2: 00007fad26e7a010 CR3: 00000001ff0f3000 CR4: 00000000000007e0
Dec 17 11:36:04 herbox kernel: [ 2205.699253] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 17 11:36:04 herbox kernel: [ 2205.699258] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 17 11:36:04 herbox kernel: [ 2205.699264] Process jbd2/sdb6-8 (pid: 925, threadinfo ffff880212ff8000, task ffff880210484500)
Dec 17 11:36:04 herbox kernel: [ 2205.699267] Stack:
Dec 17 11:36:04 herbox kernel: [ 2205.699270]  0000000000000002 ffffffff81134de0 0000000000000000 ffffffff81134ba0
Dec 17 11:36:04 herbox kernel: [ 2205.699280]  ffff88021fc903e0 0000000000000002 ffff88021fc90560 0000000000000005
Dec 17 11:36:04 herbox kernel: [ 2205.699288]  0000000000000001 0000000000000000 ffff880212ff9a80 ffffffff81135a63
Dec 17 11:36:04 herbox kernel: [ 2205.699297] Call Trace:
Dec 17 11:36:04 herbox kernel: [ 2205.699307]  [<ffffffff81134de0>] ? lru_deactivate_fn+0x40/0x40
Dec 17 11:36:04 herbox kernel: [ 2205.699315]  [<ffffffff81134ba0>] ? __activate_page.part.9+0x170/0x170
Dec 17 11:36:04 herbox kernel: [ 2205.699323]  [<ffffffff81135a63>] lru_add_drain_cpu+0x83/0xf0
Dec 17 11:36:04 herbox kernel: [ 2205.699330]  [<ffffffff81135b76>] lru_add_drain+0x16/0x20
Dec 17 11:36:04 herbox kernel: [ 2205.699337]  [<ffffffff81135b96>] __pagevec_release+0x16/0x40
Dec 17 11:36:04 herbox kernel: [ 2205.699346]  [<ffffffff81132b03>] write_cache_pages+0x383/0x460
Dec 17 11:36:04 herbox kernel: [ 2205.699355]  [<ffffffff81033ee8>] ? native_smp_send_reschedule+0x48/0x60
Dec 17 11:36:04 herbox kernel: [ 2205.699364]  [<ffffffff81132120>] ? set_page_dirty_lock+0x60/0x60
Dec 17 11:36:04 herbox kernel: [ 2205.699373]  [<ffffffff81132c2a>] generic_writepages+0x4a/0x70
Dec 17 11:36:04 herbox kernel: [ 2205.699384]  [<ffffffff8127170f>] journal_submit_data_buffers+0xbf/0x1a0
Dec 17 11:36:04 herbox kernel: [ 2205.699392]  [<ffffffff81080e48>] ? __wake_up_common+0x58/0x90
Dec 17 11:36:04 herbox kernel: [ 2205.699401]  [<ffffffff81272060>] jbd2_journal_commit_transaction+0x310/0x13a0
Dec 17 11:36:04 herbox kernel: [ 2205.699411]  [<ffffffff81040ae9>] ? default_spin_lock_flags+0x9/0x10
Dec 17 11:36:04 herbox kernel: [ 2205.699420]  [<ffffffff8169f13e>] ? _raw_spin_lock_irqsave+0x2e/0x40
Dec 17 11:36:04 herbox kernel: [ 2205.699429]  [<ffffffff81064028>] ? lock_timer_base.isra.35+0x38/0x70
Dec 17 11:36:04 herbox kernel: [ 2205.699437]  [<ffffffff81064a42>] ? try_to_del_timer_sync+0x92/0x130
Dec 17 11:36:04 herbox kernel: [ 2205.699446]  [<ffffffff81277136>] kjournald2+0xb6/0x240
Dec 17 11:36:04 herbox kernel: [ 2205.699454]  [<ffffffff81078720>] ? add_wait_queue+0x60/0x60
Dec 17 11:36:04 herbox kernel: [ 2205.699463]  [<ffffffff81277080>] ? commit_timeout+0x10/0x10
Dec 17 11:36:04 herbox kernel: [ 2205.699470]  [<ffffffff81077e43>] kthread+0x93/0xa0
Dec 17 11:36:04 herbox kernel: [ 2205.699477]  [<ffffffff816a8a24>] kernel_thread_helper+0x4/0x10
Dec 17 11:36:04 herbox kernel: [ 2205.699485]  [<ffffffff81077db0>] ? flush_kthread_worker+0xb0/0xb0
Dec 17 11:36:04 herbox kernel: [ 2205.699492]  [<ffffffff816a8a20>] ? gs_change+0x13/0x13
Dec 17 11:36:04 herbox kernel: [ 2205.699495] Code: 90 48 89 75 c8 48 8b 37 49 89 fe 48 89 55 c0 85 f6 0f 84 b4 00 00 00 45 31 ff 31 db 45 31 e4 0f 1f 40 00 49 63 c4 4d 8b 6c c6 10 <49> 8b 45 00 48 89 c1 48 c1 e8 38 83 e0 03 48 c1 e9 3a 48 8d 14 
Dec 17 11:36:04 herbox kernel: [ 2205.699571] RIP  [<ffffffff81135300>] pagevec_lru_move_fn+0x40/0x110
Dec 17 11:36:04 herbox kernel: [ 2205.699578]  RSP <ffff880212ff9a00>
Dec 17 11:36:04 herbox kernel: [ 2205.699584] ---[ end trace bbc7c1fc73cca7c9 ]---
Dec 17 11:36:04 herbox kernel: [ 2205.699589] ------------[ cut here ]------------
Dec 17 11:36:04 herbox kernel: [ 2205.699598] WARNING: at /build/buildd/linux-lts-quantal-3.5.0/kernel/exit.c:912 do_exit+0x55/0x480()
Dec 17 11:36:04 herbox kernel: [ 2205.699601] Hardware name: System Product Name
Dec 17 11:36:04 herbox kernel: [ 2205.699604] Modules linked in: rfcomm bnep bluetooth parport_pc ppdev lp parport kvm snd_hda_codec_hdmi snd_hda_codec_realtek arc4 snd_hda_intel snd_hda_codec radeon rt2800pci ttm rt2800lib crc_ccitt snd_seq_midi snd_rawmidi drm_kms_helper rt2x00pci rt2x00lib drm edac_core snd_hwdep snd_seq_midi_event mac80211 snd_pcm snd_seq joydev cfg80211 snd_timer mac_hid i2c_algo_bit edac_mce_amd snd_seq_device sp5100_tco shpchp psmouse snd k10temp serio_raw soundcore snd_page_alloc eeprom_93cx6 i2c_piix4 wmi microcode asus_atk0110 hid_generic hid_logitech_dj firewire_ohci usbhid firewire_core hid crc_itu_t r8169 pata_atiixp ahci libahci pata_via
Dec 17 11:36:04 herbox kernel: [ 2205.699688] Pid: 925, comm: jbd2/sdb6-8 Tainted: G      D      3.5.0-44-generic #67~precise1-Ubuntu
Dec 17 11:36:04 herbox kernel: [ 2205.699691] Call Trace:
Dec 17 11:36:04 herbox kernel: [ 2205.699699]  [<ffffffff81052e9f>] warn_slowpath_common+0x7f/0xc0
Dec 17 11:36:04 herbox kernel: [ 2205.699706]  [<ffffffff81052efa>] warn_slowpath_null+0x1a/0x20
Dec 17 11:36:04 herbox kernel: [ 2205.699714]  [<ffffffff81059265>] do_exit+0x55/0x480
Dec 17 11:36:04 herbox kernel: [ 2205.699722]  [<ffffffff816a01d0>] oops_end+0xb0/0xf0
Dec 17 11:36:04 herbox kernel: [ 2205.699731]  [<ffffffff810177e8>] die+0x58/0x90
Dec 17 11:36:04 herbox kernel: [ 2205.699739]  [<ffffffff8169fcd2>] do_general_protection+0x162/0x170
Dec 17 11:36:04 herbox kernel: [ 2205.699748]  [<ffffffff8169f5f5>] general_protection+0x25/0x30
Dec 17 11:36:04 herbox kernel: [ 2205.699755]  [<ffffffff81135300>] ? pagevec_lru_move_fn+0x40/0x110
Dec 17 11:36:04 herbox kernel: [ 2205.699762]  [<ffffffff81134de0>] ? lru_deactivate_fn+0x40/0x40
Dec 17 11:36:04 herbox kernel: [ 2205.699769]  [<ffffffff81134ba0>] ? __activate_page.part.9+0x170/0x170
Dec 17 11:36:04 herbox kernel: [ 2205.699776]  [<ffffffff81135a63>] lru_add_drain_cpu+0x83/0xf0
Dec 17 11:36:04 herbox kernel: [ 2205.699783]  [<ffffffff81135b76>] lru_add_drain+0x16/0x20
Dec 17 11:36:04 herbox kernel: [ 2205.699790]  [<ffffffff81135b96>] __pagevec_release+0x16/0x40
Dec 17 11:36:04 herbox kernel: [ 2205.699798]  [<ffffffff81132b03>] write_cache_pages+0x383/0x460
Dec 17 11:36:04 herbox kernel: [ 2205.699806]  [<ffffffff81033ee8>] ? native_smp_send_reschedule+0x48/0x60
Dec 17 11:36:04 herbox kernel: [ 2205.699815]  [<ffffffff81132120>] ? set_page_dirty_lock+0x60/0x60
Dec 17 11:36:04 herbox kernel: [ 2205.699824]  [<ffffffff81132c2a>] generic_writepages+0x4a/0x70
Dec 17 11:36:04 herbox kernel: [ 2205.699832]  [<ffffffff8127170f>] journal_submit_data_buffers+0xbf/0x1a0
Dec 17 11:36:04 herbox kernel: [ 2205.699839]  [<ffffffff81080e48>] ? __wake_up_common+0x58/0x90
Dec 17 11:36:04 herbox kernel: [ 2205.699848]  [<ffffffff81272060>] jbd2_journal_commit_transaction+0x310/0x13a0
Dec 17 11:36:04 herbox kernel: [ 2205.699857]  [<ffffffff81040ae9>] ? default_spin_lock_flags+0x9/0x10
Dec 17 11:36:04 herbox kernel: [ 2205.699865]  [<ffffffff8169f13e>] ? _raw_spin_lock_irqsave+0x2e/0x40
Dec 17 11:36:04 herbox kernel: [ 2205.699872]  [<ffffffff81064028>] ? lock_timer_base.isra.35+0x38/0x70
Dec 17 11:36:04 herbox kernel: [ 2205.699880]  [<ffffffff81064a42>] ? try_to_del_timer_sync+0x92/0x130
Dec 17 11:36:04 herbox kernel: [ 2205.699889]  [<ffffffff81277136>] kjournald2+0xb6/0x240
Dec 17 11:36:04 herbox kernel: [ 2205.699896]  [<ffffffff81078720>] ? add_wait_queue+0x60/0x60
Dec 17 11:36:04 herbox kernel: [ 2205.699904]  [<ffffffff81277080>] ? commit_timeout+0x10/0x10
Dec 17 11:36:04 herbox kernel: [ 2205.699911]  [<ffffffff81077e43>] kthread+0x93/0xa0
Dec 17 11:36:04 herbox kernel: [ 2205.699918]  [<ffffffff816a8a24>] kernel_thread_helper+0x4/0x10
Dec 17 11:36:04 herbox kernel: [ 2205.699925]  [<ffffffff81077db0>] ? flush_kthread_worker+0xb0/0xb0
Dec 17 11:36:04 herbox kernel: [ 2205.699932]  [<ffffffff816a8a20>] ? gs_change+0x13/0x13
Dec 17 11:36:04 herbox kernel: [ 2205.699936] ---[ end trace bbc7c1fc73cca7ca ]---
Dec 17 11:36:04 herbox kernel: [ 2206.139421] general protection fault: 0000 [#2] SMP 
Dec 17 11:36:04 herbox kernel: [ 2206.139433] CPU 2 
Dec 17 11:36:04 herbox kernel: [ 2206.139437] Modules linked in: rfcomm bnep bluetooth parport_pc ppdev lp parport kvm snd_hda_codec_hdmi snd_hda_codec_realtek arc4 snd_hda_intel snd_hda_codec radeon rt2800pci ttm rt2800lib crc_ccitt snd_seq_midi snd_rawmidi drm_kms_helper rt2x00pci rt2x00lib drm edac_core snd_hwdep snd_seq_midi_event mac80211 snd_pcm snd_seq joydev cfg80211 snd_timer mac_hid i2c_algo_bit edac_mce_amd snd_seq_device sp5100_tco shpchp psmouse snd k10temp serio_raw soundcore snd_page_alloc eeprom_93cx6 i2c_piix4 wmi microcode asus_atk0110 hid_generic hid_logitech_dj firewire_ohci usbhid firewire_core hid crc_itu_t r8169 pata_atiixp ahci libahci pata_via
Dec 17 11:36:04 herbox kernel: [ 2206.139537] 
Dec 17 11:36:04 herbox kernel: [ 2206.139544] Pid: 4273, comm: task14 Tainted: G      D W    3.5.0-44-generic #67~precise1-Ubuntu System manufacturer System Product Name/M5A88-V EVO
Dec 17 11:36:04 herbox kernel: [ 2206.139554] RIP: 0010:[<ffffffff81135300>]  [<ffffffff81135300>] pagevec_lru_move_fn+0x40/0x110
Dec 17 11:36:04 herbox kernel: [ 2206.139570] RSP: 0018:ffff8801ff08dbd8  EFLAGS: 00010246
Dec 17 11:36:04 herbox kernel: [ 2206.139576] RAX: 0000000000000000 RBX: 0000000000000000 RCX: 0000000004e4278f
Dec 17 11:36:04 herbox kernel: [ 2206.139580] RDX: 0000000000000000 RSI: 000000000000000e RDI: ffff88021fc90260
Dec 17 11:36:04 herbox kernel: [ 2206.139585] RBP: ffff8801ff08dc28 R08: ffffea0005fcb61c R09: ffff8801d32bfcb0
Dec 17 11:36:04 herbox kernel: [ 2206.139589] R10: ffff8801ff08dfd8 R11: 0000000000000293 R12: 0000000000000000
Dec 17 11:36:04 herbox kernel: [ 2206.139594] R13: ff7fea0005fd7840 R14: ffff88021fc90260 R15: 0000000000000000
Dec 17 11:36:04 herbox kernel: [ 2206.139600] FS:  00007fa31e2d9700(0000) GS:ffff88021fc80000(0000) knlGS:0000000000000000
Dec 17 11:36:04 herbox kernel: [ 2206.139604] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Dec 17 11:36:04 herbox kernel: [ 2206.139609] CR2: 00007fad1d3f5010 CR3: 00000001f9b68000 CR4: 00000000000007e0
Dec 17 11:36:04 herbox kernel: [ 2206.139614] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 17 11:36:04 herbox kernel: [ 2206.139618] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 17 11:36:04 herbox kernel: [ 2206.139624] Process task14 (pid: 4273, threadinfo ffff8801ff08c000, task ffff8801c5ebdc00)
Dec 17 11:36:04 herbox kernel: [ 2206.139627] Stack:
Dec 17 11:36:04 herbox kernel: [ 2206.139630]  ffff8801ff08dbe8 ffffffff81040ae9 0000000000000000 ffffffff81134ba0
Dec 17 11:36:04 herbox kernel: [ 2206.139641]  ffff8801ff08dc18 ffff88021fc90260 ffffea0005fcb600 0000000000001916
Dec 17 11:36:04 herbox kernel: [ 2206.139649]  ffff8801fd080b00 0000000000000000 ffff8801ff08dc48 ffffffff81135811
Dec 17 11:36:04 herbox kernel: [ 2206.139657] Call Trace:
Dec 17 11:36:04 herbox kernel: [ 2206.139671]  [<ffffffff81040ae9>] ? default_spin_lock_flags+0x9/0x10
Dec 17 11:36:04 herbox kernel: [ 2206.139679]  [<ffffffff81134ba0>] ? __activate_page.part.9+0x170/0x170
Dec 17 11:36:04 herbox kernel: [ 2206.139687]  [<ffffffff81135811>] activate_page+0x91/0xb0
Dec 17 11:36:04 herbox kernel: [ 2206.139694]  [<ffffffff8113587b>] mark_page_accessed+0x4b/0x60
Dec 17 11:36:04 herbox kernel: [ 2206.139703]  [<ffffffff81129266>] do_generic_file_read.constprop.34+0x1d6/0x440
Dec 17 11:36:04 herbox kernel: [ 2206.139712]  [<ffffffff8112a23f>] generic_file_aio_read+0xef/0x280
Dec 17 11:36:04 herbox kernel: [ 2206.139722]  [<ffffffff8129b353>] ? fuse_do_getattr+0x163/0x1f0
Dec 17 11:36:04 herbox kernel: [ 2206.139730]  [<ffffffff8129cc08>] fuse_file_aio_read+0x78/0xa0
Dec 17 11:36:04 herbox kernel: [ 2206.139740]  [<ffffffff811886ca>] do_sync_read+0xda/0x120
Dec 17 11:36:04 herbox kernel: [ 2206.139750]  [<ffffffff812bbaa3>] ? security_file_permission+0x93/0xb0
Dec 17 11:36:04 herbox kernel: [ 2206.139758]  [<ffffffff81188b51>] ? rw_verify_area+0x61/0xf0
Dec 17 11:36:04 herbox kernel: [ 2206.139766]  [<ffffffff81189030>] vfs_read+0xb0/0x180
Dec 17 11:36:04 herbox kernel: [ 2206.139774]  [<ffffffff8118914a>] sys_read+0x4a/0x90
Dec 17 11:36:04 herbox kernel: [ 2206.139784]  [<ffffffff816a7729>] system_call_fastpath+0x16/0x1b
Dec 17 11:36:04 herbox kernel: [ 2206.139788] Code: 90 48 89 75 c8 48 8b 37 49 89 fe 48 89 55 c0 85 f6 0f 84 b4 00 00 00 45 31 ff 31 db 45 31 e4 0f 1f 40 00 49 63 c4 4d 8b 6c c6 10 <49> 8b 45 00 48 89 c1 48 c1 e8 38 83 e0 03 48 c1 e9 3a 48 8d 14 
Dec 17 11:36:04 herbox kernel: [ 2206.139868] RIP  [<ffffffff81135300>] pagevec_lru_move_fn+0x40/0x110
Dec 17 11:36:04 herbox kernel: [ 2206.139876]  RSP <ffff8801ff08dbd8>
Dec 17 11:36:04 herbox kernel: [ 2206.139912] ---[ end trace bbc7c1fc73cca7cb ]---
Dec 17 11:36:04 herbox kernel: [ 2206.249252] BUG: unable to handle kernel NULL pointer dereference at 0000000000000005
Dec 17 11:36:04 herbox kernel: [ 2206.249266] IP: [<ffffffff81135300>] pagevec_lru_move_fn+0x40/0x110
Dec 17 11:36:04 herbox kernel: [ 2206.249281] PGD 2092cf067 PUD 1f9775067 PMD 0 
Dec 17 11:36:04 herbox kernel: [ 2206.249291] Oops: 0000 [#3] SMP 
Dec 17 11:36:04 herbox kernel: [ 2206.249298] CPU 2 
Dec 17 11:36:04 herbox kernel: [ 2206.249301] Modules linked in: rfcomm bnep bluetooth parport_pc ppdev lp parport kvm snd_hda_codec_hdmi snd_hda_codec_realtek arc4 snd_hda_intel snd_hda_codec radeon rt2800pci ttm rt2800lib crc_ccitt snd_seq_midi snd_rawmidi drm_kms_helper rt2x00pci rt2x00lib drm edac_core snd_hwdep snd_seq_midi_event mac80211 snd_pcm snd_seq joydev cfg80211 snd_timer mac_hid i2c_algo_bit edac_mce_amd snd_seq_device sp5100_tco shpchp psmouse snd k10temp serio_raw soundcore snd_page_alloc eeprom_93cx6 i2c_piix4 wmi microcode asus_atk0110 hid_generic hid_logitech_dj firewire_ohci usbhid firewire_core hid crc_itu_t r8169 pata_atiixp ahci libahci pata_via
Dec 17 11:36:04 herbox kernel: [ 2206.249396] 
Dec 17 11:36:04 herbox kernel: [ 2206.249403] Pid: 2806, comm: unity-panel-ser Tainted: G      D W    3.5.0-44-generic #67~precise1-Ubuntu System manufacturer System Product Name/M5A88-V EVO
Dec 17 11:36:04 herbox kernel: [ 2206.249412] RIP: 0010:[<ffffffff81135300>]  [<ffffffff81135300>] pagevec_lru_move_fn+0x40/0x110
Dec 17 11:36:04 herbox kernel: [ 2206.249422] RSP: 0018:ffff8801f96bbd78  EFLAGS: 00010087
Dec 17 11:36:04 herbox kernel: [ 2206.249427] RAX: 000000000000000e RBX: ffff88021fffcd00 RCX: 0000000000016e08
Dec 17 11:36:04 herbox kernel: [ 2206.249432] RDX: 0000000000000002 RSI: ffffea0005f18f80 RDI: ffff88021fffcd00
Dec 17 11:36:04 herbox kernel: [ 2206.249436] RBP: ffff8801f96bbdc8 R08: 00007fc53e5f4000 R09: 00000000ffffffff
Dec 17 11:36:04 herbox kernel: [ 2206.249440] R10: 0000000000000000 R11: 0000000000000000 R12: 000000000000000e
Dec 17 11:36:04 herbox kernel: [ 2206.249445] R13: 0000000000000005 R14: ffff88021fc902e0 R15: 0000000000000282
Dec 17 11:36:04 herbox kernel: [ 2206.249450] FS:  00007fc53e5cf940(0000) GS:ffff88021fc80000(0000) knlGS:0000000000000000
Dec 17 11:36:04 herbox kernel: [ 2206.249455] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Dec 17 11:36:04 herbox kernel: [ 2206.249459] CR2: 0000000000000005 CR3: 00000002120fe000 CR4: 00000000000007e0
Dec 17 11:36:04 herbox kernel: [ 2206.249464] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 17 11:36:04 herbox kernel: [ 2206.249468] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 17 11:36:04 herbox kernel: [ 2206.249473] Process unity-panel-ser (pid: 2806, threadinfo ffff8801f96ba000, task ffff8801f9650000)
Dec 17 11:36:04 herbox kernel: [ 2206.249477] Stack:
Dec 17 11:36:04 herbox kernel: [ 2206.249480]  ffff8801f96bbdb8 ffff88021fffcd00 0000000000000000 ffffffff81134de0
Dec 17 11:36:04 herbox kernel: [ 2206.249490]  0000000000000aea 0000000000000002 ffff88021fc902e0 0000000000000000
Dec 17 11:36:04 herbox kernel: [ 2206.249498]  ffff8801f8d76b00 00007fc53e5f4000 ffff8801f96bbdd8 ffffffff811353e7
Dec 17 11:36:04 herbox kernel: [ 2206.249506] Call Trace:
Dec 17 11:36:04 herbox kernel: [ 2206.249516]  [<ffffffff81134de0>] ? lru_deactivate_fn+0x40/0x40
Dec 17 11:36:04 herbox kernel: [ 2206.249524]  [<ffffffff811353e7>] __pagevec_lru_add+0x17/0x20
Dec 17 11:36:04 herbox kernel: [ 2206.249532]  [<ffffffff81135a7b>] lru_add_drain_cpu+0x9b/0xf0
Dec 17 11:36:04 herbox kernel: [ 2206.249539]  [<ffffffff81135b76>] lru_add_drain+0x16/0x20
Dec 17 11:36:04 herbox kernel: [ 2206.249546]  [<ffffffff8115474c>] unmap_region+0x4c/0x110
Dec 17 11:36:04 herbox kernel: [ 2206.249554]  [<ffffffff8117542b>] ? kfree+0x3b/0x140
Dec 17 11:36:04 herbox kernel: [ 2206.249562]  [<ffffffff8108086a>] ? lg_local_unlock+0x1a/0x20
Dec 17 11:36:04 herbox kernel: [ 2206.249570]  [<ffffffff811a7a86>] ? mntput_no_expire+0x46/0x160
Dec 17 11:36:04 herbox kernel: [ 2206.249577]  [<ffffffff811548a2>] ? detach_vmas_to_be_unmapped+0x92/0xe0
Dec 17 11:36:04 herbox kernel: [ 2206.249585]  [<ffffffff811564ad>] do_munmap+0x1cd/0x300
Dec 17 11:36:04 herbox kernel: [ 2206.249592]  [<ffffffff8115662e>] vm_munmap+0x4e/0x70
Dec 17 11:36:04 herbox kernel: [ 2206.249599]  [<ffffffff8115744b>] sys_munmap+0x2b/0x40
Dec 17 11:36:04 herbox kernel: [ 2206.249608]  [<ffffffff816a7729>] system_call_fastpath+0x16/0x1b
Dec 17 11:36:04 herbox kernel: [ 2206.249612] Code: 90 48 89 75 c8 48 8b 37 49 89 fe 48 89 55 c0 85 f6 0f 84 b4 00 00 00 45 31 ff 31 db 45 31 e4 0f 1f 40 00 49 63 c4 4d 8b 6c c6 10 <49> 8b 45 00 48 89 c1 48 c1 e8 38 83 e0 03 48 c1 e9 3a 48 8d 14 
Dec 17 11:36:04 herbox kernel: [ 2206.249692] RIP  [<ffffffff81135300>] pagevec_lru_move_fn+0x40/0x110
Dec 17 11:36:04 herbox kernel: [ 2206.249699]  RSP <ffff8801f96bbd78>
Dec 17 11:36:04 herbox kernel: [ 2206.249702] CR2: 0000000000000005
Dec 17 11:36:04 herbox kernel: [ 2206.249708] ---[ end trace bbc7c1fc73cca7cc ]---


```

Thanks in advanced,
Brynn Cassie

---

### Post by brynn.west on 2013-12-17
So reproduced another crash (it sounds so much nicer that way) and after reading [this post]("http://askubuntu.com/questions/237090/tons-of-general-protection-faults") it makes me pretty sure it has to be hardware, but memtest still checks out. With all the references to M5A88-V EVO, it seems that it should be the motherboard? Or perhaps the graphics card on the motherboard? 

Can someone confirm that I'm thinking of this correctly? Or is it more likly another issue? I'd rather be a bit more sure before I look into motherboard replacements...

More output:
```
Dec 17 23:06:02 herbox kernel: [  536.008910] general protection fault: 0000 [#5] SMP 
Dec 17 23:06:02 herbox kernel: [  536.009020] CPU 2 
Dec 17 23:06:02 herbox kernel: [  536.009057] Modules linked in: parport_pc ppdev rfcomm bnep bluetooth snd_hda_codec_hdmi kvm snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi wmi snd_rawmidi snd_seq_midi_event asus_atk0110 snd_seq snd_timer snd_seq_device arc4 snd rt2800pci rt2800lib crc_ccitt rt2x00pci rt2x00lib joydev mac80211 radeon psmouse cfg80211 eeprom_93cx6 microcode serio_raw ttm drm_kms_helper drm i2c_algo_bit k10temp edac_core edac_mce_amd soundcore snd_page_alloc sp5100_tco i2c_piix4 mac_hid shpchp lp parport hid_generic hid_logitech_dj firewire_ohci usbhid hid r8169 ahci libahci pata_atiixp pata_via firewire_core crc_itu_t
Dec 17 23:06:02 herbox kernel: [  536.010466] 
Dec 17 23:06:02 herbox kernel: [  536.010480] Pid: 2055, comm: unity-panel-ser Tainted: G      D      3.5.0-44-generic #67~precise1-Ubuntu System manufacturer System Product Name/M5A88-V EVO
Dec 17 23:06:02 herbox kernel: [  536.010719] RIP: 0010:[<ffffffff8117514a>]  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:06:02 herbox kernel: [  536.010867] RSP: 0018:ffff8800370add38  EFLAGS: 00010282
Dec 17 23:06:02 herbox kernel: [  536.010955] RAX: 0000000000000000 RBX: 00007ff4f32cd000 RCX: 0000000000019aad
Dec 17 23:06:02 herbox kernel: [  536.011067] RDX: 0000000000019aac RSI: 00000000000080d0 RDI: 0000000000016ff0
Dec 17 23:06:02 herbox kernel: [  536.011179] RBP: ffff8800370add88 R08: ffff88011fc96ff0 R09: 0000000000000001
Dec 17 23:06:02 herbox kernel: [  536.011291] R10: 0000000000000071 R11: ffff8800cce63580 R12: ffff88011b406b00
Dec 17 23:06:02 herbox kernel: [  536.011403] R13: ff7f8800c9115d10 R14: ffffffff81156e8a R15: 00000000000080d0
Dec 17 23:06:02 herbox kernel: [  536.011518] FS:  00007ff4f32a9940(0000) GS:ffff88011fc80000(0000) knlGS:00000000f73fcb00
Dec 17 23:06:02 herbox kernel: [  536.011644] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Dec 17 23:06:02 herbox kernel: [  536.011736] CR2: 000000000a4d303c CR3: 00000000cccfb000 CR4: 00000000000007e0
Dec 17 23:06:02 herbox kernel: [  536.011848] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 17 23:06:02 herbox kernel: [  536.011961] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 17 23:06:02 herbox kernel: [  536.012074] Process unity-panel-ser (pid: 2055, threadinfo ffff8800370ac000, task ffff880115811700)
Dec 17 23:06:02 herbox kernel: [  536.012213] Stack:
Dec 17 23:06:02 herbox kernel: [  536.018865]  ffff880114f6fa8b ffff8800370ade58 0000000000000001 ffff8800c1624700
Dec 17 23:06:02 herbox kernel: [  536.025683]  ffff8800370add68 00007ff4f32cd000 ffff88010406b100 ffff8800c1624700
Dec 17 23:06:02 herbox kernel: [  536.032506]  0000000000001000 0000000000000000 ffff8800370ade48 ffffffff81156e8a
Dec 17 23:06:02 herbox kernel: [  536.039313] Call Trace:
Dec 17 23:06:02 herbox kernel: [  536.046041]  [<ffffffff81156e8a>] mmap_region+0x39a/0x610
Dec 17 23:06:02 herbox kernel: [  536.052679]  [<ffffffff81157340>] do_mmap_pgoff+0x240/0x320
Dec 17 23:06:02 herbox kernel: [  536.059183]  [<ffffffff81144bc6>] vm_mmap_pgoff+0x86/0xb0
Dec 17 23:06:02 herbox kernel: [  536.065509]  [<ffffffff81155ea8>] sys_mmap_pgoff+0xc8/0x1f0
Dec 17 23:06:02 herbox kernel: [  536.071696]  [<ffffffff81018932>] sys_mmap+0x22/0x30
Dec 17 23:06:02 herbox kernel: [  536.077711]  [<ffffffff816a7729>] system_call_fastpath+0x16/0x1b
Dec 17 23:06:02 herbox kernel: [  536.083764] Code: 00 4d 8b 04 24 65 4c 03 04 25 48 dc 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 e8 00 00 00 49 63 44 24 20 49 8b 3c 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0f 0f 94 c0 84 c0 74 c2 49 
Dec 17 23:06:02 herbox kernel: [  536.096550] RIP  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:06:02 herbox kernel: [  536.102628]  RSP <ffff8800370add38>
Dec 17 23:06:02 herbox kernel: [  536.108698] ---[ end trace eeb414fcdfbff28f ]---
Dec 17 23:06:09 herbox kernel: [  542.487983] general protection fault: 0000 [#6] SMP 
Dec 17 23:06:09 herbox kernel: [  542.494114] CPU 2 
Dec 17 23:06:09 herbox kernel: [  542.494150] Modules linked in: parport_pc ppdev rfcomm bnep bluetooth snd_hda_codec_hdmi kvm snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi wmi snd_rawmidi snd_seq_midi_event asus_atk0110 snd_seq snd_timer snd_seq_device arc4 snd rt2800pci rt2800lib crc_ccitt rt2x00pci rt2x00lib joydev mac80211 radeon psmouse cfg80211 eeprom_93cx6 microcode serio_raw ttm drm_kms_helper drm i2c_algo_bit k10temp edac_core edac_mce_amd soundcore snd_page_alloc sp5100_tco i2c_piix4 mac_hid shpchp lp parport hid_generic hid_logitech_dj firewire_ohci usbhid hid r8169 ahci libahci pata_atiixp pata_via firewire_core crc_itu_t
Dec 17 23:06:09 herbox kernel: [  542.533214] 
Dec 17 23:06:09 herbox kernel: [  542.539760] Pid: 3254, comm: wine-browser Tainted: G      D      3.5.0-44-generic #67~precise1-Ubuntu System manufacturer System Product Name/M5A88-V EVO
Dec 17 23:06:09 herbox kernel: [  542.546674] RIP: 0010:[<ffffffff8117514a>]  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:06:09 herbox kernel: [  542.553587] RSP: 0018:ffff8800c14d3dd8  EFLAGS: 00010282
Dec 17 23:06:09 herbox kernel: [  542.560411] RAX: 0000000000000000 RBX: ffff88010406c600 RCX: 0000000000019aad
Dec 17 23:06:09 herbox kernel: [  542.567259] RDX: 0000000000019aac RSI: 00000000000080d0 RDI: 0000000000016ff0
Dec 17 23:06:09 herbox kernel: [  542.574077] RBP: ffff8800c14d3e28 R08: ffff88011fc96ff0 R09: dead000000200200
Dec 17 23:06:09 herbox kernel: [  542.580903] R10: ffffea0003244ac0 R11: 0000000000000001 R12: ffff88011b406b00
Dec 17 23:06:09 herbox kernel: [  542.587708] R13: ff7f8800c9115d10 R14: ffffffff8118f05c R15: 00000000000080d0
Dec 17 23:06:09 herbox kernel: [  542.594521] FS:  00007faea881f700(0000) GS:ffff88011fc80000(0000) knlGS:00000000f73fcb00
Dec 17 23:06:09 herbox kernel: [  542.601405] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Dec 17 23:06:09 herbox kernel: [  542.608311] CR2: 00007faea826a3ec CR3: 00000000c0e40000 CR4: 00000000000007e0
Dec 17 23:06:09 herbox kernel: [  542.615276] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 17 23:06:09 herbox kernel: [  542.622252] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 17 23:06:09 herbox kernel: [  542.629210] Process wine-browser (pid: 3254, threadinfo ffff8800c14d2000, task ffff8800aa309700)
Dec 17 23:06:09 herbox kernel: [  542.636109] Stack:
Dec 17 23:06:09 herbox kernel: [  542.642819]  ffff88010406c600 ffff880118d1d100 ffff8800c14d3f58 0000000001385728
Dec 17 23:06:09 herbox kernel: [  542.649644]  ffff8800c14d3e08 ffff88010406c600 ffff88010406c600 ffff880118d1d100
Dec 17 23:06:09 herbox kernel: [  542.656473]  ffff8800c14d3f58 0000000001385728 ffff8800c14d3e68 ffffffff8118f05c
Dec 17 23:06:09 herbox kernel: [  542.663298] Call Trace:
Dec 17 23:06:09 herbox kernel: [  542.670068]  [<ffffffff8118f05c>] __bprm_mm_init+0x3c/0x150
Dec 17 23:06:09 herbox kernel: [  542.676889]  [<ffffffff81190748>] bprm_mm_init+0x78/0x90
Dec 17 23:06:09 herbox kernel: [  542.683560]  [<ffffffff81190aa1>] do_execve_common.isra.30+0x171/0x350
Dec 17 23:06:09 herbox kernel: [  542.690131]  [<ffffffff81190c9b>] do_execve+0x1b/0x20
Dec 17 23:06:09 herbox kernel: [  542.696517]  [<ffffffff8101d6c7>] sys_execve+0x47/0x70
Dec 17 23:06:09 herbox kernel: [  542.702759]  [<ffffffff816a7b6c>] stub_execve+0x6c/0xc0
Dec 17 23:06:09 herbox kernel: [  542.708839] Code: 00 4d 8b 04 24 65 4c 03 04 25 48 dc 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 e8 00 00 00 49 63 44 24 20 49 8b 3c 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0f 0f 94 c0 84 c0 74 c2 49 
Dec 17 23:06:09 herbox kernel: [  542.722019] RIP  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:06:09 herbox kernel: [  542.728213]  RSP <ffff8800c14d3dd8>
Dec 17 23:06:09 herbox kernel: [  542.734393] ---[ end trace eeb414fcdfbff290 ]---
Dec 17 23:06:58 herbox kernel: [  591.498300] general protection fault: 0000 [#7] SMP 
Dec 17 23:06:58 herbox kernel: [  591.504452] CPU 2 
Dec 17 23:06:58 herbox kernel: [  591.504489] Modules linked in: parport_pc ppdev rfcomm bnep bluetooth snd_hda_codec_hdmi kvm snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi wmi snd_rawmidi snd_seq_midi_event asus_atk0110 snd_seq snd_timer snd_seq_device arc4 snd rt2800pci rt2800lib crc_ccitt rt2x00pci rt2x00lib joydev mac80211 radeon psmouse cfg80211 eeprom_93cx6 microcode serio_raw ttm drm_kms_helper drm i2c_algo_bit k10temp edac_core edac_mce_amd soundcore snd_page_alloc sp5100_tco i2c_piix4 mac_hid shpchp lp parport hid_generic hid_logitech_dj firewire_ohci usbhid hid r8169 ahci libahci pata_atiixp pata_via firewire_core crc_itu_t
Dec 17 23:06:58 herbox kernel: [  591.544040] 
Dec 17 23:06:58 herbox kernel: [  591.550635] Pid: 1092, comm: whoopsie Tainted: G      D      3.5.0-44-generic #67~precise1-Ubuntu System manufacturer System Product Name/M5A88-V EVO
Dec 17 23:06:58 herbox kernel: [  591.557581] RIP: 0010:[<ffffffff8117514a>]  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:06:58 herbox kernel: [  591.564591] RSP: 0018:ffff880100d33d38  EFLAGS: 00010282
Dec 17 23:06:58 herbox kernel: [  591.571538] RAX: 0000000000000000 RBX: 00007f04bf616000 RCX: 0000000000019aad
Dec 17 23:06:58 herbox kernel: [  591.578469] RDX: 0000000000019aac RSI: 00000000000080d0 RDI: 0000000000016ff0
Dec 17 23:06:58 herbox kernel: [  591.585355] RBP: ffff880100d33d88 R08: ffff88011fc96ff0 R09: 0000000000000001
Dec 17 23:06:58 herbox kernel: [  591.592242] R10: 0000000000100073 R11: ffff880100ca0580 R12: ffff88011b406b00
Dec 17 23:06:58 herbox kernel: [  591.599136] R13: ff7f8800c9115d10 R14: ffffffff81156e8a R15: 00000000000080d0
Dec 17 23:06:58 herbox kernel: [  591.606009] FS:  00007f04b8fcd7c0(0000) GS:ffff88011fc80000(0000) knlGS:00000000132dfb40
Dec 17 23:06:58 herbox kernel: [  591.612917] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Dec 17 23:06:58 herbox kernel: [  591.619847] CR2: 000000000a50703c CR3: 0000000102997000 CR4: 00000000000007e0
Dec 17 23:06:58 herbox kernel: [  591.626849] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 17 23:06:58 herbox kernel: [  591.633850] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 17 23:06:58 herbox kernel: [  591.640843] Process whoopsie (pid: 1092, threadinfo ffff880100d32000, task ffff880100c50000)
Dec 17 23:06:58 herbox kernel: [  591.647917] Stack:
Dec 17 23:06:58 herbox kernel: [  591.654804]  ffff88010406db00 0000000000000001 0000000000000001 0000000000001000
Dec 17 23:06:58 herbox kernel: [  591.661694]  ffff880100d33d78 00007f04bf616000 ffff88010406db00 0000000000000000
Dec 17 23:06:58 herbox kernel: [  591.668547]  0000000000001000 0000000000000000 ffff880100d33e48 ffffffff81156e8a
Dec 17 23:06:58 herbox kernel: [  591.675397] Call Trace:
Dec 17 23:06:58 herbox kernel: [  591.682183]  [<ffffffff81156e8a>] mmap_region+0x39a/0x610
Dec 17 23:06:58 herbox kernel: [  591.689009]  [<ffffffff81193c55>] ? putname+0x35/0x50
Dec 17 23:06:58 herbox kernel: [  591.695704]  [<ffffffff81157340>] do_mmap_pgoff+0x240/0x320
Dec 17 23:06:58 herbox kernel: [  591.702254]  [<ffffffff81144bc6>] vm_mmap_pgoff+0x86/0xb0
Dec 17 23:06:58 herbox kernel: [  591.708637]  [<ffffffff81155ee3>] sys_mmap_pgoff+0x103/0x1f0
Dec 17 23:06:58 herbox kernel: [  591.714875]  [<ffffffff81018932>] sys_mmap+0x22/0x30
Dec 17 23:06:58 herbox kernel: [  591.720949]  [<ffffffff816a7729>] system_call_fastpath+0x16/0x1b
Dec 17 23:06:58 herbox kernel: [  591.727057] Code: 00 4d 8b 04 24 65 4c 03 04 25 48 dc 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 e8 00 00 00 49 63 44 24 20 49 8b 3c 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0f 0f 94 c0 84 c0 74 c2 49 
Dec 17 23:06:58 herbox kernel: [  591.739969] RIP  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:06:58 herbox kernel: [  591.746105]  RSP <ffff880100d33d38>
Dec 17 23:06:58 herbox kernel: [  591.752250] ---[ end trace eeb414fcdfbff291 ]---
Dec 17 23:07:09 herbox kernel: [  602.679289] general protection fault: 0000 [#8] SMP 
Dec 17 23:07:09 herbox kernel: [  602.685452] CPU 2 
Dec 17 23:07:09 herbox kernel: [  602.685490] Modules linked in: parport_pc ppdev rfcomm bnep bluetooth snd_hda_codec_hdmi kvm snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi wmi snd_rawmidi snd_seq_midi_event asus_atk0110 snd_seq snd_timer snd_seq_device arc4 snd rt2800pci rt2800lib crc_ccitt rt2x00pci rt2x00lib joydev mac80211 radeon psmouse cfg80211 eeprom_93cx6 microcode serio_raw ttm drm_kms_helper drm i2c_algo_bit k10temp edac_core edac_mce_amd soundcore snd_page_alloc sp5100_tco i2c_piix4 mac_hid shpchp lp parport hid_generic hid_logitech_dj firewire_ohci usbhid hid r8169 ahci libahci pata_atiixp pata_via firewire_core crc_itu_t
Dec 17 23:07:09 herbox kernel: [  602.724721] 
Dec 17 23:07:09 herbox kernel: [  602.731280] Pid: 2243, comm: wine-browser Tainted: G      D      3.5.0-44-generic #67~precise1-Ubuntu System manufacturer System Product Name/M5A88-V EVO
Dec 17 23:07:09 herbox kernel: [  602.738228] RIP: 0010:[<ffffffff8117514a>]  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:07:09 herbox kernel: [  602.745152] RSP: 0018:ffff8800cbaf9cf0  EFLAGS: 00010282
Dec 17 23:07:09 herbox kernel: [  602.751998] RAX: 0000000000000000 RBX: ffff880104068000 RCX: 0000000000019aad
Dec 17 23:07:09 herbox kernel: [  602.758872] RDX: 0000000000019aac RSI: 00000000000000d0 RDI: 0000000000016ff0
Dec 17 23:07:09 herbox kernel: [  602.765725] RBP: ffff8800cbaf9d40 R08: ffff88011fc96ff0 R09: dead000000200200
Dec 17 23:07:09 herbox kernel: [  602.772590] R10: ffffea0002a863c0 R11: 0000000000016da0 R12: ffff88011b406b00
Dec 17 23:07:09 herbox kernel: [  602.779421] R13: ff7f8800c9115d10 R14: ffffffff8104fe0b R15: 00000000000000d0
Dec 17 23:07:09 herbox kernel: [  602.786275] FS:  00007faea881f700(0000) GS:ffff88011fc80000(0000) knlGS:00000000134dfb40
Dec 17 23:07:09 herbox kernel: [  602.793184] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Dec 17 23:07:09 herbox kernel: [  602.800095] CR2: 000000000138d788 CR3: 00000000cb851000 CR4: 00000000000007e0
Dec 17 23:07:09 herbox kernel: [  602.807064] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 17 23:07:09 herbox kernel: [  602.814023] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 17 23:07:09 herbox kernel: [  602.820978] Process wine-browser (pid: 2243, threadinfo ffff8800cbaf8000, task ffff8800cfa5dc00)
Dec 17 23:07:09 herbox kernel: [  602.827878] Stack:
Dec 17 23:07:09 herbox kernel: [  602.834585]  00000000000084d0 0000000000000000 ffff8800cfa5dc00 ffff8800cfa5dc00
Dec 17 23:07:09 herbox kernel: [  602.841417]  ffff8800cbaf9d60 ffff880104068000 ffff88010433a300 ffff8800c0c5a6e0
Dec 17 23:07:09 herbox kernel: [  602.848223]  0000000000000000 0000000000000000 ffff8800cbaf9dc0 ffffffff8104fe0b
Dec 17 23:07:09 herbox kernel: [  602.855046] Call Trace:
Dec 17 23:07:09 herbox kernel: [  602.861809]  [<ffffffff8104fe0b>] dup_mmap+0x13b/0x3f0
Dec 17 23:07:09 herbox kernel: [  602.868475]  [<ffffffff8105104b>] dup_mm+0xeb/0x240
Dec 17 23:07:09 herbox kernel: [  602.874989]  [<ffffffff810519e5>] copy_process.part.22+0x805/0xe70
Dec 17 23:07:09 herbox kernel: [  602.881378]  [<ffffffff810520c7>] copy_process+0x77/0x80
Dec 17 23:07:09 herbox kernel: [  602.887589]  [<ffffffff8105221a>] do_fork+0xfa/0x290
Dec 17 23:07:09 herbox kernel: [  602.893648]  [<ffffffff811a5d71>] ? alloc_fd+0xd1/0x120
Dec 17 23:07:09 herbox kernel: [  602.899719]  [<ffffffff8169eeae>] ? _raw_spin_lock+0xe/0x20
Dec 17 23:07:09 herbox kernel: [  602.905663]  [<ffffffff81186e41>] ? fd_install+0x61/0x80
Dec 17 23:07:09 herbox kernel: [  602.911481]  [<ffffffff81192e73>] ? do_pipe_flags+0xc3/0x120
Dec 17 23:07:09 herbox kernel: [  602.917253]  [<ffffffff8101d678>] sys_clone+0x28/0x30
Dec 17 23:07:09 herbox kernel: [  602.922982]  [<ffffffff816a7a33>] stub_clone+0x13/0x20
Dec 17 23:07:09 herbox kernel: [  602.928710]  [<ffffffff816a7729>] ? system_call_fastpath+0x16/0x1b
Dec 17 23:07:09 herbox kernel: [  602.934433] Code: 00 4d 8b 04 24 65 4c 03 04 25 48 dc 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 e8 00 00 00 49 63 44 24 20 49 8b 3c 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0f 0f 94 c0 84 c0 74 c2 49 
Dec 17 23:07:09 herbox kernel: [  602.946907] RIP  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:07:09 herbox kernel: [  602.952883]  RSP <ffff8800cbaf9cf0>
Dec 17 23:07:09 herbox kernel: [  602.958852] ---[ end trace eeb414fcdfbff292 ]---
Dec 17 23:07:13 herbox kernel: [  606.736117] general protection fault: 0000 [#9] SMP 
Dec 17 23:07:13 herbox kernel: [  606.742071] CPU 2 
Dec 17 23:07:13 herbox kernel: [  606.742109] Modules linked in: parport_pc ppdev rfcomm bnep bluetooth snd_hda_codec_hdmi kvm snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi wmi snd_rawmidi snd_seq_midi_event asus_atk0110 snd_seq snd_timer snd_seq_device arc4 snd rt2800pci rt2800lib crc_ccitt rt2x00pci rt2x00lib joydev mac80211 radeon psmouse cfg80211 eeprom_93cx6 microcode serio_raw ttm drm_kms_helper drm i2c_algo_bit k10temp edac_core edac_mce_amd soundcore snd_page_alloc sp5100_tco i2c_piix4 mac_hid shpchp lp parport hid_generic hid_logitech_dj firewire_ohci usbhid hid r8169 ahci libahci pata_atiixp pata_via firewire_core crc_itu_t
Dec 17 23:07:13 herbox kernel: [  606.780265] 
Dec 17 23:07:13 herbox kernel: [  606.786643] Pid: 2399, comm: firefox.exe Tainted: G      D      3.5.0-44-generic #67~precise1-Ubuntu System manufacturer System Product Name/M5A88-V EVO
Dec 17 23:07:13 herbox kernel: [  606.793340] RIP: 0010:[<ffffffff8117514a>]  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:07:13 herbox kernel: [  606.800051] RSP: 0018:ffff8800372cbdb8  EFLAGS: 00010282
Dec 17 23:07:13 herbox kernel: [  606.806774] RAX: 0000000000000000 RBX: ffff8800c0c456e0 RCX: 0000000000019aad
Dec 17 23:07:13 herbox kernel: [  606.813544] RDX: 0000000000019aac RSI: 00000000000000d0 RDI: 0000000000016ff0
Dec 17 23:07:13 herbox kernel: [  606.820345] RBP: ffff8800372cbe08 R08: ffff88011fc96ff0 R09: 0000000000000001
Dec 17 23:07:13 herbox kernel: [  606.827150] R10: 0000000000000000 R11: ffff8800372cbf30 R12: ffff88011b406b00
Dec 17 23:07:13 herbox kernel: [  606.833984] R13: ff7f8800c9115d10 R14: ffffffff811556e7 R15: 00000000000000d0
Dec 17 23:07:13 herbox kernel: [  606.840842] FS:  0000000081ff0000(0063) GS:ffff88011fc80000(006b) knlGS:000000000357fb40
Dec 17 23:07:13 herbox kernel: [  606.847610] CS:  0010 DS: 002b ES: 002b CR0: 0000000080050033
Dec 17 23:07:13 herbox kernel: [  606.854241] CR2: 0000000081f98018 CR3: 00000000cd2fe000 CR4: 00000000000007e0
Dec 17 23:07:13 herbox kernel: [  606.860878] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 17 23:07:13 herbox kernel: [  606.867495] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 17 23:07:13 herbox kernel: [  606.874077] Process firefox.exe (pid: 2399, threadinfo ffff8800372ca000, task ffff88003725c500)
Dec 17 23:07:13 herbox kernel: [  606.880727] Stack:
Dec 17 23:07:13 herbox kernel: [  606.887207]  0000000000000000 ffff8800cd15c078 0000000000006300 0000000000000032
Dec 17 23:07:13 herbox kernel: [  606.893704]  0000000000000000 ffff8800c0c456e0 ffff8800c0c456e0 0000000000100070
Dec 17 23:07:13 herbox kernel: [  606.900037]  0000000006300000 ffff880115cf4600 ffff8800372cbe58 ffffffff811556e7
Dec 17 23:07:13 herbox kernel: [  606.906235] Call Trace:
Dec 17 23:07:13 herbox kernel: [  606.912229]  [<ffffffff811556e7>] __split_vma+0x77/0x270
Dec 17 23:07:13 herbox kernel: [  606.918306]  [<ffffffff811562d0>] split_vma+0x20/0x30
Dec 17 23:07:13 herbox kernel: [  606.924240]  [<ffffffff81158398>] mprotect_fixup+0x228/0x2c0
Dec 17 23:07:13 herbox kernel: [  606.930045]  [<ffffffff811585d1>] sys_mprotect+0x1a1/0x250
Dec 17 23:07:13 herbox kernel: [  606.935790]  [<ffffffff8104bfee>] sys32_mprotect+0xe/0x10
Dec 17 23:07:13 herbox kernel: [  606.941496]  [<ffffffff816a8f76>] cstar_dispatch+0x7/0x21
Dec 17 23:07:13 herbox kernel: [  606.947184] Code: 00 4d 8b 04 24 65 4c 03 04 25 48 dc 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 e8 00 00 00 49 63 44 24 20 49 8b 3c 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0f 0f 94 c0 84 c0 74 c2 49 
Dec 17 23:07:13 herbox kernel: [  606.959613] RIP  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:07:13 herbox kernel: [  606.965602]  RSP <ffff8800372cbdb8>
Dec 17 23:07:13 herbox kernel: [  606.971553] ---[ end trace eeb414fcdfbff293 ]---
Dec 17 23:07:42 herbox kernel: [  634.901909] general protection fault: 0000 [#10] SMP 
Dec 17 23:07:42 herbox kernel: [  634.907868] CPU 2 
Dec 17 23:07:42 herbox kernel: [  634.907905] Modules linked in: parport_pc ppdev rfcomm bnep bluetooth snd_hda_codec_hdmi kvm snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi wmi snd_rawmidi snd_seq_midi_event asus_atk0110 snd_seq snd_timer snd_seq_device arc4 snd rt2800pci rt2800lib crc_ccitt rt2x00pci rt2x00lib joydev mac80211 radeon psmouse cfg80211 eeprom_93cx6 microcode serio_raw ttm drm_kms_helper drm i2c_algo_bit k10temp edac_core edac_mce_amd soundcore snd_page_alloc sp5100_tco i2c_piix4 mac_hid shpchp lp parport hid_generic hid_logitech_dj firewire_ohci usbhid hid r8169 ahci libahci pata_atiixp pata_via firewire_core crc_itu_t
Dec 17 23:07:42 herbox kernel: [  634.946014] 
Dec 17 23:07:42 herbox kernel: [  634.952367] Pid: 1957, comm: gnome-settings- Tainted: G      D      3.5.0-44-generic #67~precise1-Ubuntu System manufacturer System Product Name/M5A88-V EVO
Dec 17 23:07:42 herbox kernel: [  634.959065] RIP: 0010:[<ffffffff8117514a>]  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:07:42 herbox kernel: [  634.965769] RSP: 0018:ffff880100ff3e38  EFLAGS: 00010282
Dec 17 23:07:42 herbox kernel: [  634.972448] RAX: 0000000000000000 RBX: ffff880115d6e900 RCX: 0000000000019aad
Dec 17 23:07:42 herbox kernel: [  634.979200] RDX: 0000000000019aac RSI: 00000000000000d0 RDI: 0000000000016ff0
Dec 17 23:07:42 herbox kernel: [  634.985940] RBP: ffff880100ff3e88 R08: ffff88011fc96ff0 R09: 00000000ffffffff
Dec 17 23:07:42 herbox kernel: [  634.992713] R10: 0000000000000000 R11: 0000000000000206 R12: ffff88011b406b00
Dec 17 23:07:42 herbox kernel: [  634.999515] R13: ff7f8800c9115d10 R14: ffffffff811556e7 R15: 00000000000000d0
Dec 17 23:07:42 herbox kernel: [  635.006366] FS:  00007faf59ae1940(0000) GS:ffff88011fc80000(0000) knlGS:00000000134dfb40
Dec 17 23:07:42 herbox kernel: [  635.013267] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Dec 17 23:07:42 herbox kernel: [  635.020189] CR2: 00007faf59ac3000 CR3: 000000010197f000 CR4: 00000000000007e0
Dec 17 23:07:42 herbox kernel: [  635.027164] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 17 23:07:42 herbox kernel: [  635.034134] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 17 23:07:42 herbox kernel: [  635.041096] Process gnome-settings- (pid: 1957, threadinfo ffff880100ff2000, task ffff88010131c500)
Dec 17 23:07:42 herbox kernel: [  635.048138] Stack:
Dec 17 23:07:42 herbox kernel: [  635.055016]  ffff880100ff3e78 ffff8800c1624800 ffff88011fc8ed40 0000000000000246
Dec 17 23:07:42 herbox kernel: [  635.061888]  ffff880114f91cb0 ffff880115d6e900 ffff8800cfb516e0 ffff8800cfb516e0
Dec 17 23:07:42 herbox kernel: [  635.061895]  00007faf59ac4000 ffff880115d6e900 ffff880100ff3ed8 ffffffff811556e7
Dec 17 23:07:42 herbox kernel: [  635.061906] Call Trace:
Dec 17 23:07:42 herbox kernel: [  635.061909]  [<ffffffff811556e7>] __split_vma+0x77/0x270
Dec 17 23:07:42 herbox kernel: [  635.061916]  [<ffffffff811565c3>] do_munmap+0x2e3/0x300
Dec 17 23:07:42 herbox kernel: [  635.061922]  [<ffffffff8115662e>] vm_munmap+0x4e/0x70
Dec 17 23:07:42 herbox kernel: [  635.061926]  [<ffffffff8115744b>] sys_munmap+0x2b/0x40
Dec 17 23:07:42 herbox kernel: [  635.061931]  [<ffffffff816a7729>] system_call_fastpath+0x16/0x1b
Dec 17 23:07:42 herbox kernel: [  635.061938] Code: 00 4d 8b 04 24 65 4c 03 04 25 48 dc 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 e8 00 00 00 49 63 44 24 20 49 8b 3c 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0f 0f 94 c0 84 c0 74 c2 49 
Dec 17 23:07:42 herbox kernel: [  635.061999] RIP  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:07:42 herbox kernel: [  635.062005]  RSP <ffff880100ff3e38>
Dec 17 23:07:42 herbox kernel: [  635.062045] ---[ end trace eeb414fcdfbff294 ]---
Dec 17 23:10:47 herbox kernel: [  819.844294] general protection fault: 0000 [#11] SMP 
Dec 17 23:10:47 herbox kernel: [  819.851255] CPU 2 
Dec 17 23:10:47 herbox kernel: [  819.851293] Modules linked in: parport_pc ppdev rfcomm bnep bluetooth snd_hda_codec_hdmi kvm snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi wmi snd_rawmidi snd_seq_midi_event asus_atk0110 snd_seq snd_timer snd_seq_device arc4 snd rt2800pci rt2800lib crc_ccitt rt2x00pci rt2x00lib joydev mac80211 radeon psmouse cfg80211 eeprom_93cx6 microcode serio_raw ttm drm_kms_helper drm i2c_algo_bit k10temp edac_core edac_mce_amd soundcore snd_page_alloc sp5100_tco i2c_piix4 mac_hid shpchp lp parport hid_generic hid_logitech_dj firewire_ohci usbhid hid r8169 ahci libahci pata_atiixp pata_via firewire_core crc_itu_t
Dec 17 23:10:47 herbox kernel: [  819.895663] 
Dec 17 23:10:47 herbox kernel: [  819.902735] Pid: 1099, comm: irqbalance Tainted: G      D      3.5.0-44-generic #67~precise1-Ubuntu System manufacturer System Product Name/M5A88-V EVO
Dec 17 23:10:47 herbox kernel: [  819.910016] RIP: 0010:[<ffffffff8117514a>]  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:10:47 herbox kernel: [  819.917360] RSP: 0018:ffff880101345e38  EFLAGS: 00010282
Dec 17 23:10:47 herbox kernel: [  819.924559] RAX: 0000000000000000 RBX: ffff880115cf6c80 RCX: 0000000000019aad
Dec 17 23:10:47 herbox kernel: [  819.931693] RDX: 0000000000019aac RSI: 00000000000000d0 RDI: 0000000000016ff0
Dec 17 23:10:47 herbox kernel: [  819.938762] RBP: ffff880101345e88 R08: ffff88011fc96ff0 R09: 00000000ffffffff
Dec 17 23:10:47 herbox kernel: [  819.945828] R10: 3437313520343833 R11: 0000000000000206 R12: ffff88011b406b00
Dec 17 23:10:47 herbox kernel: [  819.952916] R13: ff7f8800c9115d10 R14: ffffffff811556e7 R15: 00000000000000d0
Dec 17 23:10:47 herbox kernel: [  819.960035] FS:  00007f8295f4b740(0000) GS:ffff88011fc80000(0000) knlGS:00000000028efb40
Dec 17 23:10:47 herbox kernel: [  819.967179] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Dec 17 23:10:47 herbox kernel: [  819.974308] CR2: 00007f8295f64000 CR3: 0000000100c77000 CR4: 00000000000007e0
Dec 17 23:10:47 herbox kernel: [  819.981452] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 17 23:10:47 herbox kernel: [  819.988539] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 17 23:10:47 herbox kernel: [  819.995591] Process irqbalance (pid: 1099, threadinfo ffff880101344000, task ffff880115e78000)
Dec 17 23:10:47 herbox kernel: [  820.002714] Stack:
Dec 17 23:10:47 herbox kernel: [  820.009826]  ffff880101345e78 ffff8800aa04ba00 ffff88011fc8ed40 0000000000000246
Dec 17 23:10:47 herbox kernel: [  820.017046]  ffff8800cf70f1a0 ffff880115cf6c80 ffff880118e48160 ffff880118e48160
Dec 17 23:10:47 herbox kernel: [  820.024200]  00007f8295f65000 ffff880115cf6c80 ffff880101345ed8 ffffffff811556e7
Dec 17 23:10:47 herbox kernel: [  820.031326] Call Trace:
Dec 17 23:10:47 herbox kernel: [  820.038411]  [<ffffffff811556e7>] __split_vma+0x77/0x270
Dec 17 23:10:47 herbox kernel: [  820.045537]  [<ffffffff811565c3>] do_munmap+0x2e3/0x300
Dec 17 23:10:47 herbox kernel: [  820.052607]  [<ffffffff8115662e>] vm_munmap+0x4e/0x70
Dec 17 23:10:47 herbox kernel: [  820.059634]  [<ffffffff8115744b>] sys_munmap+0x2b/0x40
Dec 17 23:10:47 herbox kernel: [  820.066671]  [<ffffffff816a7729>] system_call_fastpath+0x16/0x1b
Dec 17 23:10:47 herbox kernel: [  820.073709] Code: 00 4d 8b 04 24 65 4c 03 04 25 48 dc 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 e8 00 00 00 49 63 44 24 20 49 8b 3c 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0f 0f 94 c0 84 c0 74 c2 49 
Dec 17 23:10:47 herbox kernel: [  820.088917] RIP  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:10:47 herbox kernel: [  820.096333]  RSP <ffff880101345e38>
Dec 17 23:10:47 herbox kernel: [  820.103630] ---[ end trace eeb414fcdfbff295 ]---
Dec 17 23:12:39 herbox kernel: [  931.640589] general protection fault: 0000 [#12] SMP 
Dec 17 23:12:39 herbox kernel: [  931.647759] CPU 2 
Dec 17 23:12:39 herbox kernel: [  931.647796] Modules linked in: parport_pc ppdev rfcomm bnep bluetooth snd_hda_codec_hdmi kvm snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi wmi snd_rawmidi snd_seq_midi_event asus_atk0110 snd_seq snd_timer snd_seq_device arc4 snd rt2800pci rt2800lib crc_ccitt rt2x00pci rt2x00lib joydev mac80211 radeon psmouse cfg80211 eeprom_93cx6 microcode serio_raw ttm drm_kms_helper drm i2c_algo_bit k10temp edac_core edac_mce_amd soundcore snd_page_alloc sp5100_tco i2c_piix4 mac_hid shpchp lp parport hid_generic hid_logitech_dj firewire_ohci usbhid hid r8169 ahci libahci pata_atiixp pata_via firewire_core crc_itu_t
Dec 17 23:12:39 herbox kernel: [  931.692809] 
Dec 17 23:12:39 herbox kernel: [  931.700061] Pid: 2337, comm: wineserver Tainted: G      D      3.5.0-44-generic #67~precise1-Ubuntu System manufacturer System Product Name/M5A88-V EVO
Dec 17 23:12:39 herbox kernel: [  931.707520] RIP: 0010:[<ffffffff8117514a>]  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:12:39 herbox kernel: [  931.714867] RSP: 0018:ffff8800ccc69e48  EFLAGS: 00010282
Dec 17 23:12:39 herbox kernel: [  931.722230] RAX: 0000000000000000 RBX: ffff880115d6cd00 RCX: 0000000000019aad
Dec 17 23:12:39 herbox kernel: [  931.729514] RDX: 0000000000019aac RSI: 00000000000000d0 RDI: 0000000000016ff0
Dec 17 23:12:39 herbox kernel: [  931.736664] RBP: ffff8800ccc69e98 R08: ffff88011fc96ff0 R09: 00000000f75c4e14
Dec 17 23:12:39 herbox kernel: [  931.743782] R10: 0000000000000000 R11: 0000000000000282 R12: ffff88011b406b00
Dec 17 23:12:39 herbox kernel: [  931.750900] R13: ff7f8800c9115d10 R14: ffffffff811556e7 R15: 00000000000000d0
Dec 17 23:12:39 herbox kernel: [  931.758035] FS:  00007f783724d700(0000) GS:ffff88011fc80000(0063) knlGS:00000000f73fcb00
Dec 17 23:12:39 herbox kernel: [  931.765214] CS:  0010 DS: 002b ES: 002b CR0: 000000008005003b
Dec 17 23:12:39 herbox kernel: [  931.772373] CR2: 000000000a647034 CR3: 00000000c1bd6000 CR4: 00000000000007e0
Dec 17 23:12:39 herbox kernel: [  931.779562] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 17 23:12:39 herbox kernel: [  931.786704] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 17 23:12:39 herbox kernel: [  931.793778] Process wineserver (pid: 2337, threadinfo ffff8800ccc68000, task ffff880037259700)
Dec 17 23:12:39 herbox kernel: [  931.800893] Stack:
Dec 17 23:12:39 herbox kernel: [  931.807975]  ffff880037259700 0000000000000000 0000000000000000 0000000000000000
Dec 17 23:12:39 herbox kernel: [  931.815231]  ffff880115cbd898 ffff880115d6cd00 ffff8800c1a202c0 ffff8800c1a202c0
Dec 17 23:12:39 herbox kernel: [  931.822451]  000000000a667000 ffff880115d6cd00 ffff8800ccc69ee8 ffffffff811556e7
Dec 17 23:12:39 herbox kernel: [  931.829615] Call Trace:
Dec 17 23:12:39 herbox kernel: [  931.836676]  [<ffffffff811556e7>] __split_vma+0x77/0x270
Dec 17 23:12:39 herbox kernel: [  931.843642]  [<ffffffff811563ea>] do_munmap+0x10a/0x300
Dec 17 23:12:39 herbox kernel: [  931.850455]  [<ffffffff8118908d>] ? vfs_read+0x10d/0x180
Dec 17 23:12:39 herbox kernel: [  931.857126]  [<ffffffff81156ae1>] sys_brk+0x121/0x130
Dec 17 23:12:39 herbox kernel: [  931.863650]  [<ffffffff816a8f76>] cstar_dispatch+0x7/0x21
Dec 17 23:12:39 herbox kernel: [  931.870020] Code: 00 4d 8b 04 24 65 4c 03 04 25 48 dc 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 e8 00 00 00 49 63 44 24 20 49 8b 3c 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0f 0f 94 c0 84 c0 74 c2 49 
Dec 17 23:12:39 herbox kernel: [  931.883426] RIP  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:12:39 herbox kernel: [  931.889882]  RSP <ffff8800ccc69e48>
Dec 17 23:12:39 herbox kernel: [  931.896224] ---[ end trace eeb414fcdfbff296 ]---
Dec 17 23:12:44 herbox kernel: [  936.664855] general protection fault: 0000 [#13] SMP 
Dec 17 23:12:44 herbox kernel: [  936.671106] CPU 2 
Dec 17 23:12:44 herbox kernel: [  936.671142] Modules linked in: parport_pc ppdev rfcomm bnep bluetooth snd_hda_codec_hdmi kvm snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi wmi snd_rawmidi snd_seq_midi_event asus_atk0110 snd_seq snd_timer snd_seq_device arc4 snd rt2800pci rt2800lib crc_ccitt rt2x00pci rt2x00lib joydev mac80211 radeon psmouse cfg80211 eeprom_93cx6 microcode serio_raw ttm drm_kms_helper drm i2c_algo_bit k10temp edac_core edac_mce_amd soundcore snd_page_alloc sp5100_tco i2c_piix4 mac_hid shpchp lp parport hid_generic hid_logitech_dj firewire_ohci usbhid hid r8169 ahci libahci pata_atiixp pata_via firewire_core crc_itu_t
Dec 17 23:12:44 herbox kernel: [  936.710875] 
Dec 17 23:12:44 herbox kernel: [  936.717515] Pid: 2082, comm: indicator-print Tainted: G      D      3.5.0-44-generic #67~precise1-Ubuntu System manufacturer System Product Name/M5A88-V EVO
Dec 17 23:12:44 herbox kernel: [  936.724481] RIP: 0010:[<ffffffff8117514a>]  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:12:44 herbox kernel: [  936.731449] RSP: 0018:ffff880037123d38  EFLAGS: 00010282
Dec 17 23:12:44 herbox kernel: [  936.738412] RAX: 0000000000000000 RBX: 00007fc309785000 RCX: 0000000000019aad
Dec 17 23:12:44 herbox kernel: [  936.745455] RDX: 0000000000019aac RSI: 00000000000080d0 RDI: 0000000000016ff0
Dec 17 23:12:44 herbox kernel: [  936.752435] RBP: ffff880037123d88 R08: ffff88011fc96ff0 R09: 0000000000000001
Dec 17 23:12:44 herbox kernel: [  936.759361] R10: 00000000000000d1 R11: ffff88003710f9a0 R12: ffff88011b406b00
Dec 17 23:12:44 herbox kernel: [  936.766266] R13: ff7f8800c9115d10 R14: ffffffff81156e8a R15: 00000000000080d0
Dec 17 23:12:44 herbox kernel: [  936.773188] FS:  00007fc3009e1940(0000) GS:ffff88011fc80000(0000) knlGS:00000000f73fcb00
Dec 17 23:12:44 herbox kernel: [  936.780157] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Dec 17 23:12:44 herbox kernel: [  936.787090] CR2: 00007fc307fee210 CR3: 00000000c9298000 CR4: 00000000000007e0
Dec 17 23:12:44 herbox kernel: [  936.794069] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Dec 17 23:12:44 herbox kernel: [  936.801053] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Dec 17 23:12:44 herbox kernel: [  936.808041] Process indicator-print (pid: 2082, threadinfo ffff880037122000, task ffff8800c92b1700)
Dec 17 23:12:44 herbox kernel: [  936.815135] Stack:
Dec 17 23:12:44 herbox kernel: [  936.822183]  ffff880119635005 0000000000000000 0000000000000001 ffff880116f59230
Dec 17 23:12:44 herbox kernel: [  936.829241]  ffff880037123d68 00007fc309785000 ffff880115cf6200 ffff8800c1bac600
Dec 17 23:12:44 herbox kernel: [  936.836158]  0000000000001000 0000000000000000 ffff880037123e48 ffffffff81156e8a
Dec 17 23:12:44 herbox kernel: [  936.843060] Call Trace:
Dec 17 23:12:44 herbox kernel: [  936.849887]  [<ffffffff81156e8a>] mmap_region+0x39a/0x610
Dec 17 23:12:44 herbox kernel: [  936.856753]  [<ffffffff81157340>] do_mmap_pgoff+0x240/0x320
Dec 17 23:12:44 herbox kernel: [  936.863613]  [<ffffffff81144bc6>] vm_mmap_pgoff+0x86/0xb0
Dec 17 23:12:44 herbox kernel: [  936.870318]  [<ffffffff81155ea8>] sys_mmap_pgoff+0xc8/0x1f0
Dec 17 23:12:44 herbox kernel: [  936.876878]  [<ffffffff81018932>] sys_mmap+0x22/0x30
Dec 17 23:12:44 herbox kernel: [  936.883269]  [<ffffffff816a7729>] system_call_fastpath+0x16/0x1b
Dec 17 23:12:44 herbox kernel: [  936.889524] Code: 00 4d 8b 04 24 65 4c 03 04 25 48 dc 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 e8 00 00 00 49 63 44 24 20 49 8b 3c 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0f 0f 94 c0 84 c0 74 c2 49 
Dec 17 23:12:44 herbox kernel: [  936.902844] RIP  [<ffffffff8117514a>] kmem_cache_alloc+0x5a/0x150
Dec 17 23:12:44 herbox kernel: [  936.909191]  RSP <ffff880037123d38>
Dec 17 23:12:44 herbox kernel: [  936.915438] ---[ end trace eeb414fcdfbff297 ]---


```

---

### Post by brynn.west on 2014-01-03
After replacing my MB and GPU I get another lock up. This time while listening to music. Open applications were Clementine 1.2.1 and Firefox.

Could this be overheating? The CPU? Is it possibally NOT hardware? Any idea? Anything usful I can provide?

Here is the latest syslog output right before crash:
```

Jan  3 01:35:15 herbox AptDaemon: INFO: Quitting due to inactivity
Jan  3 01:35:15 herbox AptDaemon: INFO: Quitting was requested
Jan  3 02:01:14 herbox kernel: [ 2091.764073] type=1400 audit(1388732474.834:32): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1101 comm="cupsd" pid=1101 comm="cupsd" capability=36  capname="block_suspend"
Jan  3 02:15:14 herbox kernel: [ 2931.240419] type=1400 audit(1388733314.782:33): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1101 comm="cupsd" pid=1101 comm="cupsd" capability=36  capname="block_suspend"
Jan  3 02:17:01 herbox CRON[4303]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  3 02:29:14 herbox kernel: [ 3770.896171] type=1400 audit(1388734154.914:34): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1101 comm="cupsd" pid=1101 comm="cupsd" capability=36  capname="block_suspend"
Jan  3 03:17:01 herbox CRON[5410]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  3 03:27:33 herbox ntfs-3g[6538]: Version 2012.1.15AR.1 external FUSE 28
Jan  3 03:27:33 herbox ntfs-3g[6538]: Mounted /dev/sdc1 (Read-Write, label "TheHole", NTFS 3.1)
Jan  3 03:27:33 herbox ntfs-3g[6538]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177
Jan  3 03:27:33 herbox ntfs-3g[6538]: Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,default_permissions,fsname=/dev/sdc1,blkdev,blksize=4096
Jan  3 03:27:33 herbox ntfs-3g[6538]: Global ownership and permissions enforced, configuration type 7

```

This is the start of the crash:
```

Jan  3 03:45:42 herbox kernel: [ 8355.637539] general protection fault: 0000 [#1] SMP 
Jan  3 03:45:42 herbox kernel: [ 8355.637550] CPU 2 
Jan  3 03:45:42 herbox kernel: [ 8355.637553] Modules linked in: rfcomm bnep bluetooth parport_pc ppdev nvidia(PO) snd_hda_codec_hdmi joydev hid_logitech_dj hid_generic snd_hda_codec_realtek usbhid snd_hda_intel snd_hda_codec hid snd_hwdep snd_pcm arc4 rt2800pci rt2800lib snd_seq_midi snd_rawmidi crc_ccitt snd_seq_midi_event snd_seq rt2x00pci snd_timer rt2x00lib snd_seq_device mac80211 snd soundcore kvm_amd kvm cfg80211 snd_page_alloc eeepc_wmi asus_wmi mxm_wmi sparse_keymap k10temp wmi microcode edac_core psmouse eeprom_93cx6 edac_mce_amd serio_raw sp5100_tco mac_hid i2c_piix4 lp parport r8169
Jan  3 03:45:42 herbox kernel: [ 8355.637637] 
Jan  3 03:45:42 herbox kernel: [ 8355.637643] Pid: 1121, comm: Xorg Tainted: P           O 3.5.0-23-generic #35~precise1-Ubuntu To be filled by O.E.M. To be filled by O.E.M./M5A97 LE R2.0
Jan  3 03:45:42 herbox kernel: [ 8355.637652] RIP: 0010:[<ffffffff811737ab>]  [<ffffffff811737ab>] __kmalloc+0x7b/0x1a0
Jan  3 03:45:42 herbox kernel: [ 8355.637666] RSP: 0018:ffff880211817c48  EFLAGS: 00010282
Jan  3 03:45:42 herbox kernel: [ 8355.637671] RAX: 0000000000000000 RBX: ffff880211ea5e58 RCX: 000000000008d55a
Jan  3 03:45:42 herbox kernel: [ 8355.637675] RDX: 000000000008d559 RSI: 0000000000000000 RDI: 0000000000016770
Jan  3 03:45:42 herbox kernel: [ 8355.637679] RBP: ffff880211817c98 R08: ffff88021fd16770 R09: 00007ffff0a0a54c
Jan  3 03:45:42 herbox kernel: [ 8355.637683] R10: 0000000000000000 R11: 0000000000003246 R12: ffff880217002500
Jan  3 03:45:42 herbox kernel: [ 8355.637687] R13: ff7f8802106b9ae0 R14: 00000000000002d0 R15: ffffffffa098f66d
Jan  3 03:45:42 herbox kernel: [ 8355.637692] FS:  00007f6e3e463880(0000) GS:ffff88021fd00000(0000) knlGS:00000000f7399b00
Jan  3 03:45:42 herbox kernel: [ 8355.637696] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Jan  3 03:45:42 herbox kernel: [ 8355.637700] CR2: 00007f266014c000 CR3: 000000020fb3d000 CR4: 00000000000007e0
Jan  3 03:45:42 herbox kernel: [ 8355.637705] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jan  3 03:45:42 herbox kernel: [ 8355.637709] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jan  3 03:45:42 herbox kernel: [ 8355.637714] Process Xorg (pid: 1121, threadinfo ffff880211816000, task ffff88020fc90000)
Jan  3 03:45:42 herbox kernel: [ 8355.637716] Stack:
Jan  3 03:45:42 herbox kernel: [ 8355.637719]  0000000000000000 ffffffffa098f66d 0000000000000010 0000000000000010
Jan  3 03:45:42 herbox kernel: [ 8355.637730]  0000000000000000 ffff880211ea5e58 0000000000000010 0000000000000010
Jan  3 03:45:42 herbox kernel: [ 8355.637738]  0000000000000000 ffff880211845480 ffff880211817cc8 ffffffffa098f66d
Jan  3 03:45:42 herbox kernel: [ 8355.637746] Call Trace:
Jan  3 03:45:42 herbox kernel: [ 8355.637975]  [<ffffffffa098f66d>] ? os_alloc_mem+0x10d/0x120 [nvidia]
Jan  3 03:45:42 herbox kernel: [ 8355.638153]  [<ffffffffa098f66d>] os_alloc_mem+0x10d/0x120 [nvidia]
Jan  3 03:45:42 herbox kernel: [ 8355.638338]  [<ffffffffa034c1a9>] ? _nv000423rm+0xd/0x2f [nvidia]
Jan  3 03:45:42 herbox kernel: [ 8355.638520]  [<ffffffffa095be92>] _nv014822rm+0x30/0x3f [nvidia]
Jan  3 03:45:42 herbox kernel: [ 8355.638713]  [<ffffffffa0373166>] ? _nv001359rm+0x98/0x11f [nvidia]
Jan  3 03:45:42 herbox kernel: [ 8355.638906]  [<ffffffffa037f29b>] ? _nv001094rm+0x152/0x485 [nvidia]
Jan  3 03:45:42 herbox kernel: [ 8355.639098]  [<ffffffffa0374164>] ? _nv000960rm+0xa8/0xf9 [nvidia]
Jan  3 03:45:42 herbox kernel: [ 8355.639289]  [<ffffffffa0374127>] ? _nv000960rm+0x6b/0xf9 [nvidia]
Jan  3 03:45:42 herbox kernel: [ 8355.639471]  [<ffffffffa095a3b2>] ? _nv001108rm+0x582/0xaaf [nvidia]
Jan  3 03:45:42 herbox kernel: [ 8355.639648]  [<ffffffffa09662a7>] ? rm_ioctl+0x76/0x100 [nvidia]
Jan  3 03:45:42 herbox kernel: [ 8355.639824]  [<ffffffffa0984bfc>] ? nv_kern_ioctl+0x15c/0x490 [nvidia]
Jan  3 03:45:42 herbox kernel: [ 8355.639998]  [<ffffffffa0984f81>] ? nv_kern_unlocked_ioctl+0x21/0x30 [nvidia]
Jan  3 03:45:42 herbox kernel: [ 8355.640007]  [<ffffffff811996fa>] ? do_vfs_ioctl+0x8a/0x340
Jan  3 03:45:42 herbox kernel: [ 8355.640016]  [<ffffffff81187d0d>] ? vfs_read+0x10d/0x180
Jan  3 03:45:42 herbox kernel: [ 8355.640024]  [<ffffffff81199a41>] ? sys_ioctl+0x91/0xa0
Jan  3 03:45:42 herbox kernel: [ 8355.640034]  [<ffffffff816a7029>] ? system_call_fastpath+0x16/0x1b
Jan  3 03:45:42 herbox kernel: [ 8355.640037] Code: 00 4d 8b 04 24 65 4c 03 04 25 48 dc 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 e7 00 00 00 49 63 44 24 20 49 8b 3c 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0f 0f 94 c0 84 c0 74 c2 49 
Jan  3 03:45:42 herbox kernel: [ 8355.640116] RIP  [<ffffffff811737ab>] __kmalloc+0x7b/0x1a0
Jan  3 03:45:42 herbox kernel: [ 8355.640124]  RSP <ffff880211817c48>
Jan  3 03:45:42 herbox kernel: [ 8355.640174] ---[ end trace ac1a6d077efa7e28 ]---
Jan  3 03:45:42 herbox pulseaudio[6851]: [pulseaudio] client-conf-x11.c: xcb_connection_has_error() returned true
Jan  3 03:45:42 herbox rtkit-daemon[1839]: Successfully made thread 6854 of process 6854 (n/a) owned by '1000' high priority at nice level -11.
Jan  3 03:45:42 herbox rtkit-daemon[1839]: Supervising 1 threads of 1 processes of 1 users.
Jan  3 03:45:42 herbox pulseaudio[6854]: [pulseaudio] pid.c: Stale PID file, overwriting.
Jan  3 03:45:42 herbox kernel: [ 8355.802292] general protection fault: 0000 [#2] SMP 
Jan  3 03:45:42 herbox kernel: [ 8355.802297] CPU 2 
Jan  3 03:45:42 herbox kernel: [ 8355.802298] Modules linked in: rfcomm bnep bluetooth parport_pc ppdev nvidia(PO) snd_hda_codec_hdmi joydev hid_logitech_dj hid_generic snd_hda_codec_realtek usbhid snd_hda_intel snd_hda_codec hid snd_hwdep snd_pcm arc4 rt2800pci rt2800lib snd_seq_midi snd_rawmidi crc_ccitt snd_seq_midi_event snd_seq rt2x00pci snd_timer rt2x00lib snd_seq_device mac80211 snd soundcore kvm_amd kvm cfg80211 snd_page_alloc eeepc_wmi asus_wmi mxm_wmi sparse_keymap k10temp wmi microcode edac_core psmouse eeprom_93cx6 edac_mce_amd serio_raw sp5100_tco mac_hid i2c_piix4 lp parport r8169
Jan  3 03:45:42 herbox kernel: [ 8355.802331] 
Jan  3 03:45:42 herbox kernel: [ 8355.802333] Pid: 6862, comm: sed Tainted: P      D    O 3.5.0-23-generic #35~precise1-Ubuntu To be filled by O.E.M. To be filled by O.E.M./M5A97 LE R2.0
Jan  3 03:45:42 herbox kernel: [ 8355.802337] RIP: 0010:[<ffffffff8117643b>]  [<ffffffff8117643b>] __kmalloc_track_caller+0x7b/0x190
Jan  3 03:45:42 herbox kernel: [ 8355.802344] RSP: 0018:ffff880210119cd8  EFLAGS: 00010282
Jan  3 03:45:42 herbox kernel: [ 8355.802346] RAX: 0000000000000000 RBX: 0000000000000000 RCX: 000000000008d55a
Jan  3 03:45:42 herbox kernel: [ 8355.802347] RDX: 000000000008d559 RSI: 0000000000000000 RDI: 0000000000016770
Jan  3 03:45:42 herbox kernel: [ 8355.802349] RBP: ffff880210119d28 R08: ffff88021fd16770 R09: ffffc90000002000
Jan  3 03:45:42 herbox kernel: [ 8355.802350] R10: ffff88020782ac00 R11: 0000000000000000 R12: ffff880217002500
Jan  3 03:45:42 herbox kernel: [ 8355.802351] R13: ff7f8802106b9ae0 R14: 00000000000000d0 R15: 0000000000000000
Jan  3 03:45:42 herbox kernel: [ 8355.802354] FS:  00007f14de7c27c0(0000) GS:ffff88021fd00000(0000) knlGS:00000000f7399b00
Jan  3 03:45:42 herbox kernel: [ 8355.802355] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jan  3 03:45:42 herbox kernel: [ 8355.802357] CR2: 0000000002142248 CR3: 00000001ffb62000 CR4: 00000000000007e0
Jan  3 03:45:42 herbox kernel: [ 8355.802358] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jan  3 03:45:42 herbox kernel: [ 8355.802360] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jan  3 03:45:42 herbox kernel: [ 8355.802362] Process sed (pid: 6862, threadinfo ffff880210118000, task ffff8801ffadc500)
Jan  3 03:45:42 herbox kernel: [ 8355.802363] Stack:
Jan  3 03:45:42 herbox kernel: [ 8355.802364]  ffff880210119ce8 ffffffff812b992c ffffffff811958f0 000000000000000a
Jan  3 03:45:42 herbox kernel: [ 8355.802368]  0000000000001000 0000000000000000 ffff8801587051b8 000000000000000a
Jan  3 03:45:42 herbox kernel: [ 8355.802371]  00000000000000d0 0000000000000000 ffff880210119d58 ffffffff81142f92
Jan  3 03:45:42 herbox kernel: [ 8355.802374] Call Trace:
Jan  3 03:45:42 herbox kernel: [ 8355.802379]  [<ffffffff812b992c>] ? security_inode_permission+0x1c/0x30
Jan  3 03:45:42 herbox kernel: [ 8355.802382]  [<ffffffff811958f0>] ? vfs_rename+0xa0/0x240
Jan  3 03:45:42 herbox kernel: [ 8355.802386]  [<ffffffff81142f92>] kstrdup+0x42/0x70
Jan  3 03:45:42 herbox kernel: [ 8355.802389]  [<ffffffff811958f0>] vfs_rename+0xa0/0x240
Jan  3 03:45:42 herbox kernel: [ 8355.802392]  [<ffffffff81192578>] ? __lookup_hash+0x28/0x90
Jan  3 03:45:42 herbox kernel: [ 8355.802395]  [<ffffffff8169c39d>] ? mutex_lock+0x1d/0x50
Jan  3 03:45:42 herbox kernel: [ 8355.802398]  [<ffffffff81197c98>] sys_renameat+0x218/0x240
Jan  3 03:45:42 herbox kernel: [ 8355.802401]  [<ffffffff8117403f>] ? kmem_cache_free+0x2f/0x110
Jan  3 03:45:42 herbox kernel: [ 8355.802404]  [<ffffffff811555e8>] ? do_munmap+0x258/0x300
Jan  3 03:45:42 herbox kernel: [ 8355.802407]  [<ffffffff81197cdb>] sys_rename+0x1b/0x20
Jan  3 03:45:42 herbox kernel: [ 8355.802410]  [<ffffffff816a7029>] system_call_fastpath+0x16/0x1b
Jan  3 03:45:42 herbox kernel: [ 8355.802412] Code: 00 4d 8b 04 24 65 4c 03 04 25 48 dc 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 d7 00 00 00 49 63 44 24 20 49 8b 3c 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0f 0f 94 c0 84 c0 74 c2 49 
Jan  3 03:45:42 herbox kernel: [ 8355.802441] RIP  [<ffffffff8117643b>] __kmalloc_track_caller+0x7b/0x190
Jan  3 03:45:42 herbox kernel: [ 8355.802443]  RSP <ffff880210119cd8>
Jan  3 03:45:42 herbox kernel: [ 8355.802446] ---[ end trace ac1a6d077efa7e29 ]---
Jan  3 03:45:42 herbox kernel: [ 8355.806079] general protection fault: 0000 [#3] SMP 
Jan  3 03:45:42 herbox kernel: [ 8355.806083] CPU 2 
Jan  3 03:45:42 herbox kernel: [ 8355.806084] Modules linked in: rfcomm bnep bluetooth parport_pc ppdev nvidia(PO) snd_hda_codec_hdmi joydev hid_logitech_dj hid_generic snd_hda_codec_realtek usbhid snd_hda_intel snd_hda_codec hid snd_hwdep snd_pcm arc4 rt2800pci rt2800lib snd_seq_midi snd_rawmidi crc_ccitt snd_seq_midi_event snd_seq rt2x00pci snd_timer rt2x00lib snd_seq_device mac80211 snd soundcore kvm_amd kvm cfg80211 snd_page_alloc eeepc_wmi asus_wmi mxm_wmi sparse_keymap k10temp wmi microcode edac_core psmouse eeprom_93cx6 edac_mce_amd serio_raw sp5100_tco mac_hid i2c_piix4 lp parport r8169
Jan  3 03:45:42 herbox kernel: [ 8355.806116] 
Jan  3 03:45:42 herbox kernel: [ 8355.806118] Pid: 6863, comm: udev-acl.ck Tainted: P      D    O 3.5.0-23-generic #35~precise1-Ubuntu To be filled by O.E.M. To be filled by O.E.M./M5A97 LE R2.0
Jan  3 03:45:42 herbox kernel: [ 8355.806122] RIP: 0010:[<ffffffff811737ab>]  [<ffffffff811737ab>] __kmalloc+0x7b/0x1a0
Jan  3 03:45:42 herbox kernel: [ 8355.806128] RSP: 0018:ffff8801eea61c88  EFLAGS: 00010282
Jan  3 03:45:42 herbox kernel: [ 8355.806130] RAX: 0000000000000000 RBX: ffff8801eea61d40 RCX: 000000000008d55a
Jan  3 03:45:42 herbox kernel: [ 8355.806131] RDX: 000000000008d559 RSI: 0000000000000000 RDI: 0000000000016770
Jan  3 03:45:42 herbox kernel: [ 8355.806133] RBP: ffff8801eea61cd8 R08: ffff88021fd16770 R09: 000000000000ffff
Jan  3 03:45:42 herbox kernel: [ 8355.806134] R10: 0000000000000000 R11: 0000000000000246 R12: ffff880217002500
Jan  3 03:45:42 herbox kernel: [ 8355.806135] R13: ff7f8802106b9ae0 R14: 00000000000000d0 R15: ffffffff8133f157
Jan  3 03:45:42 herbox kernel: [ 8355.806137] FS:  00007fd368993700(0000) GS:ffff88021fd00000(0000) knlGS:00000000f7399b00
Jan  3 03:45:42 herbox kernel: [ 8355.806139] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jan  3 03:45:42 herbox kernel: [ 8355.806140] CR2: 00007fd367d21ef7 CR3: 00000001ffb62000 CR4: 00000000000007e0
Jan  3 03:45:42 herbox kernel: [ 8355.806142] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jan  3 03:45:42 herbox kernel: [ 8355.806143] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jan  3 03:45:42 herbox kernel: [ 8355.806145] Process udev-acl.ck (pid: 6863, threadinfo ffff8801eea60000, task ffff8801ffad8000)
Jan  3 03:45:42 herbox kernel: [ 8355.806146] Stack:
Jan  3 03:45:42 herbox kernel: [ 8355.806147]  0000000000000000 0000000000000000 00000000000280d0 000000000000000b
Jan  3 03:45:42 herbox kernel: [ 8355.806151]  00000000000080d0 ffff8801eea61d40 00000000000000d0 000000000000000b
Jan  3 03:45:42 herbox kernel: [ 8355.806154]  ffffffffa004d2be ffff8802034f5000 ffff8801eea61d28 ffffffff8133f157
Jan  3 03:45:42 herbox kernel: [ 8355.806157] Call Trace:
Jan  3 03:45:42 herbox kernel: [ 8355.806162]  [<ffffffff8133f157>] kvasprintf+0x57/0x90
Jan  3 03:45:42 herbox kernel: [ 8355.806165]  [<ffffffff8133f1c8>] kasprintf+0x38/0x40
Jan  3 03:45:42 herbox kernel: [ 8355.806169]  [<ffffffff81333069>] ? add_uevent_var+0x69/0x100
Jan  3 03:45:42 herbox kernel: [ 8355.806174]  [<ffffffffa004c385>] sound_devnode+0x35/0x50 [soundcore]
Jan  3 03:45:42 herbox kernel: [ 8355.806178]  [<ffffffff81426bc5>] device_get_devnode+0x85/0x110
Jan  3 03:45:42 herbox kernel: [ 8355.806181]  [<ffffffff81426d64>] dev_uevent+0x114/0x170
Jan  3 03:45:42 herbox kernel: [ 8355.806184]  [<ffffffff81426335>] show_uevent+0xb5/0x140
Jan  3 03:45:42 herbox kernel: [ 8355.806187]  [<ffffffff81425e10>] dev_attr_show+0x20/0x60
Jan  3 03:45:42 herbox kernel: [ 8355.806190]  [<ffffffff8112c13e>] ? __get_free_pages+0xe/0x40
Jan  3 03:45:42 herbox kernel: [ 8355.806194]  [<ffffffff811f7fa6>] fill_read_buffer.isra.7+0x66/0xf0
Jan  3 03:45:42 herbox kernel: [ 8355.806197]  [<ffffffff811f80d4>] sysfs_read_file+0xa4/0xc0
Jan  3 03:45:42 herbox kernel: [ 8355.806200]  [<ffffffff81187cb0>] vfs_read+0xb0/0x180
Jan  3 03:45:42 herbox kernel: [ 8355.806203]  [<ffffffff81187dca>] sys_read+0x4a/0x90
Jan  3 03:45:42 herbox kernel: [ 8355.806206]  [<ffffffff816a7029>] system_call_fastpath+0x16/0x1b
Jan  3 03:45:42 herbox kernel: [ 8355.806208] Code: 00 4d 8b 04 24 65 4c 03 04 25 48 dc 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 e7 00 00 00 49 63 44 24 20 49 8b 3c 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0f 0f 94 c0 84 c0 74 c2 49 
Jan  3 03:45:42 herbox kernel: [ 8355.806237] RIP  [<ffffffff811737ab>] __kmalloc+0x7b/0x1a0
Jan  3 03:45:42 herbox kernel: [ 8355.806239]  RSP <ffff8801eea61c88>
Jan  3 03:45:42 herbox kernel: [ 8355.806242] ---[ end trace ac1a6d077efa7e2a ]---
Jan  3 03:45:42 herbox acpid: client 1121[0:0] has disconnected
Jan  3 03:45:42 herbox acpid: client 1121[0:0] has disconnected
Jan  3 03:45:42 herbox acpid: client connected from 6864[0:0]
Jan  3 03:45:42 herbox acpid: 1 client rule loaded
Jan  3 03:45:42 herbox pulseaudio[6851]: [pulseaudio] main.c: Daemon startup failed.
Jan  3 03:45:42 herbox kernel: [ 8355.891317] general protection fault: 0000 [#4] SMP 
Jan  3 03:45:42 herbox kernel: [ 8355.891328] CPU 2 
Jan  3 03:45:42 herbox kernel: [ 8355.891331] Modules linked in: rfcomm bnep bluetooth parport_pc ppdev nvidia(PO) snd_hda_codec_hdmi joydev hid_logitech_dj hid_generic snd_hda_codec_realtek usbhid snd_hda_intel snd_hda_codec hid snd_hwdep snd_pcm arc4 rt2800pci rt2800lib snd_seq_midi snd_rawmidi crc_ccitt snd_seq_midi_event snd_seq rt2x00pci snd_timer rt2x00lib snd_seq_device mac80211 snd soundcore kvm_amd kvm cfg80211 snd_page_alloc eeepc_wmi asus_wmi mxm_wmi sparse_keymap k10temp wmi microcode edac_core psmouse eeprom_93cx6 edac_mce_amd serio_raw sp5100_tco mac_hid i2c_piix4 lp parport r8169
Jan  3 03:45:42 herbox kernel: [ 8355.891412] 
Jan  3 03:45:42 herbox kernel: [ 8355.891419] Pid: 6854, comm: pulseaudio Tainted: P      D    O 3.5.0-23-generic #35~precise1-Ubuntu To be filled by O.E.M. To be filled by O.E.M./M5A97 LE R2.0
Jan  3 03:45:42 herbox kernel: [ 8355.891428] RIP: 0010:[<ffffffff8117643b>]  [<ffffffff8117643b>] __kmalloc_track_caller+0x7b/0x190
Jan  3 03:45:42 herbox kernel: [ 8355.891442] RSP: 0018:ffff88020fd81c88  EFLAGS: 00010282
Jan  3 03:45:42 herbox kernel: [ 8355.891446] RAX: 0000000000000000 RBX: 0000000000000000 RCX: 000000000008d55a
Jan  3 03:45:42 herbox kernel: [ 8355.891450] RDX: 000000000008d559 RSI: 0000000000000000 RDI: 0000000000016770
Jan  3 03:45:42 herbox kernel: [ 8355.891454] RBP: ffff88020fd81cd8 R08: ffff88021fd16770 R09: ffff88021271c078
Jan  3 03:45:42 herbox kernel: [ 8355.891458] R10: 0000000000000001 R11: ffff8801f36d6210 R12: ffff880217002500
Jan  3 03:45:42 herbox kernel: [ 8355.891462] R13: ff7f8802106b9ae0 R14: 00000000000000d0 R15: ffff88020f562ab8
Jan  3 03:45:42 herbox kernel: [ 8355.891468] FS:  00007fa8e3042700(0000) GS:ffff88021fd00000(0000) knlGS:00000000f7399b00
Jan  3 03:45:42 herbox kernel: [ 8355.891472] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jan  3 03:45:42 herbox kernel: [ 8355.891476] CR2: 00007fa8e3052000 CR3: 00000002124c7000 CR4: 00000000000007e0
Jan  3 03:45:42 herbox kernel: [ 8355.891480] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jan  3 03:45:42 herbox kernel: [ 8355.891484] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jan  3 03:45:42 herbox kernel: [ 8355.891489] Process pulseaudio (pid: 6854, threadinfo ffff88020fd80000, task ffff880213390000)
Jan  3 03:45:42 herbox kernel: [ 8355.891492] Stack:
Jan  3 03:45:42 herbox kernel: [ 8355.891495]  ffff88020fd81ca8 ffffffff8169cb76 ffffffff811c791f 000000000000000a
Jan  3 03:45:42 herbox kernel: [ 8355.891504]  ffff88020fd81d08 0000000000000000 ffff88020f562ab8 000000000000000a
Jan  3 03:45:42 herbox kernel: [ 8355.891513]  00000000000000d0 ffff88020f562ab8 ffff88020fd81d08 ffffffff81142f92
Jan  3 03:45:42 herbox kernel: [ 8355.891521] Call Trace:
Jan  3 03:45:42 herbox kernel: [ 8355.891532]  [<ffffffff8169cb76>] ? down_read+0x16/0x2b
Jan  3 03:45:42 herbox kernel: [ 8355.891540]  [<ffffffff811c791f>] ? fsnotify_create_event+0x8f/0x170
Jan  3 03:45:42 herbox kernel: [ 8355.891550]  [<ffffffff81142f92>] kstrdup+0x42/0x70
Jan  3 03:45:42 herbox kernel: [ 8355.891557]  [<ffffffff811c791f>] fsnotify_create_event+0x8f/0x170
Jan  3 03:45:42 herbox kernel: [ 8355.891565]  [<ffffffff811c6bf9>] send_to_group+0x169/0x190
Jan  3 03:45:42 herbox kernel: [ 8355.891572]  [<ffffffff811c6eba>] fsnotify+0x29a/0x2b0
Jan  3 03:45:42 herbox kernel: [ 8355.891580]  [<ffffffff811c70de>] __fsnotify_parent+0xae/0x100
Jan  3 03:45:42 herbox kernel: [ 8355.891588]  [<ffffffff81188bf3>] __fput+0x1b3/0x240
Jan  3 03:45:42 herbox kernel: [ 8355.891596]  [<ffffffff81188ca5>] fput+0x25/0x30
Jan  3 03:45:42 herbox kernel: [ 8355.891602]  [<ffffffff81185976>] filp_close+0x66/0x90
Jan  3 03:45:42 herbox kernel: [ 8355.891609]  [<ffffffff81185a3e>] sys_close+0x9e/0x110
Jan  3 03:45:42 herbox kernel: [ 8355.891618]  [<ffffffff816a7029>] system_call_fastpath+0x16/0x1b
Jan  3 03:45:42 herbox kernel: [ 8355.891621] Code: 00 4d 8b 04 24 65 4c 03 04 25 48 dc 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 d7 00 00 00 49 63 44 24 20 49 8b 3c 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0f 0f 94 c0 84 c0 74 c2 49 
Jan  3 03:45:42 herbox kernel: [ 8355.891701] RIP  [<ffffffff8117643b>] __kmalloc_track_caller+0x7b/0x190
Jan  3 03:45:42 herbox kernel: [ 8355.891708]  RSP <ffff88020fd81c88>
Jan  3 03:45:42 herbox kernel: [ 8355.891714] ---[ end trace ac1a6d077efa7e2b ]---

```

](*,)

---

### Post by tgalati4 on 2014-01-03
General Protection Fault:  0000 is not very helpful.  It could be a thermal shutdown.  What are the core temps when running?  How old is this hardware?  Have you replaced the heat paste?  It's possible that you have a damaged CPU.  It's also possible that your power supply is starting to fail.  Check voltages with voltmeter or in BIOS.

---

### Post by steeldriver on 2014-01-03
bit of googling throws up this... don't know if it helps

[http://penberg.blogspot.ca/2010/07/linux-kernel-oops-debugging.html](http://penberg.blogspot.ca/2010/07/linux-kernel-oops-debugging.html)

[https://lkml.org/lkml/2010/7/11/91](https://lkml.org/lkml/2010/7/11/91)

---

### Post by brynn.west on 2014-01-04
@tgalati4 - my CPU, MB, and GPU stay around 26-28 C, my HDDs around 30 C when idle (used psensor). I replaced the MB, GPU, and my PSU is new (RMA). I also put down some fresh thermal compound. The heatsink is the one that came with my CPU from about a year and a half ago.

I just checked my voltage in my bios (new MS is ASUS M5A97 LE R2.0) and it said 1.404V for the CPU.

Does this sound okay?

@steeldriver - Thanks for the link. I tried to follow it but the instructions are rather vague when it comes to the deciphering the machine code dump. I'm not sure where to go from here. Searching all I can on:  __kmalloc+0x7b/0x1a0

I have done a fresh install of 12.04 again. Everything seems to be working okay. I can sucessfully hibernate and bring it back and it runs smooth with the new binary NVidia drivers. Still don't know why it crashed before this latest install. The only difference is I am not using Clementine. The only reason I can think that would cause anything because it is based on Amarok and there may be some wonky KDE dependencies. Really dissapointed because Clementine is one of the best players out there. Perhaps I'll try the non-PPA (1.2 in Ubuntu's repositories) and see if that works.

Still does not explain that one crash I had on a 12.04 live CD... This all originally started after some minor upgrades a couple months back iirc.

Any ideas on reproducing this crash?

---

### Post by tgalati4 on 2014-01-04
It sounds like you have gone through your hardware thoroughly.  I would check the 5VDC and 12VDC rails on the power supply.  The BIOS may show those as well.  Your temps sound OK and I presume that everything is seated properly.  Sometimes a bad SATA cable can cause issues.  I would create a minimal system--pull out as much stuff as possible.  Disconnect the hard drive, and boot from a Live USB and just run from the live session and see how long your system stays up.  Use the default software, don't load anything--it will only be in RAM anyway.  If your system stays up for 3 days continuous, then shut down and add the hard disk back and boot from it and see how long it stays up.

Isolation is key to troubleshooting.

Searching the web for trace dumps is not helpful because you have several different types of trace dumps.  One includes firefox.exe!  Are you running any virtual machines?  The fact that the machine locked up with a Live DVD would be consistent with a hardware problem.

Explain why the power supply was exchanged under an RMA?  Did it damage the motherboard?

---

### Post by brynn.west on 2014-01-04
So I've reseated everything and it's been running fine, but I will try the 3 day uptime test with just a live CD and no HDD. I'll check on this thread with my phone while I'm doing that.

The one crash on the Live CD is not this latest one. I could not capture that crash output. I only saw *similar* traces as it crashed. Sorry I can't be more helpful there. Could it be a pulseaudio problem? I may have been playing music with the Live CD going when it crashed. I can't remember though. I know I was online checking emails and other things I needed to get done. (I was having ATI driver problems at the time, but those were separate and well known issues with the drivers I was using). This latest time it happened right as I was adjusting volume.

firefox.exe must be from wine via the netflix-desktop app. I have not reinstalled that either this go around.

As for the power suppy, I originally thought the it might have fried something so I RMAed it to be sure and replaced my motherboard.

---

### Post by brynn.west on 2014-01-10
So is this useful? I get weird outputs via sensord (recently installed) Some of the ranges don't make sense.

```

Jan 10 16:36:55 herbox sensord: Sensor alarm: Chip it8721-isa-0290: +5V: +5.03 V (min = +2.43 V, max = +3.14 V) [ALARM]
Jan 10 16:36:55 herbox sensord: Sensor alarm: Chip it8721-isa-0290: Vcore: +1.06 V (min = +0.92 V, max = +0.94 V) [ALARM]
Jan 10 16:36:55 herbox sensord: Sensor alarm: Chip it8721-isa-0290: +3.3V: +3.36 V (min = +3.26 V, max = +1.03 V) [ALARM]
Jan 10 16:36:55 herbox sensord: Sensor alarm: Chip it8721-isa-0290: CPU Temp: 27.0 C (min = 56.0 C, max = 11.0 C) [ALARM]
Jan 10 16:36:55 herbox sensord: Sensor alarm: Chip it8721-isa-0290: M/B Temp: 23.0 C (min = 33.0 C, max = -43.0 C) [ALARM]

```

---

### Post by tgalati4 on 2014-01-11
In the sensors configuration file, you can change the alarm limits.  Look for /etc/sensors3.conf.  You can do some research on your motherboard and the it8721 monitor chip to see what it is supposed to track.  I agree, your voltages do look strange.  5VDC should be 5VDC, so I don't know why the limits are 2.43 and 3.14.  The Vcore at 1.06 is showing slightly high.  You need to research what the appropriate core voltages are for your processor.  Slight overvoltage is OK, undervoltage can cause lockups.  Your 3.3VDC controls RAM and other system chips and again the limits are messed up.  So it's possible that the old power supply damaged the new motherboard is a subtle way.  How long did you run the new motherboard on the old power supply?

---

### Post by brynn.west on 2014-01-11
Just to be clear, I never ran the new motherboard on the new power supply for that exact reason.

Where would I look for that information? I'm trying to just Google, but kinda difficult without knowing what exactly to search for.

---

### Post by tgalati4 on 2014-01-11
Find a cutsheet for the it8721.  Memorize it.  Find the inputs and outputs and pin numbers.  Look at your motherboard with the it8721 chip.  Find Pin#1 and follow the traces for the other pins.  That will give you an idea of how it is hooked up and to what subsystems.  Look for detailed specifications for your motherboard.  Send an email to the ASUS and ask them technical questions.  It's your board, you should know a few things about it.

---

