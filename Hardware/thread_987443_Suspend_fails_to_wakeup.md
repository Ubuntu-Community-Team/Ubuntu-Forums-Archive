---
title: "Suspend fails to wakeup"
date: 2008-11-19
forum: Hardware
---

### Post by agentoo7 on 2008-11-19
Hello everybody,
I've got a problem with my desktop.
When I go into suspend mode, I can't get out of it.
I just have a black screen.
After a while my screen LED is starting to blink (no signal)
any solutions??
Nobody was able to help me on the Dutch forum.

agentoo7.
(sorry for my very Dutchy english)

here I have the kern.log:
```

Nov 18 18:02:42 willem-ubuntu kernel: [ 5007.144232] PM: Preparing system for mem sleep
Nov 18 18:03:00 willem-ubuntu kernel: [ 5007.147102] Freezing user space processes ... (elapsed 0.00 seconds) done.
Nov 18 18:03:00 willem-ubuntu kernel: [ 5007.149974] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Nov 18 18:03:00 willem-ubuntu kernel: [ 5007.150163] PM: Entering mem sleep
Nov 18 18:03:00 willem-ubuntu kernel: [ 5007.150167] Suspending console(s) (use no_console_suspend to debug)
Nov 18 18:03:00 willem-ubuntu kernel: [ 5007.150601] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Nov 18 18:03:00 willem-ubuntu kernel: [ 5007.294736] sd 0:0:0:0: [sda] Stopping disk
Nov 18 18:03:00 willem-ubuntu kernel: [ 5007.980641] parport_pc 00:0a: disabled
Nov 18 18:03:00 willem-ubuntu kernel: [ 5007.980898] serial 00:09: disabled
Nov 18 18:03:00 willem-ubuntu kernel: [ 5007.981116] serial 00:08: disabled
Nov 18 18:03:00 willem-ubuntu kernel: [ 5007.981151] ACPI handle has no context!
Nov 18 18:03:00 willem-ubuntu kernel: [ 5007.981175] NVRM: RmPowerManagement: 4
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.057213] C-Media PCI 0000:00:08.0: PCI INT A disabled
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.057264] ACPI handle has no context!
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.072097] ehci_hcd 0000:00:03.3: PCI INT D disabled
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.088072] ohci_hcd 0000:00:03.1: PCI INT B disabled
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.088114] ohci_hcd 0000:00:03.0: PCI INT A disabled
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.088285] pata_sis 0000:00:02.5: PCI INT A disabled
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.104214] PM: suspend devices took 0.956 seconds
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.104298] ACPI: Preparing to enter system sleep state S3
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.133149] Disabling non-boot CPUs ...
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.133149] Back to C!
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.133149] ACPI: Waking up from system sleep state S3
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.133149] ACPI: Unable to turn cooling device [df417c78] 'off'
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.133149] agpgart-sis 0000:00:00.0: restoring config space at offset 0x1 (was 0x2100007, writing 0x32100007)
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.133149] pci 0000:00:01.0: restoring config space at offset 0x7 (was 0xf0, writing 0x200000f0)
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.148057] pata_sis 0000:00:02.5: restoring config space at offset 0x1 (was 0x2100001, writing 0x2100005)
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.148086] pata_sis 0000:00:02.5: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.151477] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.172048] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.212029] ehci_hcd 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.228075] C-Media PCI 0000:00:08.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Nov 18 18:03:00 willem-ubuntu kernel: [ 5008.228197] NVRM: RmPowerManagement: 5
Nov 18 18:03:00 willem-ubuntu kernel: [ 5009.123822] serial 00:08: activated
Nov 18 18:03:00 willem-ubuntu kernel: [ 5009.124947] serial 00:09: activated
Nov 18 18:03:00 willem-ubuntu kernel: [ 5009.126548] parport_pc 00:0a: activated
Nov 18 18:03:00 willem-ubuntu kernel: [ 5009.168072] sd 0:0:0:0: [sda] Starting disk
Nov 18 18:03:00 willem-ubuntu kernel: [ 5010.460308] ata2.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
Nov 18 18:03:00 willem-ubuntu kernel: [ 5010.460312] ata2.01: ACPI cmd ef/03:42:00:00:00:b0 filtered out
Nov 18 18:03:00 willem-ubuntu kernel: [ 5010.468509] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Nov 18 18:03:00 willem-ubuntu kernel: [ 5010.468513] ata2.00: ACPI cmd ef/03:22:00:00:00:a0 filtered out
Nov 18 18:03:00 willem-ubuntu kernel: [ 5010.484523] ata2.00: configured for PIO4
Nov 18 18:03:00 willem-ubuntu kernel: [ 5010.516316] ata2.01: configured for UDMA/33
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.148273] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.148278] ata1.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.164476] ata1.00: configured for UDMA/33
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180040] sd 0:0:0:0: [sda] 8452080 512-byte hardware sectors (4327 MB)
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180130] sd 0:0:0:0: [sda] Write Protect is off
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180135] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180284] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180729] PM: resume devices took 5.048 seconds
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180744] ------------[ cut here ]------------
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180746] WARNING: at /build/buildd/linux-2.6.27/kernel/power/main.c:176 suspend_test_finish+0x74/0x80()
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180749] Modules linked in: ipv6 af_packet binfmt_misc bridge stp rfcomm bnep sco l2cap bluetooth ppdev speedstep_lib cpufreq_conservative cpufreq_stats cpufreq_ondemand cpufreq_powersave freq_table cpufreq_userspace pci_slot container video output sbs sbshc wmi battery iptable_filter ip_tables x_tables ac lp snd_cmipci serio_raw gameport evdev psmouse snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_opl3_lib snd_hwdep snd_mpu401_uart snd_seq_dummy parport_pc parport nvidia(P) snd_seq_oss snd_seq_midi snd_rawmidi pcspkr snd_seq_midi_event snd_seq snd_timer snd_seq_device button snd i2c_sis96x soundcore sis_agp i2c_core shpchp pci_hotplug agpgart ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg ata_generic pata_acpi pata_sis libata ohci_hcd ehci_hcd sis900 mii usbcore scsi_mod dock thermal processor fan fbcon tileblit font bitblit softcursor fuse
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180824] Pid: 6425, comm: pm-suspend Tainted: P          2.6.27-7-generic #1
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180829]  [<c037c406>] ? printk+0x1d/0x1f
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180839]  [<c0131de9>] warn_on_slowpath+0x59/0x90
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180847]  [<c014d255>] ? sched_clock_cpu+0xd5/0x170
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180853]  [<c014c0af>] ? down_trylock+0x2f/0x40
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180858]  [<c01324c2>] ? try_acquire_console_sem+0x12/0x40
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180865]  [<c024e580>] ? kobject_put+0x20/0x50
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180870]  [<c015d204>] suspend_test_finish+0x74/0x80
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180876]  [<c015d2f6>] suspend_devices_and_enter+0xe6/0x190
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180881]  [<c015d571>] enter_state+0xd1/0x100
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180884]  [<c015d625>] state_store+0x85/0xd0
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180888]  [<c015d5a0>] ? state_store+0x0/0xd0
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180891]  [<c024e444>] kobj_attr_store+0x24/0x30
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180895]  [<c01ff4c7>] sysfs_write_file+0x97/0x100
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180900]  [<c01b24c0>] vfs_write+0xa0/0x110
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180906]  [<c01ff430>] ? sysfs_write_file+0x0/0x100
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180910]  [<c01b2602>] sys_write+0x42/0x70
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180913]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180919]  [<c0370000>] ? default_device_exit+0x60/0xb0
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180925]  =======================
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180928] ---[ end trace 46e82224b760749e ]---
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180949] PM: Finishing wakeup.
Nov 18 18:03:00 willem-ubuntu kernel: [ 5013.180951] Restarting tasks ... done.

```

---

### Post by agentoo7 on 2008-11-20
can nobody help me?

---

