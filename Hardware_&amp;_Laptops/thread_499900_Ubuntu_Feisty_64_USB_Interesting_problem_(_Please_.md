---
title: "Ubuntu Feisty 64 USB Interesting problem :( Please help!"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by freekaleek on 2007-07-13
Hey yall! Thanks for the read, I thought ide come and ask you bunch of brain box's because you usually are able to sort every problem i have faced on the way to ubuntu sucess :lolflag:

Right, here goes!

My usb thumbdrive takes about 5 hours to mount, its usb 2.0 and 1gb. It works fine with xp, and my install is fully up to date!  I don't get it because i either wait all that time, or i reboot with it plugged in but if i do that:

Either

1. It hangs after grub, on a black screen.
2. It doesnt mount.
3. It works fine, untill i unplug it and replug, and once again teh waiting game.

I have mount removable media when hot-pluged and inserted enabled, nothing else with regards to the thumbdrive.

Any help at getting it to fipping mount would be greatly appriciated, as my psp mounts within seconds, and i think my external hard drive might face the same problem!

Thanks a lot you guys

Edit

The even more confusing thing, that i left out is the fact that the lights on the drive are flashing, showing access?! Ive tried unticking the boxes, and trying to mount it manually, but it claims to be no media on the drive?!

Edit

Regards

Jack (Freekaleek)

---

### Post by kalekseishaken on 2007-07-13
When I first tried Feisty, I tried the 64b version, and it did not like the one drive I had formatted as NTFS (It was a 4GB that I had the block size set to 512B).

These days I make sure that all thumb drives are formated FAT32.

Ciao . . . C.Joseph

---

### Post by freekaleek on 2007-07-14
Yeah, i did format it to fat32 and still, the same problem, thanks anyway!

Anyone else? Know anything?

---

### Post by IntuitiveNipple on 2007-07-14
Have you checked the reports in the log files (kern.log, messages.log, etc?) You'll likely find some strong clues there as to what the problem is.

---

### Post by freekaleek on 2007-07-15
Thanks, I got this? :s

```
Jul 15 17:34:02 freekaleek-laptop kernel: [10234.446471] usb 1-1: new high speed USB device using ehci_hcd and address 7
Jul 15 17:34:02 freekaleek-laptop kernel: [10234.507204] usb 1-1: configuration #1 chosen from 1 choice
Jul 15 17:34:02 freekaleek-laptop kernel: [10234.509009] scsi1 : SCSI emulation for USB Mass Storage devices
Jul 15 17:34:02 freekaleek-laptop kernel: [10234.509155] usb-storage: device found at 7
Jul 15 17:34:02 freekaleek-laptop kernel: [10234.509157] usb-storage: waiting for device to settle before scanning
Jul 15 17:34:07 freekaleek-laptop kernel: [10237.416961] usb-storage: device scan complete
Jul 15 17:34:07 freekaleek-laptop kernel: [10237.418372] scsi 1:0:0:0: Direct-Access              Removable Disk   PMAP PQ: 0 ANSI: 0 CCS
Jul 15 17:34:07 freekaleek-laptop kernel: [10237.418831] scsi 1:0:0:1: Direct-Access              Removable Disk   PMAP PQ: 0 ANSI: 0 CCS
Jul 15 17:34:08 freekaleek-laptop kernel: [10237.627997] SCSI device sda: 2006016 512-byte hdwr sectors (1027 MB)
Jul 15 17:34:08 freekaleek-laptop kernel: [10237.628323] sda: Write Protect is off
Jul 15 17:34:08 freekaleek-laptop kernel: [10237.628326] sda: Mode Sense: 23 00 00 00
Jul 15 17:34:08 freekaleek-laptop kernel: [10237.628329] sda: assuming drive cache: write through
Jul 15 17:34:08 freekaleek-laptop kernel: [10237.630102] SCSI device sda: 2006016 512-byte hdwr sectors (1027 MB)
Jul 15 17:34:08 freekaleek-laptop kernel: [10237.631408] sda: Write Protect is off
Jul 15 17:34:08 freekaleek-laptop kernel: [10237.631413] sda: Mode Sense: 23 00 00 00
Jul 15 17:34:08 freekaleek-laptop kernel: [10237.631415] sda: assuming drive cache: write through
Jul 15 17:34:38 freekaleek-laptop kernel: [10237.631419]  sda:<6>usb 1-1: reset high speed USB device using ehci_hcd and address 7
Jul 15 17:34:41 freekaleek-laptop kernel: [10252.385216] usb 1-1: device descriptor read/64, error -110
Jul 15 17:34:56 freekaleek-laptop kernel: [10260.130842] usb 1-1: device descriptor read/64, error -110
Jul 15 17:34:56 freekaleek-laptop kernel: [10260.322662] usb 1-1: reset high speed USB device using ehci_hcd and address 7
Jul 15 17:34:59 freekaleek-laptop kernel: [10261.857475] usb 1-1: device descriptor read/64, error -110
Jul 15 17:35:15 freekaleek-laptop kernel: [10268.615078] usb 1-1: device descriptor read/64, error -110
Jul 15 17:35:15 freekaleek-laptop kernel: [10268.710998] usb 1-1: reset high speed USB device using ehci_hcd and address 7
Jul 15 17:35:25 freekaleek-laptop kernel: [10274.021159] usb 1-1: device not accepting address 7, error -110
Jul 15 17:35:25 freekaleek-laptop kernel: [10274.070900] usb 1-1: reset high speed USB device using ehci_hcd and address 7
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693169] usb 1-1: device not accepting address 7, error -110
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693198] usb 1-1: USB disconnect, address 7
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693297] Unable to handle kernel NULL pointer dereference at 0000000000000000 RIP: 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693300]  [strlen+2/32] strlen+0x2/0x20
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693308] PGD 6519067 PUD 6518067 PMD 0 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693311] Oops: 0000 [1] SMP 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693314] CPU 0 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693315] Modules linked in: sg sd_mod usb_storage libusual binfmt_misc rfcomm l2cap bluetooth vboxdrv ipv6 ppdev powernow_k8 cpufreq_userspace cpufreq_ondemand cpufreq_powersave cpufreq_conservative cpufreq_stats freq_table pcc_acpi tc1100_wmi sony_acpi dev_acpi button video ac container dock sbs i2c_ec asus_acpi backlight battery af_packet eeprom fglrx(P) ndiswrapper parport_pc lp parport fuse joydev snd_atiixp_modem snd_seq_dummy snd_seq_oss snd_atiixp snd_ac97_codec snd_seq_midi snd_rawmidi snd_seq_midi_event ac97_bus snd_pcm_oss snd_mixer_oss snd_seq serio_raw snd_pcm snd_timer snd_seq_device psmouse pcspkr k8temp snd soundcore snd_page_alloc i2c_piix4 i2c_core shpchp pci_hotplug tsdev evdev ext3 jbd mbcache 8139too ide_cd cdrom ide_disk ata_generic libata scsi_mod atiixp 8139cp mii ohci_hcd generic ehci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb cfbcopyarea cfbimgblt cfbfillrect capability commoncap
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693366] Pid: 1968, comm: khubd Tainted: P      2.6.20-16-generic #2
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693370] RIP: 0010:[strlen+2/32]  [strlen+2/32] strlen+0x2/0x20
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693376] RSP: 0018:ffff81003583dc18  EFLAGS: 00010246
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693379] RAX: 0000000000000000 RBX: ffffffff880b9700 RCX: 0000000000000002
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693383] RDX: ffffffff885e8940 RSI: ffff81000864a388 RDI: 0000000000000000
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693386] RBP: ffffffff880a45f4 R08: 0000000000000000 R09: 0000000000000000
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693390] R10: 0000000000000001 R11: ffffffff802306c0 R12: ffff81000864a388
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693394] R13: ffffffff880b9710 R14: ffffffff880b9620 R15: 0000000000000000
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693399] FS:  0000000041802940(0000) GS:ffffffff8054e000(0000) knlGS:00000000f75d7b10
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693402] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693405] CR2: 0000000000000000 CR3: 000000000541c000 CR4: 00000000000006e0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693409] Process khubd (pid: 1968, threadinfo ffff81003583c000, task ffff81003601d100)
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693411] Stack:  ffffffff803a73a0 ffffffff880b9700 ffff81000864a378 ffff81000864a388
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693419]  ffffffff803a7691 0000000000000282 ffff81000864a378 ffff81000864a0e8
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693424]  0000000000000246 ffffffff885dc1c0 00000000ffffffed ffff810037de3498
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693429] Call Trace:
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693434]  [make_class_name+32/144] make_class_name+0x20/0x90
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693443]  [class_device_del+193/368] class_device_del+0xc1/0x170
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693453]  [class_device_unregister+9/32] class_device_unregister+0x9/0x20
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693474]  [_end+128346306/2130485360] :scsi_mod:__scsi_remove_device+0x32/0xa0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693492]  [_end+128334525/2130485360] :scsi_mod:scsi_forget_host+0x4d/0x80
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693508]  [_end+128310245/2130485360] :scsi_mod:scsi_remove_host+0x75/0x100
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693519]  [_end+133787344/2130485360] :usb_storage:storage_disconnect+0x10/0x20
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693538]  [_end+128001341/2130485360] :usbcore:usb_unbind_interface+0x6d/0xd0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693548]  [__device_release_driver+145/192] __device_release_driver+0x91/0xc0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693554]  [device_release_driver+56/96] device_release_driver+0x38/0x60
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693561]  [bus_remove_device+137/176] bus_remove_device+0x89/0xb0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693567]  [device_del+418/544] device_del+0x1a2/0x220
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693586]  [_end+127989666/2130485360] :usbcore:usb_disable_device+0x82/0x100
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693603]  [_end+127973323/2130485360] :usbcore:usb_disconnect+0xab/0x150
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693623]  [_end+127977434/2130485360] :usbcore:hub_thread+0x43a/0xcd0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693632]  [thread_return+0/245] thread_return+0x0/0xf5
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693644]  [autoremove_wake_function+0/48] autoremove_wake_function+0x0/0x30
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693665]  [_end+127976352/2130485360] :usbcore:hub_thread+0x0/0xcd0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693669]  [keventd_create_kthread+0/144] keventd_create_kthread+0x0/0x90
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693677]  [kthread+217/288] kthread+0xd9/0x120
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693687]  [child_rip+10/18] child_rip+0xa/0x12
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693692]  [keventd_create_kthread+0/144] keventd_create_kthread+0x0/0x90
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693706]  [kthread+0/288] kthread+0x0/0x120
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693711]  [child_rip+0/18] child_rip+0x0/0x12
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693716] 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693717] 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693718] Code: 80 3f 00 74 15 48 89 f8 66 0f 1f 44 00 00 48 83 c0 01 80 38 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693727] RIP  [strlen+2/32] strlen+0x2/0x20
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693733]  RSP <ffff81003583dc18>
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693735] CR2: 0000000000000000
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.693736]  <6>sd 1:0:0:0: scsi: Device offlined - not ready after error recovery
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.694945] sd 1:0:0:0: SCSI error: return code = 0x00010000
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.694948] end_request: I/O error, dev sda, sector 0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.694951] printk: 4 messages suppressed.
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.694954] Buffer I/O error on device sda, logical block 0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.694981] Buffer I/O error on device sda, logical block 0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.694995] Buffer I/O error on device sda, logical block 0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.695003] Buffer I/O error on device sda, logical block 0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.695011] Buffer I/O error on device sda, logical block 0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.695015] ldm_validate_partition_table(): Disk read failed.
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.695021] Buffer I/O error on device sda, logical block 0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.695028] Buffer I/O error on device sda, logical block 0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.695036] Buffer I/O error on device sda, logical block 0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.695043] Buffer I/O error on device sda, logical block 0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.695047] Dev sda: unable to read RDB block 0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.695052] Buffer I/O error on device sda, logical block 0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.695080]  unknown partition table
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.695124] sd 1:0:0:0: Attached scsi removable disk sda
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.695162] sd 1:0:0:0: Attached scsi generic sg0 type 0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.700278] sdb : READ CAPACITY failed.
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.700280] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.700283] sdb : sense not available. 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.700915] sdb: Write Protect is off
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.700918] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.700920] sdb: assuming drive cache: write through
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.700971] sd 1:0:0:1: Attached scsi removable disk sdb
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.701010] sd 1:0:0:1: Attached scsi generic sg1 type 0
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.751293] sda : READ CAPACITY failed.
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.751295] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.751299] sda : sense not available. 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.751453] sda: Write Protect is off
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.751456] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.751459] sda: assuming drive cache: write through
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.751625] sda : READ CAPACITY failed.
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.751627] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.751629] sda : sense not available. 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.751947] sda: Write Protect is off
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.751950] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.751952] sda: assuming drive cache: write through
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.753528] sda : READ CAPACITY failed.
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.753530] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.753535] sda : sense not available. 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.754830] sda: Write Protect is off
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.754835] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.754837] sda: assuming drive cache: write through
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.755006] sda : READ CAPACITY failed.
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.755008] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.755010] sda : sense not available. 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.755161] sda: Write Protect is off
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.755164] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.755166] sda: assuming drive cache: write through
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.842153] sdb : READ CAPACITY failed.
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.842155] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.842159] sdb : sense not available. 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.842884] sdb: Write Protect is off
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.842888] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.842890] sdb: assuming drive cache: write through
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.843361] sdb : READ CAPACITY failed.
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.843363] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.843365] sdb : sense not available. 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.843756] sdb: Write Protect is off
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.843759] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.843761] sdb: assuming drive cache: write through
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.846974] sdb : READ CAPACITY failed.
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.846976] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.846980] sdb : sense not available. 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.847415] sdb: Write Protect is off
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.847418] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.847421] sdb: assuming drive cache: write through
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.848490] sdb : READ CAPACITY failed.
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.848492] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.848496] sdb : sense not available. 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.848887] sdb: Write Protect is off
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.848890] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.848892] sdb: assuming drive cache: write through
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.877955] sdb : READ CAPACITY failed.
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.877957] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.877962] sdb : sense not available. 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.879542] sdb: Write Protect is off
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.879546] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.879549] sdb: assuming drive cache: write through
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.882726] sdb : READ CAPACITY failed.
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.882729] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.882733] sdb : sense not available. 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.883173] sdb: Write Protect is off
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.883176] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.883179] sdb: assuming drive cache: write through
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.917789] sda : READ CAPACITY failed.
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.917791] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.917795] sda : sense not available. 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.918317] sda: Write Protect is off
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.918320] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.918322] sda: assuming drive cache: write through
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.918716] sda : READ CAPACITY failed.
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.918718] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.918720] sda : sense not available. 
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.919827] sda: Write Protect is off
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.919831] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:36 freekaleek-laptop kernel: [10278.919833] sda: assuming drive cache: write through
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.495252] sdb : READ CAPACITY failed.
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.495254] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.495258] sdb : sense not available. 
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.495737] sdb: Write Protect is off
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.495740] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.495742] sdb: assuming drive cache: write through
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.496168] sdb : READ CAPACITY failed.
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.496169] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.496172] sdb : sense not available. 
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.496561] sdb: Write Protect is off
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.496564] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.496566] sdb: assuming drive cache: write through
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.524771] sda : READ CAPACITY failed.
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.524773] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.524778] sda : sense not available. 
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.526612] sda: Write Protect is off
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.526617] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.526620] sda: assuming drive cache: write through
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.528662] sda : READ CAPACITY failed.
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.528663] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.528667] sda : sense not available. 
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.529059] sda: Write Protect is off
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.529062] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:38 freekaleek-laptop kernel: [10280.529064] sda: assuming drive cache: write through
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.383101] sdb : READ CAPACITY failed.
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.383103] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.383108] sdb : sense not available. 
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.383609] sdb: Write Protect is off
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.383612] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.383614] sdb: assuming drive cache: write through
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.384015] sdb : READ CAPACITY failed.
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.384017] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.384019] sdb : sense not available. 
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.384398] sdb: Write Protect is off
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.384401] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.384403] sdb: assuming drive cache: write through
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.413285] sda : READ CAPACITY failed.
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.413287] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.413291] sda : sense not available. 
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.413775] sda: Write Protect is off
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.413778] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.413780] sda: assuming drive cache: write through
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.414169] sda : READ CAPACITY failed.
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.414170] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.414173] sda : sense not available. 
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.414399] sda: Write Protect is off
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.414402] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:40 freekaleek-laptop kernel: [10281.414404] sda: assuming drive cache: write through
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.821718] sdb : READ CAPACITY failed.
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.821721] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.821726] sdb : sense not available. 
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.822284] sdb: Write Protect is off
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.822287] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.822289] sdb: assuming drive cache: write through
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.822705] sdb : READ CAPACITY failed.
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.822706] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.822709] sdb : sense not available. 
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.823106] sdb: Write Protect is off
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.823108] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.823111] sdb: assuming drive cache: write through
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.889455] sda : READ CAPACITY failed.
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.889457] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.889463] sda : sense not available. 
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.890051] sda: Write Protect is off
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.890055] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.890057] sda: assuming drive cache: write through
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.890478] sda : READ CAPACITY failed.
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.890479] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.890482] sda : sense not available. 
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.890926] sda: Write Protect is off
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.890929] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:42 freekaleek-laptop kernel: [10282.890931] sda: assuming drive cache: write through
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.397603] sdb : READ CAPACITY failed.
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.397605] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.397610] sdb : sense not available. 
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.398151] sdb: Write Protect is off
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.398155] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.398157] sdb: assuming drive cache: write through
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.398558] sdb : READ CAPACITY failed.
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.398559] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.398562] sdb : sense not available. 
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.398967] sdb: Write Protect is off
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.398970] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.398972] sdb: assuming drive cache: write through
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.426927] sda : READ CAPACITY failed.
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.426929] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.426934] sda : sense not available. 
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.427409] sda: Write Protect is off
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.427412] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.427414] sda: assuming drive cache: write through
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.427810] sda : READ CAPACITY failed.
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.427812] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.427814] sda : sense not available. 
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.429350] sda: Write Protect is off
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.429355] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:44 freekaleek-laptop kernel: [10284.429357] sda: assuming drive cache: write through
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.302013] sdb : READ CAPACITY failed.
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.302016] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.302021] sdb : sense not available. 
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.302414] sdb: Write Protect is off
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.302417] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.302421] sdb: assuming drive cache: write through
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.303061] sdb : READ CAPACITY failed.
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.303062] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.303065] sdb : sense not available. 
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.303455] sdb: Write Protect is off
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.303458] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.303460] sdb: assuming drive cache: write through
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.370955] sda : READ CAPACITY failed.
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.370958] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.370964] sda : sense not available. 
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.371565] sda: Write Protect is off
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.371568] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.371571] sda: assuming drive cache: write through
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.371994] sda : READ CAPACITY failed.
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.371996] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.371999] sda : sense not available. 
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.372407] sda: Write Protect is off
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.372409] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:46 freekaleek-laptop kernel: [10285.372411] sda: assuming drive cache: write through
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.211987] sdb : READ CAPACITY failed.
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.211989] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.211996] sdb : sense not available. 
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.212547] sdb: Write Protect is off
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.212550] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.212552] sdb: assuming drive cache: write through
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.212994] sdb : READ CAPACITY failed.
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.212995] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.212998] sdb : sense not available. 
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.213235] sdb: Write Protect is off
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.213238] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.213240] sdb: assuming drive cache: write through
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.274557] sda : READ CAPACITY failed.
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.274561] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.274566] sda : sense not available. 
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.275164] sda: Write Protect is off
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.275167] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.275169] sda: assuming drive cache: write through
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.275588] sda : READ CAPACITY failed.
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.275589] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.275592] sda : sense not available. 
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.277127] sda: Write Protect is off
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.277134] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:48 freekaleek-laptop kernel: [10287.277137] sda: assuming drive cache: write through
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.016230] sdb : READ CAPACITY failed.
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.016232] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.016239] sdb : sense not available. 
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.017688] sdb: Write Protect is off
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.017695] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.017699] sdb: assuming drive cache: write through
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.030225] sdb : READ CAPACITY failed.
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.030227] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.030232] sdb : sense not available. 
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.030702] sdb: Write Protect is off
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.030705] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.030709] sdb: assuming drive cache: write through
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.049810] sda : READ CAPACITY failed.
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.049812] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.049817] sda : sense not available. 
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.050390] sda: Write Protect is off
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.050394] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.050396] sda: assuming drive cache: write through
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.050808] sda : READ CAPACITY failed.
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.050810] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.050812] sda : sense not available. 
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.051255] sda: Write Protect is off
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.051258] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:50 freekaleek-laptop kernel: [10289.051260] sda: assuming drive cache: write through
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.769077] sdb : READ CAPACITY failed.
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.769079] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.769084] sdb : sense not available. 
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.769694] sdb: Write Protect is off
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.769697] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.769699] sdb: assuming drive cache: write through
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.770123] sdb : READ CAPACITY failed.
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.770124] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.770127] sdb : sense not available. 
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.770531] sdb: Write Protect is off
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.770535] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.770537] sdb: assuming drive cache: write through
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.824703] sda : READ CAPACITY failed.
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.824705] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.824711] sda : sense not available. 
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.825295] sda: Write Protect is off
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.825299] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.825301] sda: assuming drive cache: write through
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.825718] sda : READ CAPACITY failed.
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.825719] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.825722] sda : sense not available. 
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.826209] sda: Write Protect is off
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.826212] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:52 freekaleek-laptop kernel: [10290.826214] sda: assuming drive cache: write through
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.731573] sdb : READ CAPACITY failed.
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.731575] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.731580] sdb : sense not available. 
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.733347] sdb: Write Protect is off
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.733353] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.733355] sdb: assuming drive cache: write through
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.737543] sdb : READ CAPACITY failed.
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.737545] sdb : status=0, message=00, host=1, driver=00 
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.737549] sdb : sense not available. 
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.738635] sdb: Write Protect is off
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.738640] sdb: Mode Sense: 00 00 00 00
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.738643] sdb: assuming drive cache: write through
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.759991] sda : READ CAPACITY failed.
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.759993] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.759997] sda : sense not available. 
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.760518] sda: Write Protect is off
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.760521] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.760523] sda: assuming drive cache: write through
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.763641] sda : READ CAPACITY failed.
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.763643] sda : status=0, message=00, host=1, driver=00 
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.763647] sda : sense not available. 
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.764118] sda: Write Protect is off
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.764121] sda: Mode Sense: 00 00 00 00
Jul 15 17:35:54 freekaleek-laptop kernel: [10291.764123] sda: assuming drive cache: write through
```

Hope that helps? Thanks a lot

Jack

---

### Post by IntuitiveNipple on 2007-07-15
Well there is the problem, starting  at "reset high speed USB device". For some reason the USB connection is failing and so whilst trying to scan the device it suddenly disappears and causes a pointer to a data structure the kernel was using to become NULL unexpectedly.

Now you have to discover *why*. I've done an initial Google search which shows this is a relatively common problem with multiple causes and solutions.

Can you provide the results of the following commands:
```
$ uname -a > usb-fault.log 
$ sudo lspci -v >> usb-fault.log
$ sudo lsusb -v >> usb-fault.log
$ gzip usb-fault.log
```
And attach usb-fault.log.gz to the reply.

Also, what make of motherboard and chipset is the PC and the USB stick?

Is there a USB hub between the stick and the PC or is the stick directly connected to the PC?

---

