---
title: "NVidia 8800 GTX on x64 - X freezes during start"
date: 2009-03-08
forum: Hardware
---

### Post by herr_tichy on 2009-03-08
Hello Forum,

I have the following problem - my machine is a Phenom X4, 4GB RAM and a GeForce 8800 GTX. Connected to the graphics card are one TFT using DVI and an older TFT using a DVI-VGA adapter. The hardware itself seems to be running fine, at least under Windows XP.

When I start X with the "nv" driver, everything works fine. Dual screen mode works and everything is cool. Whenever I try to use the closed source Nvidia driver, the machine becomes unresponsive as soon as X starts and the monitors enter standby mode. I can login via SSH, but the machine is so hogged up by the Xorg process, that every single keystroke takes a few seconds to show up.

 load average: 5.89, 4.58, 2.94

which seems a bit much for an idling desktop machine ;)

[Here's the Xorg.log running with the Nvidia driver]("http://paste.ubuntu.com/128339/")

It doesn't show anything unusual, imho.

[output of lspci]("http://paste.ubuntu.com/128340/")

/var/log/syslog shows:

```
Mar  8 16:13:26 dreiraumrakete kernel: [ 2819.002113] NVRM: Xid (0002:00): 62, CMDre 00000000 00000000 00000000 00000001 00000001
Mar  8 16:13:29 dreiraumrakete kernel: [ 2822.178156] NVRM: Xid (0002:00): 6, PE0001 
Mar  8 16:13:29 dreiraumrakete acpid: client connected from 13644[0:0] 
Mar  8 16:13:29 dreiraumrakete kernel: [ 2822.187100] NVRM: Xid (0002:00): 62, CMDre 00000000 00000000 00000000 00000001 00000001
Mar  8 16:14:18 dreiraumrakete kernel: [ 2822.777173] NVRM: Xid (0002:00): 6, PE007e 
Mar  8 16:14:18 dreiraumrakete kernel: [ 2822.780928] NVRM: Xid (0002:00): 6, PE007e 0000 80000012 00000000 ffffffff 00000000
Mar  8 16:14:18 dreiraumrakete kernel: [ 2822.784637] NVRM: Xid (0002:00): 6, PE007e 
Mar  8 16:14:18 dreiraumrakete kernel: [ 2822.788300] NVRM: Xid (0002:00): 6, PE007e 0000 80000012 00000000 ffffffff 00000000
Mar  8 16:14:18 dreiraumrakete kernel: [ 2822.792003] NVRM: Xid (0002:00): 6, PE007e 
Mar  8 16:14:18 dreiraumrakete kernel: [ 2822.795656] NVRM: Xid (0002:00): 6, PE007e 0000 80000012 00000000 ffffffff 00000000
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225510] BUG: soft lockup - CPU#3 stuck for 61s! [watchdog/3:14]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] Modules linked in: nvidia(P) ipv6 af_packet binfmt_misc rfcomm bridge stp bnep sco l2cap bluetooth ppdev powernow_k8 cpufreq_powersave cpufreq_ondemand cpufreq_stats cpufreq_conservative freq_table cpufreq_userspace wmi sbs sbshc container video output pci_slot battery iptable_filter ip_tables x_tables ext2 ac lp loop snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore serio_raw pcspkr snd_page_alloc evdev psmouse i2c_piix4 i2c_core parport_pc parport shpchp button pci_hotplug ext3 jbd mbcache sha256_generic aes_x86_64 aes_generic cbc sr_mod cdrom usbhid hid sd_mod crc_t10dif sg pata_atiixp pata_acpi ehci_hcd ata_generic ahci ohci_hcd dm_crypt r8169 dm_mod mii libata crypto_blkcipher usbcore scsi_mod dock thermal processor fan fbcon tileblit font bitblit softcursor fuse [last unloaded: nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] CPU 3:
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] Modules linked in: nvidia(P) ipv6 af_packet binfmt_misc rfcomm bridge stp bnep sco l2cap bluetooth ppdev powernow_k8 cpufreq_powersave cpufreq_ondemand cpufreq_stats cpufreq_conservative freq_table cpufreq_userspace wmi sbs sbshc container video output pci_slot battery iptable_filter ip_tables x_tables ext2 ac lp loop snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore serio_raw pcspkr snd_page_alloc evdev psmouse i2c_piix4 i2c_core parport_pc parport shpchp button pci_hotplug ext3 jbd mbcache sha256_generic aes_x86_64 aes_generic cbc sr_mod cdrom usbhid hid sd_mod crc_t10dif sg pata_atiixp pata_acpi ehci_hcd ata_generic ahci ohci_hcd dm_crypt r8169 dm_mod mii libata crypto_blkcipher usbcore scsi_mod dock thermal processor fan fbcon tileblit font bitblit softcursor fuse [last unloaded: nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] Pid: 14, comm: watchdog/3 Tainted: P          2.6.27-11-generic #1
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] RIP: 0010:[<ffffffff8021a51c>]  [<ffffffff8021a51c>] native_read_tsc+0xc/0x30
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] RSP: 0018:ffff88012f0d3b98  EFLAGS: 00000246
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] RAX: 00000000f457005e RBX: ffff88012f0d3b98 RCX: 00000000f456ffc3
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] RDX: 000000000000064a RSI: 0000000001062560 RDI: 000000000022b8bc
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] RBP: ffff88012f0d3b10 R08: ffff88012c42a000 R09: ffff88012c800920
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] R10: ffff88012008f000 R11: 0000000000000000 R12: ffffffff80213983
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] R13: ffff88012f0d3b10 R14: ffff88012c42f000 R15: ffff88012c42f000
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] FS:  00007f5f111686e0(0000) GS:ffff88012f004080(0000) knlGS:0000000000000000
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] CR2: 00007ff736b10098 CR3: 0000000120dc3000 CR4: 00000000000006e0
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] 
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] Call Trace:
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  <IRQ>  [<ffffffff803ab93c>] ? delay_tsc+0x4c/0x90
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa02c0b00>] ? _nv006973rm+0x0/0xaf [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff803aba13>] ? __const_udelay+0x53/0x60
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa067265a>] ? os_delay+0x1fa/0x290 [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa02c0b00>] ? _nv006973rm+0x0/0xaf [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa05a7ef3>] ? _nv004393rm+0x9/0xe [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa057a04b>] ? _nv002919rm+0x36/0x4b [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa05f4db4>] ? _nv002930rm+0x19e/0x1d2 [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa02c14c5>] ? _nv015707rm+0x295/0x352 [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa0516e93>] ? _nv006955rm+0x2f2/0x47f [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa0425f53>] ? _nv011237rm+0x153/0x28b [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa05dd8fe>] ? _nv003548rm+0x1d8/0x39b [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa05dd518>] ? _nv003547rm+0x84c/0xa5a [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa0429702>] ? _nv010907rm+0x565/0x112d [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa042a38e>] ? _nv010901rm+0xc4/0x9a2 [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa0517387>] ? _nv006932rm+0x26f/0x589 [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa050dea2>] ? _nv006946rm+0x66/0x90 [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa05aa7dd>] ? _nv003182rm+0xad/0xd2 [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa05b0711>] ? rm_isr_bh+0x76/0xa9 [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffffa066e3ad>] ? nv_kern_isr_bh+0x3d/0x70 [nvidia]
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff802546d6>] ? tasklet_action+0x86/0x110
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff80254d9c>] ? __do_softirq+0x8c/0x100
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff80227e0a>] ? ack_apic_level+0x4a/0x140
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff8021417c>] ? call_softirq+0x1c/0x30
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff80215875>] ? do_softirq+0x65/0xa0
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff80254b05>] ? irq_exit+0x95/0xa0
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff80215b1b>] ? do_IRQ+0x8b/0x100
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff80212f0e>] ? ret_from_intr+0x0/0x29
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  <EOI>  [<ffffffff802441c1>] ? finish_task_switch+0x31/0xf0
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff805016e4>] ? thread_return+0x37/0x3c3
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff8029d275>] ? watchdog+0x75/0xc0
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff8029d200>] ? watchdog+0x0/0xc0
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff80266c2e>] ? kthread+0x4e/0x90
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff80213c99>] ? child_rip+0xa/0x11
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff80266be0>] ? kthread+0x0/0x90
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511]  [<ffffffff80213c8f>] ? child_rip+0x0/0x11
Mar  8 16:16:15 dreiraumrakete kernel: [ 2988.225511] 
Mar  8 16:17:42 dreiraumrakete /USR/SBIN/CRON[13657]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

I have no idea where to start - help?

---

### Post by herr_tichy on 2009-03-12
Well yeah, thanks for all the support. However, NVidia Linux support didn't move either, nor did the nv-news forum, so I guess, this is a fundamental problem with the kernel-module.

However, the 8800GTX is up on ebay and has been replaced with two cheap ati cards from my drawer, which of course drew new problems... ;)

---

