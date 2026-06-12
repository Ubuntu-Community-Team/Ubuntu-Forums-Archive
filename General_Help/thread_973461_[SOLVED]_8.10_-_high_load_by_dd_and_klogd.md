---
title: "[SOLVED] 8.10 - high load by dd and klogd"
date: 2008-11-06
forum: General Help
---

### Post by flytolszh on 2008-11-06
I freshly installed 8.10 on my pc. After startup, dd and klogd produce a very high load and the following log files gain rapidly in size: messages, syslog, kern.log. All of them contain repeatedly very similar messages (from kern.log):

```

Nov  6 22:32:15 celsius kernel: [   14.452644] ------------[ cut here ]------------
Nov  6 22:32:15 celsius kernel: [   14.452646] WARNING: at /build/buildd/linux-2.6.27/arch/x86/kernel/hpet.c:286 hpet_legacy_next_event+0x5e/0x60()
Nov  6 22:32:15 celsius kernel: [   14.452648] Modules linked in: acpi_cpufreq cpufreq_powersave cpufreq_conservative cpufreq_userspace cpufreq_stats cpufreq_ondemand freq_table pci_slot sbs sbshc video output wmi battery iptable_filter ip_tables x_tables ac sbp2 lp snd_hda_intel snd_pcm_oss snd_mixer_oss psmouse serio_raw snd_pcm evdev parport_pc joydev pcspkr parport snd_seq_dummy snd_seq_oss tpm_infineon snd_seq_midi tpm container tpm_bios snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device button intel_agp snd agpgart shpchp soundcore pci_hotplug snd_page_alloc ext3 jbd mbcache sd_mod sr_mod crc_t10dif cdrom usbhid hid sg usb_storage libusual ata_piix pata_acpi ohci1394 ieee1394 ata_generic libata scsi_mod dock uhci_hcd ehci_hcd usbcore e1000e thermal processor fan fbcon tileblit font bitblit softcursor fuse
Nov  6 22:32:15 celsius kernel: [   14.452691] Pid: 0, comm: swapper Tainted: G        W 2.6.27-7-generic #1
Nov  6 22:32:15 celsius kernel: [   14.452692]  [<c037c3f6>] ? printk+0x1d/0x1f
Nov  6 22:32:15 celsius kernel: [   14.452695]  [<c0131de9>] warn_on_slowpath+0x59/0x90
Nov  6 22:32:15 celsius kernel: [   14.452698]  [<c014e63b>] ? getnstimeofday+0x4b/0x100
Nov  6 22:32:15 celsius kernel: [   14.452701]  [<c0136976>] ? set_normalized_timespec+0x16/0x90
Nov  6 22:32:15 celsius kernel: [   14.452703]  [<c0151c84>] ? clockevents_program_event+0x14/0x150
Nov  6 22:32:15 celsius kernel: [   14.452706]  [<c014b79e>] ? ktime_get+0x1e/0x40
Nov  6 22:32:15 celsius kernel: [   14.452709]  [<c015310b>] ? tick_dev_program_event+0x3b/0xc0
Nov  6 22:32:15 celsius kernel: [   14.452711]  [<c014b23b>] ? hrtimer_get_next_event+0x10b/0x130
Nov  6 22:32:15 celsius kernel: [   14.452714]  [<c0118e38>] ? read_hpet+0x8/0x20
Nov  6 22:32:15 celsius kernel: [   14.452717]  [<c014e63b>] ? getnstimeofday+0x4b/0x100
Nov  6 22:32:15 celsius kernel: [   14.452719]  [<c037df9e>] ? account_scheduler_latency+0xe/0x220
Nov  6 22:32:15 celsius kernel: [   14.452722]  [<c0118e38>] ? read_hpet+0x8/0x20
Nov  6 22:32:15 celsius kernel: [   14.452724]  [<c014e63b>] ? getnstimeofday+0x4b/0x100
Nov  6 22:32:15 celsius kernel: [   14.452727]  [<c011969e>] hpet_legacy_next_event+0x5e/0x60
Nov  6 22:32:15 celsius kernel: [   14.452729]  [<c0151d0f>] clockevents_program_event+0x9f/0x150
Nov  6 22:32:15 celsius kernel: [   1<+15_21n[_<4i<. f48er <i r5i tsc=74--b/5 pfcf  drae _eqsr lms1 1n pW4+c0e80>][0
Nov  6 22:32:15 celsius kernel: <m0m 1nt0_event+0x3b/0xc0
Nov  6 22:32:15 celsius kernel: [   14.453093]  [<c0118e38>] ? read_hpet+0x8/0x20
Nov  6 22:32:15 celsius kernel: [   14.453096]  [<c014e63b>] ? getnstimeofday+0x4b/0x100
Nov  6 22:32:15 celsius kernel: [   14.453098]  [<c011969e>] hpet_legacy_next_event+0x5e/0x60
Nov  6 22:32:15 celsius kernel: [   14.453101]  [<c0151d0f>] clockevents_program_event+0x9f/0x150
Nov  6 22:32:15 celsius kernel: [   14.453103]  [<c015310b>] tick_dev_program_event+0x3b/0xc0
Nov  6 22:32:15 celsius kernel: [   14.453105]  [<c0152be0>] tick_handle_oneshot_broadcast+0x100/0x120
Nov  6 22:32:15 celsius kernel: [   14.453108]  [<c0106c85>] timer_interrupt+0x35/0x80
Nov  6 22:32:15 celsius kernel: [   14.453110]  [<c01770b1>] handle_IRQ_event+0x41/0x80
Nov  6 22:32:15 celsius kernel: [   14.453113]  [<c0178871>] handle_edge_irq+0xb1/0x120
Nov  6 22:32:15 celsius kernel: [   14.453115]  [<c0106c15>] do_IRQ+0x45/0x80
Nov  6 22:32:15 celsius kernel: [   14.453117]  [<c0105003>] common_interrupt+0x23/0x30
Nov  6 22:32:15 celsius kernel: [   14.453119]  [<c01700d8>] ? __audit_mq_getsetattr+0x68/0xb0
Nov  6 22:32:15 celsius kernel: [   14.453123]  [<f8876800>] ? acpi_idle_enter_bm+0x268/0x2b7 [processor]
Nov  6 22:32:15 celsius kernel: [   14.453127]  [<c02dbf7b>] cpuidle_idle_call+0x7b/0xd0
Nov  6 22:32:15 celsius kernel: [   14.453129]  [<c010288d>] cpu_idle+0x7d/0x140
Nov  6 22:32:15 celsius kernel: [   14.453131]  [<c037a651>] start_secondary+0x9d/0xcc
Nov  6 22:32:15 celsius kernel: [   14.453134]  =======================
Nov  6 22:32:15 celsius kernel: [   14.453135] ---[ end trace 0d4795f4a662fa41 ]---

```

uname -a:
```

Linux celsius 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

```

I have seen other threads about a similar behaviour, but there the root cause was in the area of wlan drivers. However, I do not have a WLAN adapter in my desk-bound system.

I installed all updates available at the time of this posting.

After killing dd and klogd, the laod is reduced to a normal level. Any ideas what causes my issues or how I could avoid them?

---

### Post by dustice on 2008-11-07
I'm getting the same issue and after poking around a bit I think this is the bug; [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286285)

Dunno if there's anything we can do except wait for the next kernel release. Killing klogd seems to be an alright workaround though =P

---

### Post by flytolszh on 2008-11-07
Thank you for the hint. Indeed, killing klogd helps. The bug you are referring to seems to be about wlan and bluetooth drivers. As I don't have hardware devices of that type in my workstation, I guess it must be something different.

For the time being, I disabled klogd in all runlevels. However, that's hopefully a temporary solution until a new, fixed kernel is made available.

---

### Post by funchords on 2008-11-08
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/295781](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/295781) has been entered.  O.P. should follow and/or add comments on this launchpad report.

---

