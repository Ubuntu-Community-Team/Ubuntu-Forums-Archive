---
title: "Edgy kernel oops w/USB external drive"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by allwin on 2007-01-30
Vintage 1999 Dell 550MHZ desktop with add in USB2.0/PCI card (ALi) and Ultra external hd usb 2.0/1394 enclosure containing WDC 80 gig IDE drive.  Drive is formatted with one NTFS partition in good shape.  Can anyone help me here?

When I connect this device, watching syslog, I can see it attempting to mount.  It gets so far as to see the disk label and so forth but there is a kernel oops before it mounts.  I'm unable to use this drive as a result.  Been fooling around with it quite a while.  Here's the log messages:  (I would post lsusb -v, however when I execute that command after this error the command produces no output...the terminal acts like the command is hung)

Jan 30 00:00:52 allwin kernel: [17180133.248000] usb 5-6: new high speed USB device using ehci_hcd and address 2
Jan 30 00:00:53 allwin kernel: [17180133.400000] usb 5-6: unable to read config index 0 descriptor/start
Jan 30 00:00:53 allwin kernel: [17180133.400000] usb 5-6: can't read configurations, error -71
Jan 30 00:00:53 allwin kernel: [17180133.516000] usb 5-6: new high speed USB device using ehci_hcd and address 3
Jan 30 00:00:53 allwin kernel: [17180133.784000] usb 5-6: configuration #1 chosen from 1 choice
Jan 30 00:00:53 allwin NetworkManager: <debug info>^I[1170133253.723327] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841'). 
Jan 30 00:00:53 allwin NetworkManager: <debug info>^I[1170133253.816113] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841_if0'). 
Jan 30 00:00:54 allwin kernel: [17180134.428000] usbcore: registered new driver libusual
Jan 30 00:00:54 allwin NetworkManager: <debug info>^I[1170133254.451090] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841_usbraw'). 
Jan 30 00:00:54 allwin kernel: [17180134.720000] SCSI subsystem initialized
Jan 30 00:00:54 allwin kernel: [17180134.736000] Initializing USB Mass Storage driver...
Jan 30 00:00:54 allwin kernel: [17180134.740000] scsi0 : SCSI emulation for USB Mass Storage devices
Jan 30 00:00:54 allwin kernel: [17180134.740000] usbcore: registered new driver usb-storage
Jan 30 00:00:54 allwin kernel: [17180134.740000] USB Mass Storage support registered.
Jan 30 00:00:54 allwin kernel: [17180134.740000] usb-storage: device found at 3
Jan 30 00:00:54 allwin kernel: [17180134.740000] usb-storage: waiting for device to settle before scanning
Jan 30 00:00:54 allwin NetworkManager: <debug info>^I[1170133254.541706] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841_if0_scsi_host'). 
Jan 30 00:00:59 allwin kernel: [17180139.740000] usb-storage: device scan complete
Jan 30 00:00:59 allwin kernel: [17180139.740000]   Vendor: WDC WD80  Model: 0BB-00JHC0        Rev: 05.0
Jan 30 00:00:59 allwin kernel: [17180139.740000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan 30 00:00:59 allwin NetworkManager: <debug info>^I[1170133259.455620] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841_if0_scsi_host_scsi_device_lun0'). 
Jan 30 00:00:59 allwin kernel: [17180139.884000] SCSI device sda: 156301487 512-byte hdwr sectors (80026 MB)
Jan 30 00:00:59 allwin kernel: [17180139.888000] sda: Write Protect is off
Jan 30 00:00:59 allwin kernel: [17180139.888000] sda: Mode Sense: 03 00 00 00
Jan 30 00:00:59 allwin kernel: [17180139.888000] sda: assuming drive cache: write through
Jan 30 00:00:59 allwin kernel: [17180139.892000] SCSI device sda: 156301487 512-byte hdwr sectors (80026 MB)
Jan 30 00:00:59 allwin kernel: [17180139.892000] sda: Write Protect is off
Jan 30 00:00:59 allwin kernel: [17180139.892000] sda: Mode Sense: 03 00 00 00
Jan 30 00:00:59 allwin kernel: [17180139.892000] sda: assuming drive cache: write through
Jan 30 00:00:59 allwin kernel: [17180139.896000]  sda: sda1
Jan 30 00:00:59 allwin kernel: [17180139.904000] sd 0:0:0:0: Attached scsi disk sda
Jan 30 00:00:59 allwin kernel: [17180139.968000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 30 00:00:59 allwin NetworkManager: <debug info>^I[1170133259.690466] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jan 30 00:00:59 allwin kernel: [17180140.260000] usb 5-6: reset high speed USB device using ehci_hcd and address 3
Jan 30 00:01:00 allwin kernel: [17180140.372000] usb 5-6: device descriptor read/64, error -71
Jan 30 00:01:16 allwin kernel: [17180156.844000] usb 5-6: reset high speed USB device using ehci_hcd and address 3
Jan 30 00:01:19 allwin kernel: [17180160.308000] usb 5-6: reset high speed USB device using ehci_hcd and address 3
Jan 30 00:01:20 allwin kernel: [17180160.864000] usb 5-6: reset high speed USB device using ehci_hcd and address 3
Jan 30 00:01:34 allwin kernel: [17180175.132000] usb 5-6: reset high speed USB device using ehci_hcd and address 3
Jan 30 00:01:34 allwin kernel: [17180175.280000] usb 5-6: device firmware changed
Jan 30 00:01:34 allwin kernel: [17180175.280000] usb 5-6: USB disconnect, address 3
Jan 30 00:01:34 allwin kernel: [17180175.280000] sd 0:0:0:0: SCSI error: return code = 0x70000
Jan 30 00:01:34 allwin kernel: [17180175.280000] end_request: I/O error, dev sda, sector 40
Jan 30 00:01:34 allwin kernel: [17180175.280000] Buffer I/O error on device sda, logical block 40
Jan 30 00:01:34 allwin kernel: [17180175.284000]  0:0:0:0: SCSI error: return code = 0x10000
Jan 30 00:01:34 allwin kernel: [17180175.284000] end_request: I/O error, dev sda, sector 41
Jan 30 00:01:34 allwin kernel: [17180175.284000] Buffer I/O error on device sda, logical block 41
Jan 30 00:01:34 allwin kernel: [17180175.284000]  0:0:0:0: rejecting I/O to dead device
Jan 30 00:01:34 allwin kernel: [17180175.284000] Buffer I/O error on device sda, logical block 42
Jan 30 00:01:34 allwin kernel: [17180175.284000] Buffer I/O error on device sda, logical block 43
Jan 30 00:01:34 allwin kernel: [17180175.284000] Buffer I/O error on device sda, logical block 44
Jan 30 00:01:34 allwin kernel: [17180175.284000] Buffer I/O error on device sda, logical block 45
Jan 30 00:01:34 allwin kernel: [17180175.284000] Buffer I/O error on device sda, logical block 46
Jan 30 00:01:34 allwin kernel: [17180175.284000] Buffer I/O error on device sda, logical block 47
Jan 30 00:01:34 allwin kernel: [17180175.284000] Buffer I/O error on device sda, logical block 48
Jan 30 00:01:34 allwin kernel: [17180175.284000] Buffer I/O error on device sda, logical block 49
Jan 30 00:01:34 allwin kernel: [17180175.292000]  0:0:0:0: rejecting I/O to dead device
Jan 30 00:01:34 allwin last message repeated 6 times
Jan 30 00:01:34 allwin NetworkManager: <debug info>^I[1170133294.967750] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jan 30 00:01:34 allwin NetworkManager: <debug info>^I[1170133294.982081] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841_if0_scsi_host_scsi_device_lun0'). 
Jan 30 00:01:34 allwin NetworkManager: <debug info>^I[1170133294.989875] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841_if0_scsi_host'). 
Jan 30 00:01:35 allwin NetworkManager: <debug info>^I[1170133295.002123] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841_usbraw'). 
Jan 30 00:01:35 allwin NetworkManager: <debug info>^I[1170133295.011167] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841_if0'). 
Jan 30 00:01:35 allwin NetworkManager: <debug info>^I[1170133295.022286] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841'). 
Jan 30 00:01:35 allwin kernel: [17180175.396000] usb 5-6: new high speed USB device using ehci_hcd and address 4
Jan 30 00:01:35 allwin kernel: [17180175.664000] usb 5-6: configuration #1 chosen from 1 choice
Jan 30 00:01:35 allwin kernel: [17180175.664000] scsi1 : SCSI emulation for USB Mass Storage devices
Jan 30 00:01:35 allwin kernel: [17180175.664000] usb-storage: device found at 4
Jan 30 00:01:35 allwin kernel: [17180175.664000] usb-storage: waiting for device to settle before scanning
Jan 30 00:01:35 allwin NetworkManager: <debug info>^I[1170133295.384255] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841'). 
Jan 30 00:01:35 allwin NetworkManager: <debug info>^I[1170133295.495771] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841_if0'). 
Jan 30 00:01:35 allwin NetworkManager: <debug info>^I[1170133295.728471] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841_if0_scsi_host'). 
Jan 30 00:01:35 allwin NetworkManager: <debug info>^I[1170133295.892387] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841_usbraw'). 
Jan 30 00:01:40 allwin kernel: [17180180.664000] usb-storage: device scan complete
Jan 30 00:01:40 allwin kernel: [17180180.664000]   Vendor: WDC WD80  Model: 0BB-00JHC0        Rev: 05.0
Jan 30 00:01:40 allwin kernel: [17180180.664000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan 30 00:01:40 allwin kernel: [17180180.668000] SCSI device sda: 156301487 512-byte hdwr sectors (80026 MB)
Jan 30 00:01:40 allwin kernel: [17180180.672000] sda: Write Protect is off
Jan 30 00:01:40 allwin kernel: [17180180.672000] sda: Mode Sense: 03 00 00 00
Jan 30 00:01:40 allwin kernel: [17180180.672000] sda: assuming drive cache: write through
Jan 30 00:01:40 allwin kernel: [17180180.676000] SCSI device sda: 156301487 512-byte hdwr sectors (80026 MB)
Jan 30 00:01:40 allwin kernel: [17180180.676000] sda: Write Protect is off
Jan 30 00:01:40 allwin kernel: [17180180.676000] sda: Mode Sense: 03 00 00 00
Jan 30 00:01:40 allwin kernel: [17180180.676000] sda: assuming drive cache: write through
Jan 30 00:01:43 allwin udevd-event[5347]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:10.3/usb5/5-6/5-6:1.0/host1/target1:0:0/1:0:0:0/bus' failed
Jan 30 00:01:46 allwin kernel: [17180180.676000]  sda:<6>usb 5-6: reset high speed USB device using ehci_hcd and address 4
Jan 30 00:01:47 allwin kernel: [17180187.636000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
Jan 30 00:01:47 allwin udevd-event[5347]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:10.3/usb5/5-6/5-6:1.0/host1/target1:0:0/1:0:0:0/ioerr_cnt' failed
Jan 30 00:01:47 allwin NetworkManager: <debug info>^I[1170133307.572160] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841_if0_scsi_host_scsi_device_lun0'). 
Jan 30 00:01:48 allwin kernel: [17180188.704000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
Jan 30 00:01:48 allwin kernel: [17180188.852000] usb 5-6: device descriptor read/all, error -71
Jan 30 00:01:48 allwin kernel: [17180188.968000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
Jan 30 00:01:52 allwin kernel: [17180192.616000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
Jan 30 00:01:52 allwin kernel: [17180192.764000] usb 5-6: device descriptor read/all, error -71
Jan 30 00:01:52 allwin kernel: [17180192.880000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
Jan 30 00:01:59 allwin kernel: [17180199.780000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
Jan 30 00:02:01 allwin kernel: [17180201.480000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
Jan 30 00:02:01 allwin kernel: [17180201.632000] sd 1:0:0:0: SCSI error: return code = 0x70000
Jan 30 00:02:01 allwin kernel: [17180201.632000] end_request: I/O error, dev sda, sector 0
Jan 30 00:02:01 allwin kernel: [17180201.632000] printk: 174 messages suppressed.
Jan 30 00:02:01 allwin kernel: [17180201.632000] Buffer I/O error on device sda, logical block 0
Jan 30 00:02:06 allwin kernel: [17180206.548000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
Jan 30 00:02:06 allwin kernel: [17180206.952000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
Jan 30 00:02:08 allwin kernel: [17180209.284000] usb 5-6: reset high speed USB device using ehci_hcd and address 4
Jan 30 00:02:09 allwin kernel: [17180209.436000] usb 5-6: device firmware changed
Jan 30 00:02:09 allwin kernel: [17180209.436000] usb 5-6: USB disconnect, address 4
Jan 30 00:02:09 allwin kernel: [17180209.436000] sd 1:0:0:0: SCSI error: return code = 0x70000
Jan 30 00:02:09 allwin kernel: [17180209.436000] end_request: I/O error, dev sda, sector 1
Jan 30 00:02:09 allwin kernel: [17180209.436000] Buffer I/O error on device sda, logical block 1
Jan 30 00:02:09 allwin kernel: [17180209.436000] sd 1:0:0:0: SCSI error: return code = 0x70000
Jan 30 00:02:09 allwin kernel: [17180209.436000] end_request: I/O error, dev sda, sector 2
Jan 30 00:02:09 allwin kernel: [17180209.436000] Buffer I/O error on device sda, logical block 2
Jan 30 00:02:09 allwin kernel: [17180209.440000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
Jan 30 00:02:09 allwin kernel: [17180209.440000]  printing eip:
Jan 30 00:02:09 allwin kernel: [17180209.440000] c0246907
Jan 30 00:02:09 allwin kernel: [17180209.440000] *pde = 00000000
Jan 30 00:02:09 allwin kernel: [17180209.440000] Oops: 0000 [#1]
Jan 30 00:02:09 allwin kernel: [17180209.440000] SMP 
Jan 30 00:02:09 allwin kernel: [17180209.440000] Modules linked in: sg sd_mod usb_storage scsi_mod libusual snd_rtctimer binfmt_misc rfcomm l2cap bluetooth radeon drm cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi sbs pcc_acpi i2c_ec hotkey dev_acpi container button battery asus_acpi ac ipv6 nls_utf8 nls_cp437 vfat fat snd_seq_dummy snd_seq_oss snd_seq_midi snd_seq_midi_event snd_seq lp af_packet tsdev serio_raw psmouse evdev pcspkr parport_pc parport floppy intel_agp tulip agpgart i2c_piix4 shpchp pci_hotplug snd_au8830 gameport snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc snd_ac97_bus snd_mpu401_uart snd_rawmidi snd_seq_device i2c_core snd soundcore 3c59x mii ide_floppy ext3 jbd uhci_hcd ehci_hcd ohci_hcd usbcore ide_generic ide_cd cdrom ide_disk piix generic thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Jan 30 00:02:09 allwin kernel: [17180209.440000] CPU:    0
Jan 30 00:02:09 allwin kernel: [17180209.440000] EIP:    0060:[make_class_name+55/176]    Not tainted VLI
Jan 30 00:02:09 allwin kernel: [17180209.440000] EFLAGS: 00010202   (2.6.17-10-generic #2) 
Jan 30 00:02:09 allwin kernel: [17180209.440000] EIP is at make_class_name+0x37/0xb0
Jan 30 00:02:09 allwin kernel: [17180209.440000] eax: 00000000   ebx: ffffffff   ecx: ffffffff   edx: 0000000b
Jan 30 00:02:09 allwin kernel: [17180209.440000] esi: c88d15d4   edi: 00000000   ebp: 00000000   esp: cf51be54
Jan 30 00:02:09 allwin kernel: [17180209.440000] ds: 007b   es: 007b   ss: 0068
Jan 30 00:02:09 allwin kernel: [17180209.440000] Process khubd (pid: 1665, threadinfo=cf51a000 task=c3ba8a90)
Jan 30 00:02:09 allwin kernel: [17180209.440000] Stack: c88d15d4 d1024858 c88d15d4 d1024858 c88d15dc c0246bae d10247e0 00000000 
Jan 30 00:02:09 allwin kernel: [17180209.440000]        00000000 c88d15d4 c33f5c00 00000246 cbdab214 c0246c88 c88d1400 d100bca0 
Jan 30 00:02:09 allwin kernel: [17180209.440000]        c88d1400 c33f5c00 d10093fb c33f5c30 c33f5c00 d1003a55 c33f5ec0 d0ef2ca0 
Jan 30 00:02:09 allwin kernel: [17180209.440000] Call Trace:
Jan 30 00:02:09 allwin kernel: [17180209.440000]  <c0246bae> class_device_del+0x9e/0x170  <c0246c88> class_device_unregister+0x8/0x10
Jan 30 00:02:09 allwin kernel: [17180209.440000]  <d100bca0> __scsi_remove_device+0x30/0x80 [scsi_mod]  <d10093fb> scsi_forget_host+0x4b/0x60 [scsi_mod]
Jan 30 00:02:09 allwin kernel: [17180209.440000]  <d1003a55> scsi_remove_host+0x55/0xe4 [scsi_mod]  <d0ee3d8e> storage_disconnect+0xe/0x20 [usb_storage]
Jan 30 00:02:09 allwin kernel: [17180209.440000]  <d08ab994> usb_unbind_interface+0x34/0x70 [usbcore]  <c0245e2b> __device_release_driver+0x5b/0xa0
Jan 30 00:02:09 allwin kernel: [17180209.440000]  <c02460ec> device_release_driver+0x1c/0x30  <c0245657> bus_remove_device+0x77/0x90
Jan 30 00:02:09 allwin kernel: [17180209.440000]  <c02446c5> device_del+0x35/0x70  <d08a9bc6> usb_disable_device+0x86/0xe0 [usbcore]
Jan 30 00:02:09 allwin kernel: [17180209.440000]  <d08a5927> usb_disconnect+0x97/0xf0 [usbcore]  <d08a698a> hub_thread+0x27a/0xc80 [usbcore]
Jan 30 00:02:09 allwin kernel: [17180209.440000]  <c0136180> autoremove_wake_function+0x0/0x50  <d08a6710> hub_thread+0x0/0xc80 [usbcore]
Jan 30 00:02:09 allwin kernel: [17180209.440000]  <c0135f8b> kthread+0xab/0xe0  <c0135ee0> kthread+0x0/0xe0
Jan 30 00:02:09 allwin NetworkManager: <debug info>^I[1170133329.255151] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_3507_BF61841_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jan 30 00:02:09 allwin kernel: [17180209.440000]  <c0101005> kernel_thread_helper+0x5/0x10 
Jan 30 00:02:09 allwin kernel: [17180209.440000] Code: 89 6c 24 10 31 ed 89 d9 89 74 24 08 89 7c 24 0c 89 04 24 8b 40 48 8b 38 89 e8 f2 ae f7 d1 49 8b 04 24 89 ca 89 d9 8b 78 08 89 e8 <f2> ae f7 d1 49 8d 44 0a 02 ba d0 00 00 00 e8 c6 07 f2 ff ba f4 
Jan 30 00:02:09 allwin kernel: [17180209.440000] EIP: [make_class_name+55/176] make_class_name+0x37/0xb0 SS:ESP 0068:cf51be54
Jan 30 00:02:09 allwin kernel: [17180209.440000]  <6>sd 1:0:0:0: SCSI error: return code = 0x10000
Jan 30 00:02:09 allwin kernel: [17180209.444000] end_request: I/O error, dev sda, sector 3
Jan 30 00:02:09 allwin kernel: [17180209.444000] Buffer I/O error on device sda, logical block 3
Jan 30 00:02:09 allwin kernel: [17180209.444000] sd 1:0:0:0: rejecting I/O to device being removed
Jan 30 00:02:09 allwin kernel: [17180209.444000] Buffer I/O error on device sda, logical block 4
Jan 30 00:02:09 allwin kernel: [17180209.444000] Buffer I/O error on device sda, logical block 5
Jan 30 00:02:09 allwin kernel: [17180209.444000] sd 1:0:0:0: rejecting I/O to device being removed
Jan 30 00:02:09 allwin kernel: [17180209.444000]  unable to read partition table
Jan 30 00:02:09 allwin kernel: [17180209.444000] sd 1:0:0:0: Attached scsi disk sda
Jan 30 00:02:09 allwin kernel: [17180209.444000] sd 1:0:0:0: Attached scsi generic sg0 type 0

---

### Post by Pridkett on 2007-02-09
I've been working around the same issue with an external enclosure I have (MadDog MegaValut 3.5in Dual Firewire/USB2.0).  I got the dual mode because I knew that there were some issues with both USB and Firewire drives in Linux, this way I hoped that at least one of the interfaces would work.  Unfortunately, the initio chipset for firewire has some issues with the sbp2 driver, but we're talking USB here, so lets see what we can find.

From what I can tell, this is a problem with the kernel's handling of USB, you've probably found that your drive works just fine on Windows or Mac, which isn't surprising, their drivers are just better.  As near as I can tell, it's a bug in the kernel somewhere.  It shows up on my Breezy mythtv box, my Edgy laptop, and also on the Feisty kernel on my laptop.  So it's been around for a while.  However, I think I've found two ways you can fix this.

First: just disable USB 2.0.  You can do this by running
```
rmmod echi_hcd
```

Second solution: disable USB 2.0, then reenable it by running:
```
rmmod ehci_hcd; modprobe echi_hcd
```

This latter honestly seems to have fixed the problem for me.  Strange, I know.

---

### Post by allwin on 2007-02-09
I found another factor leading to HD's in enclosures not connectiong via 1394 or USB 2.0.

Might be specific to Western Digital WD drives.  The settings of the jumpers (master/slave/cable connect) end up being important!  I didn't realize this.

On a WD drive, if you put the jumper on MASTER (as you would think), it really means MASTER + SLAVE.  This is WRONG.  You leave the jumper OFF.  Then it means MASTER ONLY.  Confusing as #$%^ I say, but once I jumpered it that way, it started connecting.

Doesn't make (the same) difference to Windows, just Linux.  In any case, I have two cans which do both USB and 1394, and I can connect them to two Ubuntu machines here...one way or another.

Oh, I picked up a $20 dual USB/1394 PCI card with a VIA chipset.  That worked much better on one system here.  On the other system, I never could get USB 2.0 to work (though I plan to try your suggestion), but firewire was cool.

Just my luck, I guess, to have a WD drive in the can, with its strange jumpering.  I also bought an ULTRA HD can, and it was on ULTRA's website that I found the thing about the WD drive peculiarity!

---

