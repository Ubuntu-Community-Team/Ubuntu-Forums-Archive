---
title: "pcmcia cf adaptor causes core dump / system hardlock"
date: 2006-07-29
forum: Hardware &amp; Laptops
---

### Post by stobor on 2006-07-29
Hope this is the right place for this topic.  Im fairly new to Ubuntu (1 month), but have been running Gentoo for the past 2 years and feel well at home in linux.

I am trying to use a pcmcia compact flash(cf) adaptor in my new laptop (a vaio sz240).  For the most part, it works well.  I can insert and remove the card as many times as I try and the proper entries in /dev/ get created, *provided the system didn't boot with the card present*.  If I start the system with the card inserted, It works fine until the card is removed.  Removing and reinserting causes (i think) a module to crash, and further pcmcia operations (namely removing the card) hardlock the system.

Is this a configuration problem on my end or a bug?  I was thinking its probably an issue with coldplug/hotplug, but it doesn't look like those are used anymore

I am running an up-to-date Dapper System with the 2.6.15-26-686 kernel provided in synaptic, although I have tried several other kernels (older 686, 386 kernels) with the same results.

Here is the output from /var/log/messages:
->System Booted with card present
->Remove Card
```

Jul 28 23:59:45 localhost kernel: [17179851.164000] pccard: card ejected from slot 0

```
->Reinsert Card
```

Jul 28 23:59:53 localhost kernel: [17179859.276000] pccard: PCMCIA card inserted into slot 0
Jul 28 23:59:53 localhost kernel: [17179859.276000] pcmcia: registering new device pcmcia0.0
Jul 28 23:59:54 localhost kernel: [17179859.592000] hdc: TOSHIBA THNCF256MMA, CFA DISK drive
Jul 28 23:59:54 localhost kernel: [17179860.264000] ide1 at 0x5100-0x5107,0x510e on irq 3
Jul 28 23:59:54 localhost kernel: [17179860.264000] hdc: max request size: 128KiB
Jul 28 23:59:54 localhost kernel: [17179860.264000] hdc: 500736 sectors (256 MB) w/2KiB Cache, CHS=978/16/32
Jul 28 23:59:54 localhost kernel: [17179860.264000] hdc: cache flushes not supported
Jul 28 23:59:54 localhost kernel: [17179860.264000]  hdc: hdc1
Jul 28 23:59:54 localhost kernel: [17179860.272000] c01bb9a2
Jul 28 23:59:54 localhost kernel: [17179860.272000] PREEMPT SMP 
Jul 28 23:59:54 localhost kernel: [17179860.272000] Modules linked in: binfmt_misc rfcomm l2cap bluetooth sonypi i915 drm ppdev speedstep_centrino cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec i2c_core ipv6 nls_utf8 ntfs dm_mod md_mod sr_mod sbp2 parport_pc lp parport ide_disk af_packet ide_cs pcmcia joydev tsdev yenta_socket rsrc_nonstatic pcmcia_core ipw3945 ieee80211 ieee80211_crypt ieee80211_1_1_13 ieee80211_1_1_13_crypt psmouse sky2 snd_hda_intel snd_hda_codec serio_raw snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc shpchp pci_hotplug intel_agp agpgart sg evdev ext3 jbd ide_generic usb_storage ohci1394 uhci_hcd ieee1394 ehci_hcd usbcore sd_mod ata_piix libata scsi_mod ide_cd cdrom piix generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
Jul 28 23:59:54 localhost kernel: [17179860.272000] CPU:    0
Jul 28 23:59:54 localhost kernel: [17179860.272000] EIP:    0060:[create_dir+34/464]    Not tainted VLI
Jul 28 23:59:54 localhost kernel: [17179860.272000] EFLAGS: 00010286   (2.6.15-26-686) 
Jul 28 23:59:54 localhost kernel: [17179860.272000] EIP is at create_dir+0x22/0x1d0
Jul 28 23:59:54 localhost kernel: [17179860.272000] eax: f7b5c598   ebx: f3ea2a54   ecx: c0325497   edx: 00000000
Jul 28 23:59:54 localhost kernel: [17179860.272000] esi: f3ea2a50   edi: f79f8750   ebp: f7aef93c   esp: f7aef900
Jul 28 23:59:54 localhost kernel: [17179860.272000] ds: 007b   es: 007b   ss: 0068
Jul 28 23:59:54 localhost kernel: [17179860.272000] Process pccardd (pid: 3482, threadinfo=f7aee000 task=f7a09560)
Jul 28 23:59:54 localhost kernel: [17179860.272000] Stack: c01b453b c1a17440 00000001 00000001 ffffffff f3ea2a57 f3ea2a50 f3ea2a50 
Jul 28 23:59:54 localhost kernel: [17179860.272000]        f79f8750 f79f86c0 c01bbbb6 f3ea2a50 f7b5c598 f3ea2a54 f7aef93c 00000000 
Jul 28 23:59:54 localhost kernel: [17179860.272000]        00000000 c01f810f f3ea2a50 f3ea2a50 fffffffe c01f83cd f3ea2a50 f3ea2a50 
Jul 28 23:59:54 localhost kernel: [17179860.272000] Call Trace:
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [read_dev_sector+155/208] read_dev_sector+0x9b/0xd0
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [sysfs_create_dir+54/128] sysfs_create_dir+0x36/0x80
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [create_dir+31/96] create_dir+0x1f/0x60
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [kobject_add+125/224] kobject_add+0x7d/0xe0
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [kobject_register+40/128] kobject_register+0x28/0x80
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [add_partition+207/288] add_partition+0xcf/0x120
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [rescan_partitions+282/368] rescan_partitions+0x11a/0x170
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [do_open+861/960] do_open+0x35d/0x3c0
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [blkdev_get+148/192] blkdev_get+0x94/0xc0
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [register_disk+193/224] register_disk+0xc1/0xe0
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [add_disk+73/96] add_disk+0x49/0x60
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [exact_match+0/16] exact_match+0x0/0x10
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [exact_lock+0/32] exact_lock+0x0/0x20
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [pg0+947967711/1069167616] ide_disk_probe+0x14f/0x18b [ide_disk]
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [driver_probe_device+84/240] driver_probe_device+0x54/0xf0
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [__device_attach+0/16] __device_attach+0x0/0x10
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [bus_for_each_drv+93/128] bus_for_each_drv+0x5d/0x80
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [device_attach+99/112] device_attach+0x63/0x70
Jul 28 23:59:54 localhost kernel: [17179860.272000]  [__device_attach+0/16] __device_attach+0x0/0x10
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [bus_add_device+53/208] bus_add_device+0x35/0xd0
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [device_pm_add+81/144] device_pm_add+0x51/0x90
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [device_add+295/416] device_add+0x127/0x1a0
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [probe_hwif_init_with_fixup+109/144] probe_hwif_init_with_fixup+0x6d/0x90
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [ide_register_hw_with_fixup+424/448] ide_register_hw_with_fixup+0x1a8/0x1c0
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [ide_undecoded_slave+0/192] ide_undecoded_slave+0x0/0xc0
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [pg0+945816073/1069167616] idecs_register+0x89/0x90 [ide_cs]
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [ide_undecoded_slave+0/192] ide_undecoded_slave+0x0/0xc0
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [pg0+945817099/1069167616] ide_config+0x3fb/0x650 [ide_cs]
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [pg0+947138257/1069167616] pccard_read_tuple+0x71/0xc0 [pcmcia_core]
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [pg0+945818028/1069167616] ide_event+0xdc/0xf0 [ide_cs]
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [pg0+948021222/1069167616] pcmcia_register_client+0x1d6/0x2a0 [pcmcia]
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [kzalloc+31/80] kzalloc+0x1f/0x50
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [pg0+945815699/1069167616] ide_attach+0x93/0xd0 [ide_cs]
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [kobject_get+23/32] kobject_get+0x17/0x20
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [pg0+948016299/1069167616] pcmcia_device_probe+0x8b/0x160 [pcmcia]
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [driver_probe_device+84/240] driver_probe_device+0x54/0xf0
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [__device_attach+0/16] __device_attach+0x0/0x10
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [bus_for_each_drv+93/128] bus_for_each_drv+0x5d/0x80
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [device_attach+99/112] device_attach+0x63/0x70
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [__device_attach+0/16] __device_attach+0x0/0x10
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [bus_add_device+53/208] bus_add_device+0x35/0xd0
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [device_pm_add+81/144] device_pm_add+0x51/0x90
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [device_add+295/416] device_add+0x127/0x1a0
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [pg0+948017513/1069167616] pcmcia_device_add+0x159/0x1e0 [pcmcia]
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [pg0+948017807/1069167616] pcmcia_card_add+0x9f/0xc0 [pcmcia]
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [vprintk+654/784] vprintk+0x28e/0x310
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [kobject_get+23/32] kobject_get+0x17/0x20
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [class_device_get+24/32] class_device_get+0x18/0x20
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [pg0+948020693/1069167616] ds_event+0x115/0x150 [pcmcia]
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [pg0+947124382/1069167616] send_event+0x8e/0xf0 [pcmcia_core]
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [pg0+947125539/1069167616] socket_insert+0xf3/0x1d0 [pcmcia_core]
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [pg0+947126444/1069167616] socket_detect_change+0x3c/0x90 [pcmcia_core]
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [pg0+947126977/1069167616] pccardd+0x1c1/0x210 [pcmcia_core]
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [ret_from_fork+6/20] ret_from_fork+0x6/0x14
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [default_wake_function+0/32] default_wake_function+0x0/0x20
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [pg0+947126528/1069167616] pccardd+0x0/0x210 [pcmcia_core]
Jul 28 23:59:55 localhost kernel: [17179860.272000]  [kernel_thread_helper+5/16] kernel_thread_helper+0x5/0x10
Jul 28 23:59:55 localhost kernel: [17179860.272000] Code: 00 00 8d bc 27 00 00 00 00 83 ec 28 8b 44 24 30 89 5c 24 18 8b 5c 24 34 89 6c 24 24 8b 6c 24 38 89 74 24 1c 89 7c 24 20 8b 50 10 <f0> ff 4a 78 0f 88 28 0e 00 00 31 c0 b9 ff ff ff ff 89 df f2 ae 

```
removing card after this causes the system to stop responding completely.

Thanks in advance for the help, let me know if i can provide any more info on the subject!

---

