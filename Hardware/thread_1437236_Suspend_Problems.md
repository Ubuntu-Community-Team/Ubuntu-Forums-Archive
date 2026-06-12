---
title: "Suspend Problems"
date: 2010-03-23
forum: Hardware
---

### Post by johnzollo on 2010-03-23
I cannot get my DFI LanParty nF4 Ultra-D motherboard to suspend.  I have default BIOS setting, and I'm pretty sure the BIOS is current.

Here's my kernel.log:

```
Mar 23 16:22:52 loadr kernel: [  104.984017] skge eth1: disabling interface
Mar 23 16:22:55 loadr kernel: [  108.032561] PM: Syncing filesystems ... done.
Mar 23 16:22:55 loadr kernel: [  108.046829] PM: Preparing system for mem sleep
Mar 23 16:23:05 loadr kernel: [  108.047328] Freezing user space processes ... (elapsed 0.00 seconds) done.
Mar 23 16:23:05 loadr kernel: [  108.048160] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Mar 23 16:23:05 loadr kernel: [  108.048210] PM: Entering mem sleep
Mar 23 16:23:05 loadr kernel: [  108.048212] Suspending console(s) (use no_console_suspend to debug)
Mar 23 16:23:05 loadr kernel: [  108.048503] sd 4:0:0:0: [sda] Stopping disk
Mar 23 16:23:05 loadr kernel: [  109.372233] ACPI handle has no context!
Mar 23 16:23:05 loadr kernel: [  109.372560] serial 00:08: disabled
Mar 23 16:23:05 loadr kernel: [  109.373261] ACPI handle has no context!
Mar 23 16:23:05 loadr kernel: [  109.373264] ACPI handle has no context!
Mar 23 16:23:05 loadr kernel: [  109.393021] ACPI handle has no context!
Mar 23 16:23:05 loadr kernel: [  109.408018] s3fb 0000:01:06.0: suspend
Mar 23 16:23:05 loadr kernel: [  109.408036] s3fb 0000:01:06.0: PCI INT A disabled
Mar 23 16:23:05 loadr kernel: [  109.408099] forcedeth 0000:00:0a.0: wake-up capability disabled by ACPI
Mar 23 16:23:05 loadr kernel: [  109.408101] forcedeth 0000:00:0a.0: PME# disabled
Mar 23 16:23:05 loadr kernel: [  109.408104] forcedeth 0000:00:0a.0: PCI INT A disabled
Mar 23 16:23:05 loadr kernel: [  109.424059] sata_nv 0000:00:08.0: PCI INT A disabled
Mar 23 16:23:05 loadr kernel: [  109.440046] sata_nv 0000:00:07.0: PCI INT A disabled
Mar 23 16:23:05 loadr kernel: [  109.472190] Intel ICH 0000:00:04.0: PCI INT A disabled
Mar 23 16:23:05 loadr kernel: [  109.472216] ehci_hcd 0000:00:02.1: PCI INT B disabled
Mar 23 16:23:05 loadr kernel: [  109.488030] ohci_hcd 0000:00:02.0: PCI INT A disabled
Mar 23 16:23:05 loadr kernel: [  109.504018] ohci_hcd 0000:00:02.0: PME# enabled
Mar 23 16:23:05 loadr kernel: [  109.504025] ohci_hcd 0000:00:02.0: wake-up capability enabled by ACPI
Mar 23 16:23:05 loadr kernel: [  109.504027] ohci_hcd 0000:00:02.0: PME# enabled
Mar 23 16:23:05 loadr kernel: [  109.504029] ohci_hcd 0000:00:02.0: wake-up capability enabled by ACPI
Mar 23 16:23:05 loadr kernel: [  109.504060] PM: suspend devices took 1.456 seconds
Mar 23 16:23:05 loadr kernel: [  109.504130] ACPI: Preparing to enter system sleep state S3
Mar 23 16:23:05 loadr kernel: [  109.505431] Disabling non-boot CPUs ...
Mar 23 16:23:05 loadr kernel: [  109.505431] Back to C!
Mar 23 16:23:05 loadr kernel: [  109.505431] pci 0000:00:00.0: restoring config space at offset 0xf (was 0x0, writing 0xff)
Mar 23 16:23:05 loadr kernel: [  109.505431] pci 0000:00:09.0: restoring config space at offset 0x7 (was 0x2280a0a0, writing 0xa280a0a0)
Mar 23 16:23:05 loadr kernel: [  109.505431] pcieport-driver 0000:00:0b.0: Linking AER extended capability
Mar 23 16:23:05 loadr kernel: [  109.505431] pcieport-driver 0000:00:0b.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
Mar 23 16:23:05 loadr kernel: [  109.505431] pcieport-driver 0000:00:0c.0: Linking AER extended capability
Mar 23 16:23:05 loadr kernel: [  109.505431] pcieport-driver 0000:00:0c.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
Mar 23 16:23:05 loadr kernel: [  109.505431] pcieport-driver 0000:00:0d.0: Linking AER extended capability
Mar 23 16:23:05 loadr kernel: [  109.505431] pcieport-driver 0000:00:0d.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
Mar 23 16:23:05 loadr kernel: [  109.505431] pcieport-driver 0000:00:0e.0: Linking AER extended capability
Mar 23 16:23:05 loadr kernel: [  109.505431] pcieport-driver 0000:00:0e.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
Mar 23 16:23:05 loadr kernel: [  109.508394] ACPI: Waking up from system sleep state S3
Mar 23 16:23:05 loadr kernel: [  109.509471] ACPI: Unable to turn cooling device [ffff88007fb3ca00] 'off'
Mar 23 16:23:05 loadr kernel: [  109.509478] ohci_hcd 0000:00:02.0: wake-up capability disabled by ACPI
Mar 23 16:23:05 loadr kernel: [  109.509480] ohci_hcd 0000:00:02.0: PME# disabled
Mar 23 16:23:05 loadr kernel: [  109.509482] ohci_hcd 0000:00:02.0: wake-up capability disabled by ACPI
Mar 23 16:23:05 loadr kernel: [  109.509484] ohci_hcd 0000:00:02.0: PME# disabled
Mar 23 16:23:05 loadr kernel: [  109.524559] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 22 (level, low) -> IRQ 22
Mar 23 16:23:05 loadr kernel: [  109.524563] ohci_hcd 0000:00:02.0: setting latency timer to 64
Mar 23 16:23:05 loadr kernel: [  109.564579] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 23 (level, low) -> IRQ 23
Mar 23 16:23:05 loadr kernel: [  109.564581] ehci_hcd 0000:00:02.1: setting latency timer to 64
Mar 23 16:23:05 loadr kernel: [  109.564613] Intel ICH 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, low) -> IRQ 22
Mar 23 16:23:05 loadr kernel: [  109.564615] Intel ICH 0000:00:04.0: setting latency timer to 64
Mar 23 16:23:05 loadr kernel: [  109.588535] pata_amd 0000:00:06.0: setting latency timer to 64
Mar 23 16:23:05 loadr kernel: [  109.604543] sata_nv 0000:00:07.0: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00007)
Mar 23 16:23:05 loadr kernel: [  109.604550] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
Mar 23 16:23:05 loadr kernel: [  109.604552] sata_nv 0000:00:07.0: setting latency timer to 64
Mar 23 16:23:05 loadr kernel: [  109.620309] sata_nv 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00007)
Mar 23 16:23:05 loadr kernel: [  109.620316] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 20 (level, low) -> IRQ 20
Mar 23 16:23:05 loadr kernel: [  109.620318] sata_nv 0000:00:08.0: setting latency timer to 64
Mar 23 16:23:05 loadr kernel: [  109.620426] pci 0000:00:09.0: setting latency timer to 64
Mar 23 16:23:05 loadr kernel: [  109.636309] forcedeth 0000:00:0a.0: restoring config space at offset 0x1 (was 0xb00003, writing 0xb80007)
Mar 23 16:23:05 loadr kernel: [  109.636314] forcedeth 0000:00:0a.0: wake-up capability disabled by ACPI
Mar 23 16:23:05 loadr kernel: [  109.636316] forcedeth 0000:00:0a.0: PME# disabled
Mar 23 16:23:05 loadr kernel: [  109.636340] pcieport-driver 0000:00:0b.0: setting latency timer to 64
Mar 23 16:23:05 loadr kernel: [  109.636344] pcieport-driver 0000:00:0c.0: setting latency timer to 64
Mar 23 16:23:05 loadr kernel: [  109.636347] pcieport-driver 0000:00:0d.0: setting latency timer to 64
Mar 23 16:23:05 loadr kernel: [  109.636351] pcieport-driver 0000:00:0e.0: setting latency timer to 64
Mar 23 16:23:05 loadr kernel: [  109.636355] s3fb 0000:01:06.0: resume
Mar 23 16:23:05 loadr kernel: [  109.636369] s3fb 0000:01:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Mar 23 16:23:05 loadr kernel: [  109.710909] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fbfff000-fbfff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Mar 23 16:23:05 loadr kernel: [  109.733574] serial 00:08: activated
Mar 23 16:23:05 loadr kernel: [  110.256294] usb 2-2: reset full speed USB device using ohci_hcd and address 2
Mar 23 16:23:05 loadr kernel: [  110.328307] ata2: SATA link down (SStatus 0 SControl 300)
Mar 23 16:23:05 loadr kernel: [  110.328316] ata1: SATA link down (SStatus 0 SControl 300)
Mar 23 16:23:05 loadr kernel: [  110.344459] ata4: SATA link down (SStatus 0 SControl 300)
Mar 23 16:23:05 loadr kernel: [  110.344467] ata3: SATA link down (SStatus 0 SControl 300)
Mar 23 16:23:05 loadr kernel: [  110.778303] usb 2-2.1: reset full speed USB device using ohci_hcd and address 3
Mar 23 16:23:05 loadr kernel: [  111.378310] usb 2-2.2: reset low speed USB device using ohci_hcd and address 4
Mar 23 16:23:05 loadr kernel: [  111.950310] usb 2-2.1.1: reset low speed USB device using ohci_hcd and address 5
Mar 23 16:23:05 loadr kernel: [  112.329310] usb 2-2.1.3: reset full speed USB device using ohci_hcd and address 6
Mar 23 16:23:05 loadr kernel: [  112.452322] sd 4:0:0:0: [sda] Starting disk
Mar 23 16:23:05 loadr kernel: [  114.644157] ata5: link is slow to respond, please be patient (ready=0)
Mar 23 16:23:05 loadr kernel: [  115.536379] ata5.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Mar 23 16:23:05 loadr kernel: [  115.536381] ata5.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Mar 23 16:23:05 loadr kernel: [  115.536395] ata5: nv_mode_filter: 0x701f&0x701f->0x701f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
Mar 23 16:23:05 loadr kernel: [  115.696318] ata5.00: configured for UDMA/33
Mar 23 16:23:05 loadr kernel: [  115.704425] sd 4:0:0:0: [sda] 19807200 512-byte hardware sectors (10141 MB)
Mar 23 16:23:05 loadr kernel: [  115.704439] sd 4:0:0:0: [sda] Write Protect is off
Mar 23 16:23:05 loadr kernel: [  115.704441] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 23 16:23:05 loadr kernel: [  115.704462] sd 4:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Mar 23 16:23:05 loadr kernel: [  115.704704] PM: resume devices took 6.196 seconds
Mar 23 16:23:05 loadr kernel: [  115.704710] ------------[ cut here ]------------
Mar 23 16:23:05 loadr kernel: [  115.704711] WARNING: at /build/buildd/linux-2.6.27/kernel/power/main.c:176 suspend_test_finish+0x75/0x80()
Mar 23 16:23:05 loadr kernel: [  115.704713] Modules linked in: binfmt_misc sco bridge stp bnep rfcomm l2cap bluetooth ppdev cpufreq_conservative cpufreq_ondemand cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave pci_slot video output sbs sbshc container wmi battery iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport pcspkr k8temp evdev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd i2c_nforce2 s3fb svgalib vgastate soundcore snd_page_alloc button shpchp pci_hotplug i2c_core ext3 jbd mbcache sd_mod crc_t10dif sg usbhid hid pata_amd sata_nv ata_generic pata_acpi skge ohci1394 libata ohci_hcd ieee1394 forcedeth ehci_hcd scsi_mod dock usbcore floppy thermal processor fan fbcon tileblit font bitblit softcursor fuse compcache lzo_decompress lzo_compress tlsf
Mar 23 16:23:05 loadr kernel: [  115.704747] Pid: 5653, comm: pm-suspend Not tainted 2.6.27-16-generic #1
Mar 23 16:23:05 loadr kernel: [  115.704749] 
Mar 23 16:23:05 loadr kernel: [  115.704749] Call Trace:
Mar 23 16:23:05 loadr kernel: [  115.704754]  [<ffffffff8024eb64>] warn_on_slowpath+0x64/0x90
Mar 23 16:23:05 loadr kernel: [  115.704758]  [<ffffffff80501efc>] ? printk+0x6c/0x70
Mar 23 16:23:05 loadr kernel: [  115.704762]  [<ffffffff803a5017>] ? kobject_put+0x27/0x60
Mar 23 16:23:05 loadr kernel: [  115.704764]  [<ffffffff80502fb9>] ? mutex_unlock+0x9/0x20
Mar 23 16:23:05 loadr kernel: [  115.704767]  [<ffffffff8043659a>] ? dpm_complete+0x18a/0x1a0
Mar 23 16:23:05 loadr kernel: [  115.704769]  [<ffffffff8027e4e5>] suspend_test_finish+0x75/0x80
Mar 23 16:23:05 loadr kernel: [  115.704772]  [<ffffffff8027e5f4>] suspend_devices_and_enter+0x104/0x1b0
Mar 23 16:23:05 loadr kernel: [  115.704774]  [<ffffffff8027e8b1>] enter_state+0xe1/0x110
Mar 23 16:23:05 loadr kernel: [  115.704776]  [<ffffffff8027e99a>] state_store+0xba/0x100
Mar 23 16:23:05 loadr kernel: [  115.704778]  [<ffffffff803a4eb7>] kobj_attr_store+0x17/0x20
Mar 23 16:23:05 loadr kernel: [  115.704781]  [<ffffffff8034a25a>] sysfs_write_file+0xca/0x140
Mar 23 16:23:05 loadr kernel: [  115.704784]  [<ffffffff802ea4cb>] vfs_write+0xcb/0x130
Mar 23 16:23:05 loadr kernel: [  115.704786]  [<ffffffff802ea625>] sys_write+0x55/0x90
Mar 23 16:23:05 loadr kernel: [  115.704789]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
Mar 23 16:23:05 loadr kernel: [  115.704791] 
Mar 23 16:23:05 loadr kernel: [  115.704792] ---[ end trace aed2d889a91477f1 ]---
Mar 23 16:23:05 loadr kernel: [  115.704809] PM: Finishing wakeup.
Mar 23 16:23:05 loadr kernel: [  115.704811] Restarting tasks ... done.
Mar 23 16:23:07 loadr kernel: [  117.085700] eth0: no link during initialization.
Mar 23 16:23:07 loadr kernel: [  117.088810] skge eth1: enabling interface
```

Anything you could do would be greatly appreciated!!!

thanks in advance!

Sincerely,
John

---

### Post by Muzer on 2010-03-23
Try fiddling with settings to do with ACPI in the BIOS - make sure you write down what they were beforehand so you can change them back if it makes it worse!

---

### Post by johnzollo on 2010-03-24
Muzer, thanks for the idea.  Turns out it was my USB based KVM switch.  Much better now.  Then I had an issue with my nvidia graphics card.  I used the binary driver, and now that's coming back from suspend too.  The only problem I have left is my SATA Maxtor HDD.  Everything else comes back ok, but the drive is lost after restore.

Any ideas???

thanks!

-john

---

