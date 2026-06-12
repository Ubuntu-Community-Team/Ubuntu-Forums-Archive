---
title: "iPod not recognized"
date: 2006-04-22
forum: Hardware &amp; Laptops
---

### Post by escobar5 on 2006-04-22
Hello,

i'm having problems trying to connect my 3 Gen iPod, it doesn't get recognized, this is what i get when i connect it and run dmesg:

```

[4295348.444000] usb 4-2: new full speed USB device using uhci_hcd and address 2[4295348.598000] usb 4-2: device descriptor read/64, error -71
[4295348.773000] usb 4-2: device descriptor read/64, error -71
[4295348.936000] usb 4-2: new full speed USB device using uhci_hcd and address 3[4295349.010000] usb 4-2: device descriptor read/64, error -71
[4295349.185000] usb 4-2: device descriptor read/64, error -71
[4295349.348000] usb 4-2: new full speed USB device using uhci_hcd and address 4[4295349.758000] usb 4-2: device not accepting address 4, error -71
[4295349.820000] usb 4-2: new full speed USB device using uhci_hcd and address 5[4295350.228000] usb 4-2: device not accepting address 5, error -71
[4295352.494000] usb 5-8: new high speed USB device using ehci_hcd and address 6[4295352.682000] Initializing USB Mass Storage driver...
[4295352.685000] scsi2 : SCSI emulation for USB Mass Storage devices
[4295352.686000] usb-storage: device found at 6
[4295352.686000] usb-storage: waiting for device to settle before scanning
[4295352.686000] usbcore: registered new driver usb-storage
[4295352.686000] USB Mass Storage support registered.
[4295427.748000] usb 5-8: reset high speed USB device using ehci_hcd and address 6
[4295427.833000] usb 5-8: device descriptor read/64, error -71
[4295428.016000] usb 5-8: device descriptor read/64, error -71
[4295428.179000] usb 5-8: reset high speed USB device using ehci_hcd and address 6
[4295428.260000] usb 5-8: device descriptor read/64, error -71
[4295428.433000] usb 5-8: device descriptor read/64, error -71
[4295428.596000] usb 5-8: reset high speed USB device using ehci_hcd and address 6
[4295433.608000] usb 5-8: device descriptor read/8, error -110
[4295438.720000] usb 5-8: device descriptor read/8, error -110
[4295438.883000] usb 5-8: reset high speed USB device using ehci_hcd and address 6
[4295443.895000] usb 5-8: device descriptor read/8, error -110
[4295449.007000] usb 5-8: device descriptor read/8, error -110
[4295449.108000] scsi: Device offlined - not ready after error recovery: host 2 channel 0 id 0 lun 0
[4295449.108000] usb 5-8: USB disconnect, address 6
[4295449.108000] usb-storage: device scan complete
[4295449.108000] Unable to handle kernel NULL pointer dereference at virtual address 00000048
[4295449.108000]  printing eip:
[4295449.108000] c01748fd
[4295449.108000] *pde = 00000000
[4295449.108000] Oops: 0000 [#1]
[4295449.108000] Modules linked in: usb_storage binfmt_misc rfcomm l2cap bluetooth speedstep_lib cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi i2c_acpi_ec i2c_core button battery container ac ipv6 af_packet floppy pcspkr rtc joydev tsdev wacom usblp snd_cmipci gameport snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_opl3_lib snd_timer snd_hwdep snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore tpm_atmel tpm_nsc tpm hw_random shpchp pci_hotplug intel_agp nls_iso8859_1 vfat fat nls_cp437 ntfs dm_mod evdev fglrx agpgart psmouse mousedev parport_pc lp parport md ext3 jbd thermal processor fan usbhid e1000 ehci_hcd uhci_hcd usbcore sd_mod ide_cd cdrom ide_generic ata_piix libata scsi_mod piix ide_core unix vesafb capability commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit
[4295449.108000] CPU:    0
[4295449.108000] EIP:    0060:[<c01748fd>]    Tainted: P      VLI
[4295449.108000] EFLAGS: 00010286   (2.6.12-10-386)
[4295449.108000] EIP is at sysfs_hash_and_remove+0x8/0xd0
[4295449.108000] eax: 00000000   ebx: f88fbf00   ecx: 00000003   edx: f2c6b248
[4295449.108000] esi: f2c6b248   edi: f88fbea0   ebp: df8bb1fc   esp: c198be3c
[4295449.108000] ds: 007b   es: 007b   ss: 0068
[4295449.108000] Process khubd (pid: 3168, threadinfo=c198a000 task=dfb7b020)
[4295449.108000] Stack: f88fbf00 f2c6b248 f88fbea0 df8bb1fc c01ed151 00000000 c0278545 f2c6b248
[4295449.108000]        f2c6b190 e742c400 c01ed18c f2c6b248 f2c6b000 f88e5e62 f2c6b248 e742c400
[4295449.108000]        f7550380 e742c3f8 f88e5f03 f2c6b000 00000202 e742c400 e742c404 f88e52e7
[4295449.108000] Call Trace:
[4295449.108000]  [<c01ed151>] class_device_del+0x62/0x92
[4295449.108000]  [<c01ed18c>] class_device_unregister+0xb/0x16
[4295449.108000]  [<f88e5e62>] scsi_remove_device+0x32/0x77 [scsi_mod]
[4295449.108000]  [<f88e5f03>] __scsi_remove_target+0x5c/0x7f [scsi_mod]
[4295449.108000]  [<f88e52e7>] scsi_forget_host+0x28/0x3f [scsi_mod]
[4295449.108000]  [<f88def86>] scsi_remove_host+0xc/0x57 [scsi_mod]
[4295449.108000]  [<f91b027b>] storage_disconnect+0x50/0x6a [usb_storage]
[4295449.108000]  [<f891e09c>] usb_unbind_interface+0x36/0x65 [usbcore]
[4295449.108000]  [<c01ec374>] device_release_driver+0x49/0x55
[4295449.108000]  [<c01ec52d>] bus_remove_device+0x48/0x77
[4295449.108000]  [<c01eb918>] device_del+0x43/0x6f
[4295449.108000]  [<f89239cb>] usb_disable_device+0x77/0xe9 [usbcore]
[4295449.108000]  [<f891fb77>] usb_disconnect+0x93/0xec [usbcore]
[4295449.108000]  [<f89207c6>] hub_port_connect_change+0x57/0x2b2 [usbcore]
[4295449.108000]  [<f8920c43>] hub_events+0x222/0x2c6 [usbcore]
[4295449.108000]  [<f8920ce7>] hub_thread+0x0/0xe8 [usbcore]
[4295449.108000]  [<f8920d03>] hub_thread+0x1c/0xe8 [usbcore]
[4295449.108000]  [<c01247e2>] autoremove_wake_function+0x0/0x3a
[4295449.108000]  [<f8920ce7>] hub_thread+0x0/0xe8 [usbcore]
[4295449.108000]  [<c01247e2>] autoremove_wake_function+0x0/0x3a
[4295449.108000]  [<c0101245>] kernel_thread_helper+0x5/0xb
[4295449.108000] Code: 89 02 74 03 89 50 04 c7 41 04 00 02 20 00 89 5c 24 10 8b 46 08 89 44 24 0c 5b 5e e9 f7 a3 fe ff 5b 5e c3 55 57 56 53 8b 44 24 14 <8b> 58 48 8b 50 08 ff 4a 70 0f 88 b9 00 00 00 8b 53 0c 8d 6a fc
[4295449.108000]


```

anybody knows what is going on?

Thanks in advance

---

### Post by escobar5 on 2006-04-23
i guess no solution, man this sucks! :(

---

### Post by adamkane on 2006-04-24
Detail your hardware. Check google for any issues between Ubuntu and your motherboard.

---

