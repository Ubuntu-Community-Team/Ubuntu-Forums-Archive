---
title: "kernel freeze due to acpi problem on dual core cpu"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by jose99m on 2007-11-10
Hi,

My kernel freezes randomly during utilisation since i have installed a dual core cpu (even with the live cd !). 
2.6.22 needs a hard reset, while 2.6.17 reboots by itself.
acpi=off no acpi option permits a normal utilization of the PC, but i need to manually push the off button.

What can i do ? Compile an optimized kernel ? Try an AMD64 one ?

DFI lanparty ultraD, Athlon X2 4200+, Gutsy 7.10

Windows is working fine

Here is the syslog

Nov  7 18:24:58 desktop kernel: [   75.604000] kernel BUG at /build/buildd/linux-source-2.6.22-2.6.22/mm/mmap.c:1996!
Nov  7 18:24:58 desktop kernel: [   75.604000] invalid opcode: 0000 [#2]
Nov  7 18:24:58 desktop kernel: [   75.604000] SMP 
Nov  7 18:24:58 desktop kernel: [   75.604000] Modules linked in: ipv6 af_packet binfmt_misc rfcomm l2cap bluetooth ppdev powernow_k8 cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative video sbs button dock container ac battery nls_iso8859_1 nls_cp437 vfat fat sbp2 parport_pc lp parport snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq nvidia(P) snd_timer irtty_sir agpgart snd_seq_device sir_dev snd irda crc_ccitt pcspkr psmouse serio_raw shpchp pci_hotplug i2c_nforce2 soundcore snd_page_alloc k8temp i2c_core evdev ext3 jbd mbcache ide_cd cdrom ide_disk sata_nv amd74xx ide_core floppy skge ohci1394 ieee1394 natsemi ata_generic libata scsi_mod forcedeth ehci_hcd ohci_hcd usbcore thermal processor fan fuse apparmor commoncap
Nov  7 18:24:58 desktop kernel: [   75.604000] CPU:    1
Nov  7 18:24:58 desktop kernel: [   75.604000] EIP:    0060:[exit_mmap+235/240]    Tainted: P       VLI
Nov  7 18:24:58 desktop kernel: [   75.604000] EFLAGS: 00210206   (2.6.22-14-generic #1)
Nov  7 18:24:58 desktop kernel: [   75.604000] EIP is at exit_mmap+0xeb/0xf0
Nov  7 18:24:58 desktop kernel: [   75.604000] eax: 00000000   ebx: c18132c0   ecx: f7323688   edx: f73235d8
Nov  7 18:24:58 desktop kernel: [   75.604000] esi: 00000000   edi: 00000003   ebp: 00200202   esp: f732fcf5
Nov  7 18:24:58 desktop kernel: [   75.604000] ds: 007b   es: 007b   fs: 00d8  gs: 0000  ss: 0068
Nov  7 18:24:58 desktop kernel: [   75.604000] Process gnome-panel (pid: 6062, ti=f732e000 task=f0688f90 task.ti=f732e000)
Nov  7 18:24:58 desktop kernel: [   75.604000] Stack: 00000000 f732fd01 00000000 00000922 c18132c0 f17bea80 f17beac8 00000001 
Nov  7 18:24:58 desktop kernel: [   75.604000]        c01260c8 00000000 f0688f90 c012b5ff 00200202 c0105223 f732fddd 00200202 
Nov  7 18:24:58 desktop kernel: [   75.604000]        00000000 f732fe15 c0370068 0000000b 00200202 0000007b 0000007b 000000d8 
Nov  7 18:24:58 desktop kernel: [   75.604000] Call Trace:
Nov  7 18:24:58 desktop kernel: [   75.604000]  [mmput+56/160] mmput+0x38/0xa0
Nov  7 18:24:58 desktop kernel: [   75.604000]  [do_exit+271/2064] do_exit+0x10f/0x810
Nov  7 18:24:58 desktop kernel: [   75.604000]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Nov  7 18:24:58 desktop kernel: [   75.604000]  [die+607/608] die+0x25f/0x260
Nov  7 18:24:58 desktop kernel: [   75.604000]  [do_page_fault+827/1680] do_page_fault+0x33b/0x690
Nov  7 18:24:58 desktop kernel: [   75.604000]  [do_page_fault+0/1680] do_page_fault+0x0/0x690
Nov  7 18:24:58 desktop kernel: [   75.604000]  [error_code+114/128] error_code+0x72/0x80
Nov  7 18:24:58 desktop kernel: [   75.604000]  =======================
Nov  7 18:24:58 desktop kernel: [   75.604000] Code: 5b 5e 5f c3 8b 03 c7 43 08 00 00 00 00 e8 3e 71 fa ff 8b 53 04 83 fa ff 74 c6 8d 43 10 e8 6e 55 00 00 c7 43 04 00 00 00 00 eb b5 <0f> 0b eb fe 90 83 ec 1c 89 5c 24 0c 89 c3 89 74 24 10 89 d6 89 
Nov  7 18:24:58 desktop kernel: [   75.604000] EIP: [exit_mmap+235/240] exit_mmap+0xeb/0xf0 SS:ESP 0068:f732fcf5
Nov  7 18:24:58 desktop kernel: [   75.604000] Fixing recursive fault but reboot is needed!

---

### Post by jose99m on 2007-11-11
No idea ?

---

### Post by squideekie on 2008-02-02
I have the problem with an older dual athlon xp/mp board. do you get the hang up loading hardware drivers: unable to register resource?

---

### Post by stream303 on 2008-02-02
I found that using
[B]
acpi_irq_balance[/B]

as a kernel parameter really helped my dual-core HP tablet.  I used HTOP rather than any gui applets to monitor the cpu load.

My kernel parameters for my machine are:

```
ro quiet splash showopts **noapic acpi_irq_balance**
```

noapic was mandatory for my HP, but give acpi_irq_balance a shot on cranky smp boxes....

---

