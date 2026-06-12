---
title: "USB drive doesn't list"
date: 2009-09-20
forum: Hardware
---

### Post by litlfrog on 2009-09-20
I've got an external USB drive that only rarely works on my Ubuntu box at work. It showed up a couple of times yesterday at work when I plugged it in, but when I went to access files, the mount point would usually disappear. It doesn't even show up when I list USB devices. It had been correctly turned off in Windows using "Safely Remove Hardware," but I went and plugged it back into a Windows machine, did Safely Remove Hardware, and unplugged it again. No change, it's still not showing up on my list of devices. Any ideas? Thanks.

---

### Post by litlfrog on 2009-09-21
Bump--anyone?

---

### Post by Ayuthia on 2009-09-21
Have you checked dmesg from the Konsole after it disappears?  Usually when something gets disconnected, it is written in the log.

---

### Post by litlfrog on 2009-11-19
I'm coming back to revisit this problem today; I never fixed it. I tried plugging the drive (a Maxtor OneTouch) into both front USB ports and it doesn't show up. A different USB drive shows up just fine plugged in to either port. The OneTouch works fine on Windows machines. What's the next thing to try?

---

### Post by litlfrog on 2009-11-19
I tried unplugging it and plugging it back in. Here are the results of that dmesg command; I *think* I copied all the relevant bits here, it's hard to tell. 

> [21421.588759] usb-storage: device found at 9
[21421.588762] usb-storage: waiting for device to settle before scanning
[21426.592372] usb-storage: device scan complete
[21426.599391] scsi 5:0:0:0: Direct-Access     Maxtor   OneTouch         0125 PQ: 0 ANSI: 4
[21426.600037] sd 5:0:0:0: Attached scsi generic sg4 type 0
[21426.619381] sd 5:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[21426.626543] sd 5:0:0:0: [sdc] Write Protect is off
[21426.626553] sd 5:0:0:0: [sdc] Mode Sense: 2d 08 00 00
[21426.626557] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[21426.645318] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[21426.645332]  sdc: sdc1
[21426.715310] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[21426.715323] sd 5:0:0:0: [sdc] Attached SCSI disk
[21458.176056] usb 1-4: reset full speed USB device using ohci_hcd and address 9
[21468.562023] usb 1-4: reset full speed USB device using ohci_hcd and address 9
[21483.744036] usb 1-4: device descriptor read/64, error -110
[21499.028037] usb 1-4: device descriptor read/64, error -110
[21499.320038] usb 1-4: reset full speed USB device using ohci_hcd and address 9
[21514.488103] usb 1-4: device descriptor read/64, error -110
[21529.776065] usb 1-4: device descriptor read/64, error -110
[21530.056052] usb 1-4: reset full speed USB device using ohci_hcd and address 9
[21535.087941] usb 1-4: device descriptor read/8, error -110
[21540.208609] usb 1-4: device descriptor read/8, error -110
[21540.472051] usb 1-4: reset full speed USB device using ohci_hcd and address 9
[21545.496309] usb 1-4: device descriptor read/8, error -110
[21550.624629] usb 1-4: device descriptor read/8, error -110
[21550.728087] sd 5:0:0:0: Device offlined - not ready after error recovery
[21550.728111] sd 5:0:0:0: [sdc] Unhandled error code
[21550.728115] sd 5:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[21550.728121] end_request: I/O error, dev sdc, sector 512
[21550.728132] Buffer I/O error on device sdc, logical block 64
[21550.728141] Buffer I/O error on device sdc, logical block 65
[21550.728199] sd 5:0:0:0: rejecting I/O to offline device
[21550.728221] usb 1-4: USB disconnect, address 9
[21550.904080] usb 1-4: new full speed USB device using ohci_hcd and address 10
[21566.068067] usb 1-4: device descriptor read/64, error -110
[21581.364040] usb 1-4: device descriptor read/64, error -110
[21581.640094] usb 1-4: new full speed USB device using ohci_hcd and address 11
[21596.824098] usb 1-4: device descriptor read/64, error -110
[21612.108056] usb 1-4: device descriptor read/64, error -110
[21612.392055] usb 1-4: new full speed USB device using ohci_hcd and address 12
[21617.412807] usb 1-4: device descriptor read/8, error -110
[21622.532429] usb 1-4: device descriptor read/8, error -110
[21622.808050] usb 1-4: new full speed USB device using ohci_hcd and address 13
[21627.828970] usb 1-4: device descriptor read/8, error -110
[21632.952596] usb 1-4: device descriptor read/8, error -110
[21633.056055] hub 1-0:1.0: unable to enumerate USB device on port 4


---

### Post by litlfrog on 2009-11-21
Bump--anyone? It would be nice to be able to use this device on the Ubuntu machine, and I'm not seeing a reason why it shouldn't work.

---

### Post by PaulW21781 on 2009-12-04
I've recently come across this problem too...

ext3 formatted external USB drive, trying to copy data to it...  Drive works fine on my gentoo box, no issues, its just in Ubuntu it falls over...

```

[   53.772272] usb 1-1: new high speed USB device using ehci_hcd and address 2
[   53.921345] usb 1-1: configuration #1 chosen from 1 choice
[   54.000384] Initializing USB Mass Storage driver...
[   54.000998] scsi5 : SCSI emulation for USB Mass Storage devices
[   54.001168] usbcore: registered new interface driver usb-storage
[   54.001171] USB Mass Storage support registered.
[   54.001185] usb-storage: device found at 2
[   54.001187] usb-storage: waiting for device to settle before scanning
[   59.008741] usb-storage: device scan complete
[   59.020292] scsi 5:0:0:0: Direct-Access     ST375063 0AS                   PQ: 0 ANSI: 2 CCS
[   59.020713] sd 5:0:0:0: Attached scsi generic sg3 type 0
[   59.029723] sd 5:0:0:0: [sdc] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[   59.030459] sd 5:0:0:0: [sdc] Write Protect is off
[   59.030461] sd 5:0:0:0: [sdc] Mode Sense: 34 00 00 00
[   59.030464] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[   59.032208] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[   59.032214]  sdc:
[   62.543281] usb 2-5: new high speed USB device using ehci_hcd and address 4
[   62.670381] usb 2-5: configuration #1 chosen from 1 choice
[   62.677271] scsi6 : SCSI emulation for USB Mass Storage devices
[   69.219931]  sdc1
[   69.281588] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[   69.281593] sd 5:0:0:0: [sdc] Attached SCSI disk
[   71.649475] kjournald starting.  Commit interval 5 seconds
[   71.662293] EXT3 FS on sdc1, internal journal
[   71.662299] EXT3-fs: recovery complete.
[   71.672483] EXT3-fs: mounted filesystem with writeback data mode.
[   98.387270] __ratelimit: 9 callbacks suppressed
[  207.825034] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[  238.769303] sd 5:0:0:0: Device offlined - not ready after error recovery
[  238.769317] sd 5:0:0:0: [sdc] Unhandled error code
[  238.769319] sd 5:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[  238.769323] end_request: I/O error, dev sdc, sector 489683215
[  238.769329] Buffer I/O error on device sdc1, logical block 61210394
[  238.769331] lost page write due to I/O error on sdc1
[  238.769338] Buffer I/O error on device sdc1, logical block 61210395
[  238.769340] lost page write due to I/O error on sdc1
[  238.769343] Buffer I/O error on device sdc1, logical block 61210396
[  238.769345] lost page write due to I/O error on sdc1
[  238.769347] Buffer I/O error on device sdc1, logical block 61210397
[  238.769349] lost page write due to I/O error on sdc1
[  238.769352] Buffer I/O error on device sdc1, logical block 61210398
[  238.769354] lost page write due to I/O error on sdc1
[  238.769357] Buffer I/O error on device sdc1, logical block 61210399
[  238.769358] lost page write due to I/O error on sdc1
[  238.769361] Buffer I/O error on device sdc1, logical block 61210400
[  238.769363] lost page write due to I/O error on sdc1
[  238.769366] Buffer I/O error on device sdc1, logical block 61210401
[  238.769368] lost page write due to I/O error on sdc1
[  238.769370] Buffer I/O error on device sdc1, logical block 61210402
[  238.769372] lost page write due to I/O error on sdc1
[  238.769406] sd 5:0:0:0: rejecting I/O to offline device
[  238.769415] sd 5:0:0:0: rejecting I/O to offline device
[  238.769442] sd 5:0:0:0: rejecting I/O to offline device
[  238.769492] sd 5:0:0:0: rejecting I/O to offline device
[  238.769530] sd 5:0:0:0: rejecting I/O to offline device
[  238.769567] sd 5:0:0:0: rejecting I/O to offline device
[  238.769604] sd 5:0:0:0: rejecting I/O to offline device
[  238.769641] sd 5:0:0:0: rejecting I/O to offline device
[  238.769667] sd 5:0:0:0: rejecting I/O to offline device
[  238.769704] sd 5:0:0:0: rejecting I/O to offline device
[  238.769742] sd 5:0:0:0: rejecting I/O to offline device
[  238.769786] sd 5:0:0:0: rejecting I/O to offline device
[  238.769823] sd 5:0:0:0: rejecting I/O to offline device
[  238.769864] sd 5:0:0:0: rejecting I/O to offline device
[  238.769903] sd 5:0:0:0: rejecting I/O to offline device
[  238.769946] sd 5:0:0:0: rejecting I/O to offline device
[  238.769982] sd 5:0:0:0: rejecting I/O to offline device
[  238.770031] usb 1-1: USB disconnect, address 2
[  238.770042] sd 5:0:0:0: rejecting I/O to offline device
[  238.770081] sd 5:0:0:0: rejecting I/O to offline device
[  238.771026] EXT3-fs error (device sdc1): read_block_bitmap: Cannot read block bitmap - block_group = 1871, block_bitmap = 61308928
[  238.773179] sd 5:0:0:0: [sdc] Unhandled error code
[  238.773182] sd 5:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  238.773186] end_request: I/O error, dev sdc, sector 489683455
[  238.776444] Aborting journal on device sdc1.
[  238.776528] EXT3-fs error (device sdc1) in ext3_reserve_inode_write: Journal has aborted
[  238.776631] ------------[ cut here ]------------
[  238.776637] WARNING: at /build/buildd/linux-rt-2.6.31/fs/buffer.c:1145 mark_buffer_dirty+0x86/0xb0()
[  238.776640] Hardware name: Aspire 7720     
[  238.776641] Modules linked in: usb_storage cryptd aes_x86_64 aes_generic binfmt_misc ppdev vboxnetadp vboxnetflt vboxdrv snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy arc4 snd_seq_oss ecb snd_seq_midi snd_rawmidi snd_seq_midi_event iptable_filter snd_seq bridge snd_timer iwlagn ip_tables stp iwlcore snd_seq_device uvcvideo videodev snd sdhci_pci mac80211 bnep x_tables joydev sdhci ricoh_mmc soundcore v4l1_compat nvidia(P) cfg80211 snd_page_alloc psmouse v4l2_compat_ioctl32 serio_raw btusb acer_wmi led_class lirc_ene0100 lp lirc_dev parport raid10 raid456 raid6_pq async_xor async_memcpy async_tx xor raid1 multipath linear raid0 ohci1394 ieee1394 video tg3 intel_agp output
[  238.776698] Pid: 4240, comm: nautilus Tainted: P           2.6.31-9-rt #152-Ubuntu
[  238.776700] Call Trace:
[  238.776706]  [<ffffffff8105fce8>] warn_slowpath_common+0x78/0xb0
[  238.776709]  [<ffffffff8105fd2f>] warn_slowpath_null+0xf/0x20
[  238.776712]  [<ffffffff81149bc6>] mark_buffer_dirty+0x86/0xb0
[  238.776715]  [<ffffffff8119d392>] T.859+0x52/0x80
[  238.776717]  [<ffffffff8119d43a>] ext3_handle_error+0x7a/0xc0
[  238.776720]  [<ffffffff8119d50d>] __ext3_std_error+0x8d/0xa0
[  238.776724]  [<ffffffff811943bb>] ext3_reserve_inode_write+0x4b/0x90
[  238.776727]  [<ffffffff81194426>] ext3_mark_inode_dirty+0x26/0x50
[  238.776730]  [<ffffffff8118e74f>] ? ext3_discard_reservation+0x6f/0x90
[  238.776733]  [<ffffffff8119609d>] ext3_truncate+0x4ed/0x660
[  238.776737]  [<ffffffff81124e50>] ? unlock_super+0x20/0x30
[  238.776740]  [<ffffffff81196668>] ext3_write_begin+0x1c8/0x240
[  238.776743]  [<ffffffff811951b0>] ? ext3_get_block+0x0/0x120
[  238.776747]  [<ffffffff810df7b2>] generic_perform_write+0xb2/0x1c0
[  238.776750]  [<ffffffff811a43ce>] ? ext3_xattr_get+0x5e/0xa0
[  238.776754]  [<ffffffff810df946>] generic_file_buffered_write+0x86/0x140
[  238.776757]  [<ffffffff810e0de0>] __generic_file_aio_write_nolock+0x240/0x470
[  238.776760]  [<ffffffff810e1130>] generic_file_aio_write+0x70/0xf0
[  238.776763]  [<ffffffff81191025>] ext3_file_write+0x25/0xc0
[  238.776766]  [<ffffffff81122892>] do_sync_write+0xf2/0x130
[  238.776770]  [<ffffffff8107ae80>] ? autoremove_wake_function+0x0/0x40
[  238.776774]  [<ffffffff81012c86>] ? retint_kernel+0x26/0x30
[  238.776778]  [<ffffffff812255f1>] ? security_file_permission+0x11/0x20
[  238.776781]  [<ffffffff81122b78>] vfs_write+0xb8/0x1a0
[  238.776783]  [<ffffffff81123ecd>] ? fget_light+0x9d/0xb0
[  238.776785]  [<ffffffff811233ec>] sys_write+0x4c/0x80
[  238.776789]  [<ffffffff81012102>] system_call_fastpath+0x16/0x1b
[  238.776792] ---[ end trace 64bca549ed3ce221 ]---
[  238.780045] EXT3-fs error (device sdc1) in ext3_reserve_inode_write: Journal has aborted
[  238.780153] EXT3-fs error (device sdc1) in ext3_orphan_del: Journal has aborted
[  238.780244] EXT3-fs error (device sdc1) in ext3_truncate: Journal has aborted
[  238.780356] ext3_abort called.
[  238.780358] EXT3-fs error (device sdc1): ext3_journal_start_sb: Detected aborted journal
[  238.780361] Remounting filesystem read-only
[  238.826072] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
[  238.829146] EXT3-fs error (device sdc1): ext3_find_entry: reading directory #2 offset 0
[  238.996600] usb 1-1: new high speed USB device using ehci_hcd and address 3
[  239.150132] usb 1-1: configuration #1 chosen from 1 choice
[  239.200034] scsi7 : SCSI emulation for USB Mass Storage devices
[  239.203299] usb-storage: device found at 3
[  239.203302] usb-storage: waiting for device to settle before scanning
[  239.539464] ext3_abort called.
[  239.539470] EXT3-fs error (device sdc1): ext3_put_super: Couldn't clean up the journal
[  244.211622] usb-storage: device scan complete
[  244.266689] scsi 7:0:0:0: Direct-Access     ST375063 0AS                   PQ: 0 ANSI: 2 CCS
[  244.267886] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  244.358662] sd 7:0:0:0: [sdc] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[  244.360658] sd 7:0:0:0: [sdc] Write Protect is off
[  244.360662] sd 7:0:0:0: [sdc] Mode Sense: 34 00 00 00
[  244.360664] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  244.363641] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  244.363645]  sdc: sdc1
[  244.395853] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  244.395858] sd 7:0:0:0: [sdc] Attached SCSI disk
[  274.504064] kjournald starting.  Commit interval 5 seconds
[  274.847224] EXT3 FS on sdc1, internal journal
[  274.847230] EXT3-fs: recovery complete.
[  275.034469] EXT3-fs: mounted filesystem with writeback data mode.
```

---

