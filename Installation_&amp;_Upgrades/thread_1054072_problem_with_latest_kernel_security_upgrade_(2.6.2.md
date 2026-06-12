---
title: "problem with latest kernel security upgrade (2.6.24-23)"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by kt7 on 2009-01-29
I have problem with latest kernel security upgrade for 8.04 (Hardy Heron) :

problematic one:
[FONT="Fixedsys"]
title           Ubuntu 8.04.2, kernel 2.6.24-23-generic
root            (hd1,1)
kernel          /vmlinuz-2.6.24-23-generic root=UUID=78439b5a-0ac7-4f0a-a49d-0f7a10194414 ro quiet splash
initrd          /initrd.img-2.6.24-23-generic
[/FONT]

The kernel before that works fine: 
[FONT="Fixedsys"]
2.6.24-22-generic #1 SMP Mon Nov 24 19:35:06 UTC 2008 x86_64 GNU/Linux[/FONT]

Kernel either freezes when starting, or desktop starts with 800x600 mode and there are no other resolution options in dropdownlist (menu: System > Preferences > Screen resolution). Ati hardware acceleration seems to be on (menu: System > Administration > Hardware Drivers)

I have Fujitsu Siemens laptop AMILO XI 2550 with ATI Mobility Radeon HD2700. I use x86_64 kernels. 

here is problematic part of dmesg (kernel 2.6.24-23):
[FONT="Fixedsys"]
[   42.846615] Bluetooth: RFCOMM TTY layer initialized
[   42.846617] Bluetooth: RFCOMM ver 1.8
[   47.505450] Unable to handle kernel NULL pointer dereference at 0000000000000008 RIP: 
[   47.505453]  [<ffffffff8826ad6c>] :fglrx:__gart_init+0x7c/0x700
[   47.505503] PGD 139ba2067 PUD 129d0a067 PMD 0 
[   47.505505] Oops: 0000 [1] SMP 
[   47.505507] CPU 1 
[   47.505508] Modules linked in: rfcomm l2cap bluetooth ppdev acpi_cpufreq cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative sbs sbshc container dock ipt_LOG xt_limit ipt_addrtype xt_stat
e xt_tcpudp nf_conntrack_ipv4 xt_conntrack ip6table_filter ip6_tables nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables ext3 jbd mbcache ipv6 sbp2 parport_pc lp parport af_packe
t joydev snd_hda_intel wmi_acer snd_seq_dummy snd_pcm_oss snd_mixer_oss iwl4965 iwlwifi_mac80211 snd_seq_oss snd_seq_midi snd_pcm fglrx(P) snd_rawmidi snd_page_alloc snd_hwdep cfg80211 snd_seq_midi_event video output snd_seq iTCO_wdt bat
tery ac button snd_timer iTCO_vendor_support evdev intel_agp snd_seq_device snd psmouse serio_raw pcspkr shpchp pci_hotplug soundcore jfs sr_mod cdrom pata_jmicron sg pata_acpi ata_piix sd_mod usbhid hid sata_sil24 ata_generic ahci ohci1
394 libata ieee1394 r8169 scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   47.505565] Pid: 6158, comm: Xorg Tainted: P        2.6.24-23-generic #1
[   47.505567] RIP: 0010:[<ffffffff8826ad6c>]  [<ffffffff8826ad6c>] :fglrx:__gart_init+0x7c/0x700
[   47.505595] RSP: 0018:ffff810129c8baa8  EFLAGS: 00210202
[   47.505596] RAX: ffff810129c8bac8 RBX: ffff81013a08d008 RCX: 0000000000000000
[   47.505598] RDX: 0000000000000000 RSI: 0000000000000000 RDI: ffff810129c8bcb0
[   47.505599] RBP: ffff810129c8bdf8 R08: 0000000000000000 R09: ffff81013a705a88
[   47.505600] R10: 0000000000000000 R11: ffffffff803327a0 R12: ffff81013a704000
[   47.505601] R13: ffff810129c8bac8 R14: ffff8101376b5600 R15: 0000000000000000
[   47.505603] FS:  00007f9f73b066e0(0000) GS:ffff81013b401800(0000) knlGS:0000000000000000
[   47.505604] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   47.505606] CR2: 0000000000000008 CR3: 0000000129ca8000 CR4: 00000000000006e0
[   47.505607] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   47.505608] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   47.505610] Process Xorg (pid: 6158, threadinfo ffff810129c8a000, task ffff810129d4b7d0)
[   47.505611] Stack:  0000000000000009 0000000000000000 ffff81013771a300 ffffffff802857cd
[   47.505614]  00000026000001e8 0000000000000000 0000000000000000 0000000000000000
[   47.505616]  ffff81013a705a88 0000000000000000 0000000000000000 0000000000000000
[   47.505618] Call Trace:
[   47.505626]  [<ffffffff802857cd>] __grab_cache_page+0x2d/0xa0
[   47.505685]  [<ffffffff88268d44>] :fglrx:gal_init+0xc4/0x160
[   47.505715]  [<ffffffff8826ddd1>] :fglrx:mc_heap_init+0x31/0x5c0
[   47.505719]  [<ffffffff802de1e0>] nr_blockdev_pages+0x10/0x70
[   47.505722]  [<ffffffff8028bff0>] si_meminfo+0x30/0x50
[   47.505745]  [<ffffffff8824ff0c>] :fglrx:KCL_GetAvailableRamPages+0xc/0x20
[   47.505778]  [<ffffffff88260438>] :fglrx:firegl_init_pcie+0x1b8/0x310
[   47.505781]  [<ffffffff80296774>] handle_mm_fault+0x594/0x7b0
[   47.505814]  [<ffffffff88260280>] :fglrx:firegl_init_pcie+0x0/0x310
[   47.505841]  [<ffffffff8825c46a>] :fglrx:firegl_ioctl+0x1ba/0x230
[   47.505849]  [<ffffffff802c0c5d>] do_ioctl+0x7d/0xa0
[   47.505852]  [<ffffffff802c0ea0>] vfs_ioctl+0x220/0x2c0
[   47.505856]  [<ffffffff802b368e>] vfs_write+0x14e/0x190
[   47.505860]  [<ffffffff802c0fd1>] sys_ioctl+0x91/0xb0
[   47.505866]  [<ffffffff8020c39e>] system_call+0x7e/0x83
[   47.505874] 
[   47.505874] 
[   47.505875] Code: 49 8b 78 08 48 89 7c 24 38 31 ff 49 8b b4 24 68 1b 00 00 48 

[/FONT] .. and so on.

here is same part of dmesg with earlier kernel ( 2.6.24-22-generic):
[FONT="Fixedsys"]
[   43.362571] Bluetooth: RFCOMM TTY layer initialized
[   43.362572] Bluetooth: RFCOMM ver 1.8
45.913902] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   48.130688] [fglrx] Reserve Block - 0 offset =  0Xfffc000 length = 0X4000
[   48.130692] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   48.130693] [fglrx] Reserve Block - 2 offset =  0Xff7b000 length = 0X80000
[   48.486231] [fglrx] interrupt source 10000000 successfully enabled
[   48.486236] [fglrx] enable ID = 0x00000006
[   48.486244] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   48.498108] [fglrx] interrupt source 60000001 successfully enabled
[   48.498110] [fglrx] enable ID = 0x00000007
[   48.498113] [fglrx] Receive enable interrupt message with irqEnableMask: 60000001
[   48.498142] [fglrx] interrupt source 00000040 successfully enabled
[   48.498143] [fglrx] enable ID = 0x00000008
[   48.498145] [fglrx] Receive enable interrupt message with irqEnableMask: 00000040
[   48.514882] [fglrx] interrupt source ff00002c successfully enabled
[   48.514884] [fglrx] enable ID = 0x00000009
[   48.514886] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002c
[   48.514915] [fglrx] interrupt source ff00002d successfully enabled
[   48.514916] [fglrx] enable ID = 0x0000000A
[   48.514918] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002d
[   48.514934] [fglrx] interrupt source 20000400 successfully enabled
[   48.514936] [fglrx] enable ID = 0x0000000B
[   48.514938] [fglrx] Receive enable interrupt message with irqEnableMask: 20000400
[   92.210997] CPU0 attaching NULL sched-domain.
[   92.211002] CPU1 attaching NULL sched-domain.
[   92.233701] CPU0 attaching sched-domain:
[   92.233705]  domain 0: span 03
[   92.233707]   groups: 01 02
[   92.233710]   domain 1: span 03
[   92.233712]    groups: 03
[   92.233714] CPU1 attaching sched-domain:
[   92.233715]  domain 0: span 03
[   92.233717]   groups: 02 01
[   92.233719]   domain 1: span 03
[   92.233720]    groups: 03
[ 4095.828940] npviewer.bin[11036]: segfault at f58ef030 rip f78c7540 rsp ffe30d8c error 4
[ 6591.300213] npviewer.bin[13657]: segfault at f5932030 rip f790a540 rsp ffa4b45c error 4

[/FONT]

---

### Post by buckrodgers on 2009-02-17
Sorry, I'm nor gona help I have a similar issue,

Since I've upgraded to 2.6.27-12 I do not manage to mount UFS volumes anymore.

I have a Wrong FS type when I try to mount any JFS partition and of course passing the partition through fsck dose not identify any issue with the JFS partition.

I do not have a clue, did the latest versions of the kernel stopped support for JFS ?

Cheers

---

