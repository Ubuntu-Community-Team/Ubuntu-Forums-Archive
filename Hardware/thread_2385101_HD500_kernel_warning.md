---
title: "HD500 kernel warning"
date: 2018-02-16
forum: Hardware
---

### Post by hdaemon on 2018-02-16
Samse error on kernels 3.13,3.19,4.2.
```

[  313.760617] usb 2-1.3: new high-speed USB device number 4 using ehci-pci
[  315.294670] usb 2-1.3: new high-speed USB device number 5 using ehci-pci
[  315.380260] usb 2-1.3: config 1 interface 1 altsetting 0 bulk endpoint 0x1 has invalid maxpacket 64
[  315.380265] usb 2-1.3: config 1 interface 1 altsetting 0 bulk endpoint 0x81 has invalid maxpacket 64
[  315.380735] usb 2-1.3: New USB device found, idVendor=0e41, idProduct=414d
[  315.380740] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  315.380743] usb 2-1.3: Product: POD HD500
[  315.380745] usb 2-1.3: Manufacturer: Line 6
[  315.433729] snd_usb_podhd 2-1.3:1.0: Line 6 POD HD500 found
[  315.434174] ------------[ cut here ]------------
[  315.434182] WARNING: CPU: 0 PID: 2643 at /build/linux-lts-wily-Ejb_ce/linux-lts-wily-4.2.0/drivers/usb/core/urb.c:450 usb_submit_urb.part.6+0x15a/0x530()
[  315.434184] usb 2-1.3: BOGUS urb xfer, pipe 1 != type 3
[  315.434185] Modules linked in: snd_usb_podhd(+) snd_usb_line6 pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) joydev input_leds gpio_ich intel_rapl hid_logitech_hidpp x86_pkg_temp_thermal intel_powerclamp kvm_intel kvm crct10dif_pclmul crc32_pclmul i915 aesni_intel snd_ctxfi fglrx(POE) snd_hda_codec_hdmi aes_x86_64 lrw gf128mul glue_helper ppdev snd_seq_midi snd_seq_midi_event ablk_helper cryptd video snd_rawmidi snd_aloop snd_hda_intel snd_hda_codec drm_kms_helper snd_hda_core snd_seq drm it87 rfcomm dm_multipath hwmon_vid snd_hwdep coretemp serio_raw parport_pc snd_pcm bnep snd_seq_device amd_iommu_v2 scsi_dh lp tpm_infineon snd_timer i2c_algo_bit mei_me bluetooth parport snd mei mac_hid 8250_fintek shpchp soundcore lpc_ich btrfs hid_logitech_dj usbhid hid uas usb_storage raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq raid1 raid0 multipath linear ahci dm_mirror r8169 dm_region_hash libahci dm_log mii
[  315.434245] CPU: 0 PID: 2643 Comm: systemd-udevd Tainted: P           OE   4.2.0-42-lowlatency #49~14.04.1-Ubuntu
[  315.434247] Hardware name: DEPO Computers Z68P-DS3/Z68P-DS3, BIOS FE DE 03/27/2012
[  315.434249]  0000000000000000 ffff88081674f988 ffffffff817c7c1a ffff88081674f9d8
[  315.434252]  ffffffff81b2c230 ffff88081674f9c8 ffffffff8107a4fa ffff88080583e800
[  315.434255]  ffff880035688240 0000000000000002 0000000000000001 ffff88080583e800
[  315.434258] Call Trace:
[  315.434263]  [<ffffffff817c7c1a>] dump_stack+0x63/0x81
[  315.434268]  [<ffffffff8107a4fa>] warn_slowpath_common+0x8a/0xc0
[  315.434271]  [<ffffffff8107a576>] warn_slowpath_fmt+0x46/0x50
[  315.434274]  [<ffffffff815c04fa>] usb_submit_urb.part.6+0x15a/0x530
[  315.434278]  [<ffffffff815c0904>] usb_submit_urb+0x34/0x70
[  315.434282]  [<ffffffffc00116ce>] line6_start_listen+0x8e/0xc0 [snd_usb_line6]
[  315.434285]  [<ffffffffc0011fc1>] line6_probe+0x1f1/0x2e0 [snd_usb_line6]
[  315.434288]  [<ffffffffc017e040>] ? podhd_probe+0x40/0x40 [snd_usb_podhd]
[  315.434292]  [<ffffffffc017e032>] podhd_probe+0x32/0x40 [snd_usb_podhd]
[  315.434295]  [<ffffffff815c545d>] usb_probe_interface+0x10d/0x2e0
[  315.434298]  [<ffffffff8150384a>] driver_probe_device+0x23a/0x480
[  315.434301]  [<ffffffff81503b20>] __driver_attach+0x90/0xa0
[  315.434304]  [<ffffffff81503a90>] ? driver_probe_device+0x480/0x480
[  315.434306]  [<ffffffff815015fd>] bus_for_each_dev+0x5d/0x90
[  315.434308]  [<ffffffff8150316e>] driver_attach+0x1e/0x20
[  315.434311]  [<ffffffff81502cc0>] bus_add_driver+0x1d0/0x290
[  315.434313]  [<ffffffff815045c0>] driver_register+0x60/0xe0
[  315.434316]  [<ffffffff815c3df2>] usb_register_driver+0x82/0x150
[  315.434318]  [<ffffffffc003f000>] ? 0xffffffffc003f000
[  315.434321]  [<ffffffffc003f01e>] podhd_driver_init+0x1e/0x1000 [snd_usb_podhd]
[  315.434325]  [<ffffffff8100213d>] do_one_initcall+0xcd/0x1f0
[  315.434328]  [<ffffffff811b9d8e>] ? __vunmap+0xae/0xf0
[  315.434331]  [<ffffffff811d3bbc>] ? kfree+0x14c/0x180
[  315.434343]  [<ffffffff817c1dee>] do_init_module+0x61/0x1ea
[  315.434347]  [<ffffffff81100867>] load_module+0x13f7/0x1b50
[  315.434350]  [<ffffffff810fcf20>] ? __symbol_put+0x50/0x50
[  315.434354]  [<ffffffff811011a0>] SyS_finit_module+0x80/0xb0
[  315.434357]  [<ffffffff817cf172>] entry_SYSCALL_64_fastpath+0x16/0x75
[  315.434359] ---[ end trace f24643f8286eb62f ]---
[  315.434885] snd_usb_podhd 2-1.3:1.0: Line 6 POD HD500 now attached
[  315.434901] snd_usb_podhd 2-1.3:1.1: Line 6 POD HD500 found
[  315.434904] usb 2-1.3: selecting invalid altsetting 1
[  315.434906] snd_usb_podhd 2-1.3:1.1: set_interface failed
[  315.434916] snd_usb_podhd: probe of 2-1.3:1.1 failed with error -22
[  315.434934] usbcore: registered new interface driver snd_usb_podhd
[  316.839017] ------------[ cut here ]------------
[  316.839029] WARNING: CPU: 2 PID: 78 at /build/linux-lts-wily-Ejb_ce/linux-lts-wily-4.2.0/drivers/usb/core/urb.c:450 usb_submit_urb.part.6+0x15a/0x530()
[  316.839032] usb 2-1.3: BOGUS urb xfer, pipe 1 != type 3
[  316.839034] Modules linked in: snd_usb_podhd snd_usb_line6 pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) joydev input_leds gpio_ich intel_rapl hid_logitech_hidpp x86_pkg_temp_thermal intel_powerclamp kvm_intel kvm crct10dif_pclmul crc32_pclmul i915 aesni_intel snd_ctxfi fglrx(POE) snd_hda_codec_hdmi aes_x86_64 lrw gf128mul glue_helper ppdev snd_seq_midi snd_seq_midi_event ablk_helper cryptd video snd_rawmidi snd_aloop snd_hda_intel snd_hda_codec drm_kms_helper snd_hda_core snd_seq drm it87 rfcomm dm_multipath hwmon_vid snd_hwdep coretemp serio_raw parport_pc snd_pcm bnep snd_seq_device amd_iommu_v2 scsi_dh lp tpm_infineon snd_timer i2c_algo_bit mei_me bluetooth parport snd mei mac_hid 8250_fintek shpchp soundcore lpc_ich btrfs hid_logitech_dj usbhid hid uas usb_storage raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq raid1 raid0 multipath linear ahci dm_mirror r8169 dm_region_hash libahci dm_log mii
[  316.839109] CPU: 2 PID: 78 Comm: irq/23-ehci_hcd Tainted: P        W  OE   4.2.0-42-lowlatency #49~14.04.1-Ubuntu
[  316.839111] Hardware name: DEPO Computers Z68P-DS3/Z68P-DS3, BIOS FE DE 03/27/2012
[  316.839113]  0000000000000000 ffff88083fa83d48 ffffffff817c7c1a ffff88083fa83d98
[  316.839117]  ffffffff81b2c230 ffff88083fa83d88 ffffffff8107a4fa ffff88083fa83da8
[  316.839120]  ffff880035688240 0000000000000002 0000000000000001 ffff88080583e800
[  316.839124] Call Trace:
[  316.839126]  <IRQ>  [<ffffffff817c7c1a>] dump_stack+0x63/0x81
[  316.839136]  [<ffffffff8107a4fa>] warn_slowpath_common+0x8a/0xc0
[  316.839140]  [<ffffffff8107a576>] warn_slowpath_fmt+0x46/0x50
[  316.839144]  [<ffffffff815c04fa>] usb_submit_urb.part.6+0x15a/0x530
[  316.839149]  [<ffffffff810d32e0>] ? irq_thread_fn+0x50/0x50
[  316.839153]  [<ffffffff815c0904>] usb_submit_urb+0x34/0x70
[  316.839159]  [<ffffffffc00116ce>] line6_start_listen+0x8e/0xc0 [snd_usb_line6]
[  316.839163]  [<ffffffffc00121a9>] line6_data_received+0xb9/0xd0 [snd_usb_line6]
[  316.839167]  [<ffffffff815bd3e5>] __usb_hcd_giveback_urb+0x85/0x110
[  316.839170]  [<ffffffff815bd4f5>] usb_giveback_urb_bh+0x85/0xc0
[  316.839174]  [<ffffffff8107e543>] tasklet_hi_action+0x123/0x130
[  316.839176]  [<ffffffff8107e81d>] __do_softirq+0xdd/0x2c0
[  316.839180]  [<ffffffff810d32e0>] ? irq_thread_fn+0x50/0x50
[  316.839185]  [<ffffffff817d0cbc>] do_softirq_own_stack+0x1c/0x30
[  316.839186]  <EOI>  [<ffffffff8107ea9f>] do_softirq+0x4f/0x60
[  316.839190]  [<ffffffff8107eb47>] __local_bh_enable_ip+0x97/0xa0
[  316.839194]  [<ffffffff810d3337>] irq_forced_thread_fn+0x57/0x70
[  316.839197]  [<ffffffff810d380b>] irq_thread+0x10b/0x130
[  316.839201]  [<ffffffff810d3380>] ? wake_threads_waitq+0x30/0x30
[  316.839204]  [<ffffffff810d3700>] ? irq_thread_check_affinity+0x90/0x90
[  316.839208]  [<ffffffff81098ae9>] kthread+0xc9/0xe0
[  316.839212]  [<ffffffff81098a20>] ? kthread_create_on_node+0x1c0/0x1c0
[  316.839215]  [<ffffffff817cf59f>] ret_from_fork+0x3f/0x70
[  316.839218]  [<ffffffff81098a20>] ? kthread_create_on_node+0x1c0/0x1c0
[  316.839221] ---[ end trace f24643f8286eb630 ]---
[  316.864356] ------------[ cut here ]------------
[  316.864365] WARNING: CPU: 2 PID: 78 at /build/linux-lts-wily-Ejb_ce/linux-lts-wily-4.2.0/drivers/usb/core/urb.c:450 usb_submit_urb.part.6+0x15a/0x530()
[  316.864368] usb 2-1.3: BOGUS urb xfer, pipe 1 != type 3
[  316.864370] Modules linked in: snd_usb_podhd snd_usb_line6 pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) joydev input_leds gpio_ich intel_rapl hid_logitech_hidpp x86_pkg_temp_thermal intel_powerclamp kvm_intel kvm crct10dif_pclmul crc32_pclmul i915 aesni_intel snd_ctxfi fglrx(POE) snd_hda_codec_hdmi aes_x86_64 lrw gf128mul glue_helper ppdev snd_seq_midi snd_seq_midi_event ablk_helper cryptd video snd_rawmidi snd_aloop snd_hda_intel snd_hda_codec drm_kms_helper snd_hda_core snd_seq drm it87 rfcomm dm_multipath hwmon_vid snd_hwdep coretemp serio_raw parport_pc snd_pcm bnep snd_seq_device amd_iommu_v2 scsi_dh lp tpm_infineon snd_timer i2c_algo_bit mei_me bluetooth parport snd mei mac_hid 8250_fintek shpchp soundcore lpc_ich btrfs hid_logitech_dj usbhid hid uas usb_storage raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq raid1 raid0 multipath linear ahci dm_mirror r8169 dm_region_hash libahci dm_log mii
[  316.864434] CPU: 2 PID: 78 Comm: irq/23-ehci_hcd Tainted: P        W  OE   4.2.0-42-lowlatency #49~14.04.1-Ubuntu
[  316.864436] Hardware name: DEPO Computers Z68P-DS3/Z68P-DS3, BIOS FE DE 03/27/2012
[  316.864438]  0000000000000000 ffff88083fa83d48 ffffffff817c7c1a ffff88083fa83d98
[  316.864442]  ffffffff81b2c230 ffff88083fa83d88 ffffffff8107a4fa ffff88083fa83da8
[  316.864445]  ffff880035688240 0000000000000002 0000000000000001 ffff88080583e800
[  316.864448] Call Trace:
[  316.864450]  <IRQ>  [<ffffffff817c7c1a>] dump_stack+0x63/0x81
[  316.864457]  [<ffffffff8107a4fa>] warn_slowpath_common+0x8a/0xc0
[  316.864461]  [<ffffffff8107a576>] warn_slowpath_fmt+0x46/0x50
[  316.864466]  [<ffffffff810a3610>] ? ttwu_do_wakeup+0x40/0x110
[  316.864470]  [<ffffffff815c04fa>] usb_submit_urb.part.6+0x15a/0x530
[  316.864474]  [<ffffffff810d32e0>] ? irq_thread_fn+0x50/0x50
[  316.864477]  [<ffffffff815c0904>] usb_submit_urb+0x34/0x70
[  316.864482]  [<ffffffffc00116ce>] line6_start_listen+0x8e/0xc0 [snd_usb_line6]
[  316.864486]  [<ffffffffc00121a9>] line6_data_received+0xb9/0xd0 [snd_usb_line6]
[  316.864490]  [<ffffffff815bd3e5>] __usb_hcd_giveback_urb+0x85/0x110
[  316.864494]  [<ffffffff815bd4f5>] usb_giveback_urb_bh+0x85/0xc0
[  316.864496]  [<ffffffff8107e543>] tasklet_hi_action+0x123/0x130
[  316.864499]  [<ffffffff8107e81d>] __do_softirq+0xdd/0x2c0
[  316.864503]  [<ffffffff810d32e0>] ? irq_thread_fn+0x50/0x50
[  316.864506]  [<ffffffff817d0cbc>] do_softirq_own_stack+0x1c/0x30
[  316.864508]  <EOI>  [<ffffffff8107ea9f>] do_softirq+0x4f/0x60
[  316.864512]  [<ffffffff8107eb47>] __local_bh_enable_ip+0x97/0xa0
[  316.864515]  [<ffffffff810d3337>] irq_forced_thread_fn+0x57/0x70
[  316.864519]  [<ffffffff810d380b>] irq_thread+0x10b/0x130
[  316.864522]  [<ffffffff810d3380>] ? wake_threads_waitq+0x30/0x30
[  316.864526]  [<ffffffff810d3700>] ? irq_thread_check_affinity+0x90/0x90
[  316.864529]  [<ffffffff81098ae9>] kthread+0xc9/0xe0
[  316.864532]  [<ffffffff81098a20>] ? kthread_create_on_node+0x1c0/0x1c0
[  316.864535]  [<ffffffff817cf59f>] ret_from_fork+0x3f/0x70
[  316.864538]  [<ffffffff81098a20>] ? kthread_create_on_node+0x1c0/0x1c0
[  316.864541] ---[ end trace f24643f8286eb631 ]---
```

---

### Post by Yellow Pasque on 2018-02-16
It was fixed in kernel 4.15 - [https://github.com/torvalds/linux/commit/2a4340c57717162c6bf07a0860d05711d4de994b#diff-45dd6aa95de85e30222cad9b070fd423](https://github.com/torvalds/linux/commit/2a4340c57717162c6bf07a0860d05711d4de994b#diff-45dd6aa95de85e30222cad9b070fd423)

---

### Post by hdaemon on 2018-02-16
[FONT=arial][SIZE=3]Thnx a lot [/SIZE][COLOR=#DD4814][COLOR=#000000][SIZE=3][Temüjin]("https://ubuntuforums.org/member.php?u=327594")[/SIZE]. [/COLOR][/COLOR][/FONT][SIZE=4]Offtopic question: fglrx driver for my HD7970 still avaliable for that kernel?[/SIZE]

---

### Post by Yellow Pasque on 2018-02-16
This wiki page claims fglrx will not work with kernel > 3.19 
[http://wiki.cchtml.com/index.php?title=Crimson_15.12](http://wiki.cchtml.com/index.php?title=Crimson_15.12)

---

### Post by hdaemon on 2018-09-02
Update to Ubuntu 18.04 
with kernel [FONT=monospace][COLOR=#000000]Linux GSLM 4.15.0-33-generic

still no luck with LINE POD HD500

[/COLOR][/FONT][FONT=monospace][COLOR=#B26818]usb 1-5[/COLOR][COLOR=#000000]: new high-speed USB device number 6 using xhci_hcd[/COLOR]
[COLOR=#18B218][   44.208541] [/COLOR][COLOR=#B26818]usb 1-5[/COLOR][COLOR=#000000]**: config 1 interface 1 altsetting 0 bulk endpoint 0x1 has invalid maxpacket 64**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][   44.208548] [/COLOR][COLOR=#B26818]usb 1-5[/COLOR][COLOR=#000000]**: config 1 interface 1 altsetting 0 bulk endpoint 0x81 has invalid maxpacket 64**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][   44.209063] [/COLOR][COLOR=#B26818]usb 1-5[/COLOR][COLOR=#000000]: New USB device found, idVendor=0e41, idProduct=414d[/COLOR]
[COLOR=#18B218][   44.209068] [/COLOR][COLOR=#B26818]usb 1-5[/COLOR][COLOR=#000000]: New USB device strings: Mfr=1, Product=2, SerialNumber=0[/COLOR]
[COLOR=#18B218][   44.209072] [/COLOR][COLOR=#B26818]usb 1-5[/COLOR][COLOR=#000000]: Product: POD HD500[/COLOR]
[COLOR=#18B218][   44.209076] [/COLOR][COLOR=#B26818]usb 1-5[/COLOR][COLOR=#000000]: Manufacturer: Line 6[/COLOR]
[COLOR=#18B218][   44.209992] [/COLOR][COLOR=#B26818]snd_usb_podhd 1-5:1.0[/COLOR][COLOR=#000000]: Line 6 POD HD500 found[/COLOR]
[COLOR=#18B218][   44.210969] [/COLOR][COLOR=#B26818]snd_usb_podhd 1-5:1.0[/COLOR][COLOR=#000000]: Line 6 POD HD500 now attached[/COLOR]
[COLOR=#18B218][   44.211283] [/COLOR][COLOR=#B26818]snd_usb_podhd 1-5:1.1[/COLOR][COLOR=#000000]: Line 6 POD HD500 found[/COLOR]
[COLOR=#18B218][   44.211289] [/COLOR][COLOR=#B26818]usb 1-5[/COLOR][COLOR=#000000]**: selecting invalid altsetting 1**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][   44.211292] [/COLOR][COLOR=#B26818]snd_usb_podhd 1-5:1.1[/COLOR][COLOR=#B21818]: set_interface failed[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][   44.211304] [/COLOR][COLOR=#B26818]snd_usb_podhd 1-5:1.1[/COLOR][COLOR=#000000]: Line 6 POD HD500 now disconnected[/COLOR][COLOR=#B21818]                                                                                                                                                                                                                      [/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#18B218][   44.211317] [/COLOR][COLOR=#B26818]snd_usb_podhd[/COLOR][COLOR=#000000]**: probe of 1-5:1.1 failed with error -22**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][   69.605987] [/COLOR][COLOR=#B26818]nvidia-modeset[/COLOR][COLOR=#000000]: Allocated GPU:0 (GPU-a23356f9-937a-4843-a3cc-da12769e0681) @ PCI:0000:01:00.0[/COLOR]
[COLOR=#18B218][   69.606386] [/COLOR][COLOR=#B26818]nvidia-modeset[/COLOR][COLOR=#000000]: Freed GPU:0 (GPU-a23356f9-937a-4843-a3cc-da12769e0681) @ PCI:0000:01:00.0[/COLOR]
[COLOR=#18B218][  153.206595] [/COLOR][COLOR=#B26818]usb 1-5[/COLOR][COLOR=#000000]: USB disconnect, device number 6[/COLOR]
[COLOR=#18B218][  153.207101] [/COLOR][COLOR=#B26818]snd_usb_podhd 1-5:1.0[/COLOR][COLOR=#000000]: Line 6 POD HD500 now disconnected[/COLOR]
[COLOR=#18B218][  165.694350] [/COLOR][COLOR=#B26818]usb 1-1[/COLOR][COLOR=#000000]: new high-speed USB device number 7 using xhci_hcd[/COLOR]
[COLOR=#18B218][  165.842687] [/COLOR][COLOR=#B26818]usb 1-1[/COLOR][COLOR=#000000]**: config 1 interface 1 altsetting 0 bulk endpoint 0x1 has invalid maxpacket 64**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][  165.842693] [/COLOR][COLOR=#B26818]usb 1-1[/COLOR][COLOR=#000000]**: config 1 interface 1 altsetting 0 bulk endpoint 0x81 has invalid maxpacket 64**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][  165.843146] [/COLOR][COLOR=#B26818]usb 1-1[/COLOR][COLOR=#000000]: New USB device found, idVendor=0e41, idProduct=414d[/COLOR]
[COLOR=#18B218][  165.843147] [/COLOR][COLOR=#B26818]usb 1-1[/COLOR][COLOR=#000000]: New USB device strings: Mfr=1, Product=2, SerialNumber=0[/COLOR]
[COLOR=#18B218][  165.843149] [/COLOR][COLOR=#B26818]usb 1-1[/COLOR][COLOR=#000000]: Product: POD HD500[/COLOR]
[COLOR=#18B218][  165.843150] [/COLOR][COLOR=#B26818]usb 1-1[/COLOR][COLOR=#000000]: Manufacturer: Line 6[/COLOR]
[COLOR=#18B218][  165.843800] [/COLOR][COLOR=#B26818]snd_usb_podhd 1-1:1.0[/COLOR][COLOR=#000000]: Line 6 POD HD500 found[/COLOR]
[COLOR=#18B218][  165.844514] [/COLOR][COLOR=#B26818]snd_usb_podhd 1-1:1.0[/COLOR][COLOR=#000000]: Line 6 POD HD500 now attached[/COLOR]
[COLOR=#18B218][  165.844740] [/COLOR][COLOR=#B26818]snd_usb_podhd 1-1:1.1[/COLOR][COLOR=#000000]: Line 6 POD HD500 found[/COLOR]
[COLOR=#18B218][  165.844742] [/COLOR][COLOR=#B26818]usb 1-1[/COLOR][COLOR=#000000]**: selecting invalid altsetting 1**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][  165.844743] [/COLOR][COLOR=#B26818]snd_usb_podhd 1-1:1.1[/COLOR][COLOR=#B21818]: set_interface failed[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#18B218][  165.844747] [/COLOR][COLOR=#B26818]snd_usb_podhd 1-1:1.1[/COLOR][COLOR=#000000]: Line 6 POD HD500 now disconnected[/COLOR][COLOR=#B21818]                                                                                                                                                                                                                      [/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#18B218][  165.844752] [/COLOR][COLOR=#B26818]snd_usb_podhd[/COLOR][COLOR=#000000]**: probe of 1-1:1.1 failed with error -22**[/COLOR]
[COLOR=#000000][/COLOR]
[/FONT][FONT=monospace]
[/FONT]

---

