---
title: "[SOLVED] System going down and not responding"
date: 2008-07-16
forum: General Help
---

### Post by tghe-retford on 2008-07-16
I am having a major problem with my computer, every now and again for no reason, the computer will stop responding completely. It looks like the system is on standby (my monitor detects no video so it turns itself off) but the whole system will not respond and you either have to physically reset or power down the computer.

It came to a head today when I let MythTV record the All Star Game so I watch it tonight after work. However, when I went onto my computer this morning, it was a good as dead. I had to reset the computer and when I got back to the desktop, I was annoyed that the program I recorded hadn't recorded. :evil: I checked the kernel logs and it looked as if I got two general protection faults when I left the computer to record and go to bed:

```
Jul 16 01:59:26 tghe kernel: [  638.974834] general protection fault: 0000 [1] SMP 
Jul 16 01:59:26 tghe kernel: [  638.974837] CPU 1 
Jul 16 01:59:26 tghe kernel: [  638.974839] Modules linked in: snd_rtctimer vmnet(P) vmmon(P) binfmt_misc af_packet rfcomm l2cap bluetooth ipv6 ppdev cpufreq_userspace cpufreq_conservative cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table sbs container dock video output sbshc battery iptable_filter ip_tables x_tables ac coretemp it87 hwmon_vid sbp2 lp loop dvb_pll cx22702 snd_hda_intel cx88_dvb cx88_vp3054_i2c videobuf_dvb snd_pcm_oss snd_mixer_oss dvb_core snd_pcm snd_page_alloc snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi joydev snd_rawmidi snd_seq_midi_event cx8800 cx8802 cx88xx nvidia(P) snd_seq ir_common serio_raw i2c_algo_bit i2c_nforce2 snd_timer snd_seq_device shpchp snd tveeprom videodev v4l1_compat compat_ioctl32 v4l2_common videobuf_dma_sg btcx_risc videobuf_core pci_hotplug button psmouse parport_pc parport evdev pcspkr i2c_core soundcore ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_amd sata_nv ata_generic usbhid hid ohci1394 ahci pata_acpi ieee1394 forcedeth libata ohci_hcd ehci_hcd
Jul 16 01:59:26 tghe kernel: scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Jul 16 01:59:26 tghe kernel: [  638.974891] Pid: 6305, comm: Xorg Tainted: P        2.6.24-19-generic #1
Jul 16 01:59:26 tghe kernel: [  638.974892] RIP: 0010:[do_select+0x2c6/0x560]  [do_select+0x2c6/0x560] do_select+0x2c6/0x560
Jul 16 01:59:26 tghe kernel: [  638.974897] RSP: 0018:ffff81007c45ba48  EFLAGS: 00010206
Jul 16 01:59:26 tghe kernel: [  638.974899] RAX: 0000ffff8049b9c0 RBX: 0000000800000000 RCX: ffff810066ff63c0
Jul 16 01:59:26 tghe kernel: [  638.974900] RDX: ffff81007c712310 RSI: ffff81007c45bd44 RDI: 0000000000000023
Jul 16 01:59:26 tghe kernel: [  638.974902] RBP: ffff810066ff63c0 R08: 0000000000000000 R09: 000000000000002b
Jul 16 01:59:26 tghe kernel: [  638.974903] R10: ffff81000101cfe0 R11: ffffffff80457ff0 R12: 0000000000000023
Jul 16 01:59:26 tghe kernel: [  638.974905] R13: 0000000000000023 R14: 0000000000000000 R15: 0000000000000304
Jul 16 01:59:26 tghe kernel: [  638.974907] FS:  00007f41ad9a96e0(0000) GS:ffff81007dc01700(0000) knlGS:0000000000000000
Jul 16 01:59:26 tghe kernel: [  638.974908] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Jul 16 01:59:26 tghe kernel: [  638.974910] CR2: 000000000293a83f CR3: 000000007d19b000 CR4: 00000000000006e0
Jul 16 01:59:26 tghe kernel: [  638.974911] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jul 16 01:59:26 tghe kernel: [  638.974913] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jul 16 01:59:26 tghe kernel: [  638.974914] Process Xorg (pid: 6305, threadinfo ffff81007c45a000, task ffff81007c636fc0)
Jul 16 01:59:26 tghe kernel: [  638.974916] Stack:  ffff81000101cf80 ffff81007c45baf8 ffff81007c45ba78 ffff81007c45bf50
Jul 16 01:59:26 tghe kernel: [  638.974919]  ffff81007c45beb8 0000000000000000 000000007c45ba98 ffff81007c45bdd0
Jul 16 01:59:26 tghe kernel: [  638.974922]  ffff81007c45bdd8 ffff81007c45bde0 ffff81007c45bdc0 ffff81007c45bdc8
Jul 16 01:59:26 tghe kernel: [  638.974925] Call Trace:
Jul 16 01:59:26 tghe kernel: [  638.974942]  [__pollwait+0x0/0x130] __pollwait+0x0/0x130
Jul 16 01:59:26 tghe kernel: [  638.974948]  [<ffffffff80233e20>] default_wake_function+0x0/0x10
Jul 16 01:59:26 tghe kernel: [  638.974954]  [<ffffffff80233e20>] default_wake_function+0x0/0x10
Jul 16 01:59:26 tghe kernel: [  638.974960]  [<ffffffff80233e20>] default_wake_function+0x0/0x10
Jul 16 01:59:26 tghe kernel: [  638.974966]  [<ffffffff80233e20>] default_wake_function+0x0/0x10
Jul 16 01:59:26 tghe kernel: [  638.974973]  [<ffffffff80233e20>] default_wake_function+0x0/0x10
Jul 16 01:59:26 tghe kernel: [  638.974979]  [<ffffffff80233e20>] default_wake_function+0x0/0x10
Jul 16 01:59:26 tghe kernel: [  638.974985]  [<ffffffff80233e20>] default_wake_function+0x0/0x10
Jul 16 01:59:26 tghe kernel: [  638.974991]  [<ffffffff80233e20>] default_wake_function+0x0/0x10
Jul 16 01:59:26 tghe kernel: [  638.974997]  [<ffffffff80233e20>] default_wake_function+0x0/0x10
Jul 16 01:59:26 tghe kernel: [  638.975003]  [<ffffffff80233e20>] default_wake_function+0x0/0x10
Jul 16 01:59:26 tghe kernel: [  638.975012]  [core_sys_select+0x209/0x300] core_sys_select+0x209/0x300
Jul 16 01:59:26 tghe kernel: [  638.975034]  [__remove_hrtimer+0x74/0xb0] __remove_hrtimer+0x74/0xb0
Jul 16 01:59:26 tghe kernel: [  638.975039]  [hrtimer_try_to_cancel+0x39/0x80] hrtimer_try_to_cancel+0x39/0x80
Jul 16 01:59:26 tghe kernel: [  638.975051]  [sys_select+0x44/0x1c0] sys_select+0x44/0x1c0
Jul 16 01:59:26 tghe kernel: [  638.975060]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Jul 16 01:59:26 tghe kernel: [  638.975071] 
Jul 16 01:59:26 tghe kernel: [  638.975072] 
Jul 16 01:59:26 tghe kernel: [  638.975072] Code: 48 8b 40 38 48 85 c0 0f 84 08 02 00 00 44 8b 44 24 34 31 f6 
Jul 16 01:59:26 tghe kernel: [  638.975079] RIP  [do_select+0x2c6/0x560] do_select+0x2c6/0x560
Jul 16 01:59:26 tghe kernel: [  638.975081]  RSP <ffff81007c45ba48>
Jul 16 01:59:26 tghe kernel: [  638.975084] ---[ end trace d7c65a9fc98cc6fb ]---
```
```
Jul 16 07:02:42 tghe kernel: [18806.957885] general protection fault: 0000 [2] SMP 
Jul 16 07:02:42 tghe kernel: [18806.957889] CPU 0 
Jul 16 07:02:42 tghe kernel: [18806.957890] Modules linked in: snd_rtctimer vmnet(P) vmmon(P) binfmt_misc af_packet rfcomm l2cap bluetooth ipv6 ppdev cpufreq_userspace cpufreq_conservative cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table sbs container dock video output sbshc battery iptable_filter ip_tables x_tables ac coretemp it87 hwmon_vid sbp2 lp loop dvb_pll cx22702 snd_hda_intel cx88_dvb cx88_vp3054_i2c videobuf_dvb snd_pcm_oss snd_mixer_oss dvb_core snd_pcm snd_page_alloc snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi joydev snd_rawmidi snd_seq_midi_event cx8800 cx8802 cx88xx nvidia(P) snd_seq ir_common serio_raw i2c_algo_bit i2c_nforce2 snd_timer snd_seq_device shpchp snd tveeprom videodev v4l1_compat compat_ioctl32 v4l2_common videobuf_dma_sg btcx_risc videobuf_core pci_hotplug button psmouse parport_pc parport evdev pcspkr i2c_core soundcore ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_amd sata_nv ata_generic usbhid hid ohci1394 ahci pata_acpi ieee1394 forcedeth libata ohci_hcd ehci_hcd
Jul 16 07:02:42 tghe kernel: scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Jul 16 07:02:42 tghe kernel: [18806.957942] Pid: 7782, comm: cx88[0] dvb Tainted: P      D 2.6.24-19-generic #1
Jul 16 07:02:42 tghe kernel: [18806.957944] RIP: 0010:[memcpy_c+0xb/0x20]  [memcpy_c+0xb/0x20] memcpy_c+0xb/0x20
Jul 16 07:02:42 tghe kernel: [18806.957950] RSP: 0018:ffff81002c509dc8  EFLAGS: 00010202
Jul 16 07:02:42 tghe kernel: [18806.957952] RAX: d290c20000b073ec RBX: d51b0000001cac14 RCX: 0000000000039582
Jul 16 07:02:42 tghe kernel: [18806.957953] RDX: 0000000000000004 RSI: ffffc20000da05e0 RDI: d290c20000b073ec
Jul 16 07:02:42 tghe kernel: [18806.957955] RBP: ffff810037bfc678 R08: ffffc200009217f8 R09: 0000000000000000
Jul 16 07:02:42 tghe kernel: [18806.957956] R10: 0000000000000000 R11: ffffffff802204e0 R12: 00000000000000bc
Jul 16 07:02:42 tghe kernel: [18806.957958] R13: d51ac20000f6b1f4 R14: 0000000000000000 R15: 0000000000000000
Jul 16 07:02:42 tghe kernel: [18806.957959] FS:  0000000000000000(0000) GS:ffffffff805b9000(0000) knlGS:0000000000000000
Jul 16 07:02:42 tghe kernel: [18806.957961] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Jul 16 07:02:42 tghe kernel: [18806.957963] CR2: 000000000158021f CR3: 000000007d252000 CR4: 00000000000006e0
Jul 16 07:02:42 tghe kernel: [18806.957964] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jul 16 07:02:42 tghe kernel: [18806.957966] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jul 16 07:02:42 tghe kernel: [18806.957967] Process cx88[0] dvb (pid: 7782, threadinfo ffff81002c508000, task ffff8100603ac7e0)
Jul 16 07:02:42 tghe kernel: [18806.957969] Stack:  ffffffff88b61d6f ffff81002c509e10 00000000000000bc ffff810037bfc678
Jul 16 07:02:42 tghe kernel: [18806.957972]  ffffc20000da05e0 00000000000000bc ffffffff88b58a20 ffffc20000a37578
Jul 16 07:02:42 tghe kernel: [18806.957975]  ffff810037bfc678 ffffc20000da05e0 ffffffff88b590d2 ffff81007c514fc0
Jul 16 07:02:42 tghe kernel: [18806.957977] Call Trace:
Jul 16 07:02:42 tghe kernel: [18806.957990]  [dvb_core:dvb_ringbuffer_write+0x8f/0xb0] :dvb_core:dvb_ringbuffer_write+0x8f/0xb0
Jul 16 07:02:42 tghe kernel: [18806.957999]  [dvb_core:dvb_dmxdev_buffer_write+0x40/0x80] :dvb_core:dvb_dmxdev_buffer_write+0x40/0x80
Jul 16 07:02:42 tghe kernel: [18806.958007]  [dvb_core:dvb_dmxdev_ts_callback+0xa2/0x100] :dvb_core:dvb_dmxdev_ts_callback+0xa2/0x100
Jul 16 07:02:42 tghe kernel: [18806.958017]  [dvb_core:dvb_dmx_swfilter_packet+0x35a/0x3a0] :dvb_core:dvb_dmx_swfilter_packet+0x35a/0x3a0
Jul 16 07:02:42 tghe kernel: [18806.958030]  [dvb_core:dvb_dmx_swfilter+0xbd/0x110] :dvb_core:dvb_dmx_swfilter+0xbd/0x110
Jul 16 07:02:42 tghe kernel: [18806.958037]  [videobuf_dvb:videobuf_dvb_thread+0x120/0x1a0] :videobuf_dvb:videobuf_dvb_thread+0x120/0x1a0
Jul 16 07:02:42 tghe kernel: [18806.958042]  [videobuf_dvb:videobuf_dvb_thread+0x0/0x1a0] :videobuf_dvb:videobuf_dvb_thread+0x0/0x1a0
Jul 16 07:02:42 tghe kernel: [18806.958046]  [kthread+0x4b/0x80] kthread+0x4b/0x80
Jul 16 07:02:42 tghe kernel: [18806.958051]  [child_rip+0xa/0x12] child_rip+0xa/0x12
Jul 16 07:02:42 tghe kernel: [18806.958059]  [lapic_next_event+0x0/0x10] lapic_next_event+0x0/0x10
Jul 16 07:02:42 tghe kernel: [18806.958065]  [kthread+0x0/0x80] kthread+0x0/0x80
Jul 16 07:02:42 tghe kernel: [18806.958068]  [child_rip+0x0/0x12] child_rip+0x0/0x12
Jul 16 07:02:42 tghe kernel: [18806.958072] 
Jul 16 07:02:42 tghe kernel: [18806.958072] 
Jul 16 07:02:42 tghe kernel: [18806.958073] Code: f3 48 a5 89 d1 f3 a4 c3 66 66 66 66 2e 0f 1f 84 00 00 00 00 
Jul 16 07:02:42 tghe kernel: [18806.958079] RIP  [memcpy_c+0xb/0x20] memcpy_c+0xb/0x20
Jul 16 07:02:42 tghe kernel: [18806.958082]  RSP <ffff81002c509dc8>
Jul 16 07:02:42 tghe kernel: [18806.958101] ---[ end trace d7c65a9fc98cc6fb ]---
```

It doesn't have to be recording TV this happens either. When I used Firefox, it too caused this to happen. If I am lucky, Firefox will grey out and I can force it to close. If I am not, this happens and you have to power down the system to get back to normal.

Is there anything I can do, or is my system broken and a reinstall needed?

I'm just unhappy about missing the All Stars Game. They don't repeat it on free-to-air UK TV. :evil:

In fact, as I was writing this post, the whole system crashed again ALT+SYS RQ didn't work either, I had to reset the computer using the reset button.

And X just crashed after I wrote that last message.

And just after that, it stopped responding again.

Three crashes in the space of ten minutes. Please help. I'm posting this before the system goes down again. Not taking any chances. :(

---

### Post by prshah on 2008-07-16
> **tghe-retford said:**
> 
Three crashes in the space of ten minutes. Please help. 

Just a suggestion while one mulls over your crash details: Have you checked your system RAM / Thermal?

To check RAM, boot off a live CD, then choose the "Memory Test" option. Or you will also find a "memtest" option in your GRUB. Run it for 20~30 mins or so; anything in RED is bad. 

To check system (especially processor) temperature, I'd suggest looking in the BIOS rather than using linux utilities, because they persistently misreport the temperature on my desktop.

---

### Post by tghe-retford on 2008-07-16
> **prshah said:**
> Just a suggestion while one mulls over your crash details: Have you checked your system RAM / Thermal?

To check RAM, boot off a live CD, then choose the "Memory Test" option. Or you will also find a "memtest" option in your GRUB. Run it for 20~30 mins or so; anything in RED is bad. 

To check system (especially processor) temperature, I'd suggest looking in the BIOS rather than using linux utilities, because they persistently misreport the temperature on my desktop.
That was my first thought when I was walking to work, problems with RAM or possible overheating, but then I see this thread: [http://ubuntuforums.org/showthread.php?t=832383](http://ubuntuforums.org/showthread.php?t=832383) (my computer is self built, not a Dell but my symptoms are the same) and I do wonder whether there maybe a software problem.

---

