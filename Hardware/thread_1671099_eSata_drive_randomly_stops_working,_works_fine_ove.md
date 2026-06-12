---
title: "eSata drive randomly stops working, works fine over USB."
date: 2011-01-19
forum: Hardware
---

### Post by Xavier Oddmon on 2011-01-19
Hello! I have an external Cavalry one terabyte hard drive with eSata and USB connections. Over USB, the drive works fine. However, when using eSata, it runs for an amount of time, and then abruptly stops doing anything. Any file transfers to the device just hang, even doing something like "ls /media/Cavalry1TB" in gnome-terminal just blocks, never finishing (and pressing ctrl+c just prints ^C". When the drive is plugged in over USB, everything is fine.

This was found in syslog:
```
Jan 19 14:50:29 chris-laptop kernel: [  550.610060] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 10)
Jan 19 14:50:29 chris-laptop kernel: [  550.612232] ata7.00: configured for UDMA/100
Jan 19 14:50:29 chris-laptop kernel: [  550.612245] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 19 14:50:29 chris-laptop kernel: [  550.612248] sd 7:0:0:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
Jan 19 14:50:29 chris-laptop kernel: [  550.612252] Descriptor sense data with sense descriptors (in hex):
Jan 19 14:50:29 chris-laptop kernel: [  550.612254]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jan 19 14:50:29 chris-laptop kernel: [  550.612261]         3a 04 00 af 
Jan 19 14:50:29 chris-laptop kernel: [  550.612264] sd 7:0:0:0: [sdb] Add. Sense: Scsi parity error
Jan 19 14:50:29 chris-laptop kernel: [  550.612268] sd 7:0:0:0: [sdb] CDB: Write(10): 2a 00 3a 04 00 4f 00 00 e0 00
Jan 19 14:50:29 chris-laptop kernel: [  550.612275] end_request: I/O error, dev sdb, sector 973340751
Jan 19 14:50:29 chris-laptop kernel: [  550.612297] ata7: EH complete
Jan 19 14:50:29 chris-laptop kernel: [  550.612342] Aborting journal on device sdb1-8.
Jan 19 14:50:29 chris-laptop kernel: [  550.612364] EXT4-fs error (device sdb1) in ext4_new_inode: Journal has aborted
Jan 19 14:50:29 chris-laptop kernel: [  550.613395] EXT4-fs error (device sdb1) in ext4_mkdir: Journal has aborted
Jan 19 14:50:37 chris-laptop kernel: [  558.550993] EXT4-fs error (device sdb1): ext4_journal_start_sb: Detected aborted journal
Jan 19 14:50:37 chris-laptop kernel: [  558.551008] EXT4-fs (sdb1): Remounting filesystem read-only
Jan 19 14:51:14 chris-laptop kernel: [  595.522297] EXT4-fs error (device sdb1): ext4_put_super: Couldn't clean up the journal
Jan 19 14:51:28 chris-laptop kernel: [  609.660074] ata7.00: limiting speed to UDMA/66:PIO4
Jan 19 14:51:28 chris-laptop kernel: [  609.660086] ata7.00: exception Emask 0x10 SAct 0x1 SErr 0x0 action 0x6 frozen
Jan 19 14:51:28 chris-laptop kernel: [  609.660094] ata7.00: irq_stat 0x00020002, failed to transmit command FIS
Jan 19 14:51:28 chris-laptop kernel: [  609.660102] ata7.00: failed command: READ FPDMA QUEUED
Jan 19 14:51:28 chris-laptop kernel: [  609.660116] ata7.00: cmd 60/02:00:41:00:00/00:00:00:00:00/40 tag 0 ncq 1024 in
Jan 19 14:51:28 chris-laptop kernel: [  609.660119]          res 60/02:00:41:00:00/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
Jan 19 14:51:28 chris-laptop kernel: [  609.660126] ata7.00: status: { DRDY DF }
Jan 19 14:51:28 chris-laptop kernel: [  609.660136] ata7: hard resetting link
Jan 19 14:51:28 chris-laptop kernel: [  609.660141] ata7: controller in dubious state, performing PORT_RST
Jan 19 14:51:38 chris-laptop kernel: [  619.742681] ata7: SATA link down (SStatus 1 SControl 10)
Jan 19 14:51:38 chris-laptop kernel: [  619.757567] ata7: hard resetting link
Jan 19 14:51:43 chris-laptop kernel: [  624.812715] ata7: SATA link down (SStatus 1 SControl 10)
Jan 19 14:51:43 chris-laptop kernel: [  624.822654] ata7: hard resetting link
Jan 19 14:51:44 chris-laptop kernel: [  626.146358] pciehp 0000:00:1c.2:pcie04: Card not present on Slot(34)
Jan 19 14:51:46 chris-laptop kernel: [  628.240198] ata7: SATA link down (SStatus FFFFFFFF SControl FFFFFFFF)
Jan 19 14:51:46 chris-laptop kernel: [  628.240214] ata7.00: disabled
Jan 19 14:51:46 chris-laptop kernel: [  628.240248] sd 7:0:0:0: [sdb] Unhandled sense code
Jan 19 14:51:46 chris-laptop kernel: [  628.240253] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan 19 14:51:46 chris-laptop kernel: [  628.240262] sd 7:0:0:0: [sdb] Sense Key : Hardware Error [current] [descriptor]
Jan 19 14:51:46 chris-laptop kernel: [  628.240272] Descriptor sense data with sense descriptors (in hex):
Jan 19 14:51:46 chris-laptop kernel: [  628.240277]         72 04 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jan 19 14:51:46 chris-laptop kernel: [  628.240299]         00 00 00 41 
Jan 19 14:51:46 chris-laptop kernel: [  628.240308] sd 7:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 19 14:51:46 chris-laptop kernel: [  628.240317] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 41 00 00 02 00
Jan 19 14:51:46 chris-laptop kernel: [  628.240337] end_request: I/O error, dev sdb, sector 65
Jan 19 14:51:46 chris-laptop kernel: [  628.240381] ata7: EH complete
Jan 19 14:51:46 chris-laptop kernel: [  628.240390] EXT4-fs (sdb1): unable to read superblock
Jan 19 14:51:46 chris-laptop kernel: [  628.240402] ------------[ cut here ]------------
Jan 19 14:51:46 chris-laptop kernel: [  628.240417] WARNING: at /build/buildd/linux-2.6.32/drivers/ata/libata-core.c:6342 ata_port_detach+0x7c/0x80()
Jan 19 14:51:46 chris-laptop kernel: [  628.240428] Hardware name: EX700
Jan 19 14:51:46 chris-laptop kernel: [  628.240432] Modules linked in: usb_storage hidp hid webcamstudio videodev v4l1_compat v4l2_compat_ioctl32 rfcomm binfmt_misc ppdev sco bridge stp bnep l2cap vboxnetflt vboxdrv joydev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device arc4 btusb bluetooth iwlagn iwlcore mac80211 fbcon tileblit font bitblit softcursor ohci1394 psmouse serio_raw sdhci_pci sdhci led_class nvidia(P) snd vga16fb vgastate cfg80211 intel_agp video output soundcore snd_page_alloc wacom lp parport ieee1394 r8169 mii sata_sil24
Jan 19 14:51:46 chris-laptop kernel: [  628.240560] Pid: 45, comm: pciehpd Tainted: P        W  2.6.32-27-generic #49-Ubuntu
Jan 19 14:51:46 chris-laptop kernel: [  628.240566] Call Trace:
Jan 19 14:51:46 chris-laptop kernel: [  628.240580]  [<ffffffff8106604b>] warn_slowpath_common+0x7b/0xc0
Jan 19 14:51:46 chris-laptop kernel: [  628.240589]  [<ffffffff810660a4>] warn_slowpath_null+0x14/0x20
Jan 19 14:51:46 chris-laptop kernel: [  628.240596]  [<ffffffff813a173c>] ata_port_detach+0x7c/0x80
Jan 19 14:51:46 chris-laptop kernel: [  628.240603]  [<ffffffff813a1770>] ata_host_detach+0x30/0x50
Jan 19 14:51:46 chris-laptop kernel: [  628.240610]  [<ffffffff813a17aa>] ata_pci_remove_one+0x1a/0x20
Jan 19 14:51:46 chris-laptop kernel: [  628.240620]  [<ffffffff812d12c4>] pci_device_remove+0x34/0x60
Jan 19 14:51:46 chris-laptop kernel: [  628.240635]  [<ffffffff8136ac2f>] __device_release_driver+0x6f/0xe0
Jan 19 14:51:46 chris-laptop kernel: [  628.240643]  [<ffffffff8136ad9d>] device_release_driver+0x2d/0x40
Jan 19 14:51:46 chris-laptop kernel: [  628.240650]  [<ffffffff81369dba>] bus_remove_device+0x9a/0xc0
Jan 19 14:51:46 chris-laptop kernel: [  628.240660]  [<ffffffff81367f17>] device_del+0x127/0x1d0
Jan 19 14:51:46 chris-laptop kernel: [  628.240668]  [<ffffffff81367fd6>] device_unregister+0x16/0x30
Jan 19 14:51:46 chris-laptop kernel: [  628.240678]  [<ffffffff812cb529>] pci_stop_bus_device+0x69/0x80
Jan 19 14:51:46 chris-laptop kernel: [  628.240686]  [<ffffffff812cb5fa>] pci_remove_bus_device+0x1a/0xe0
Jan 19 14:51:46 chris-laptop kernel: [  628.240696]  [<ffffffff812de775>] pciehp_unconfigure_device+0xb5/0x1c0
Jan 19 14:51:46 chris-laptop kernel: [  628.240705]  [<ffffffff81060db1>] ? dequeue_entity+0x1a1/0x1e0
Jan 19 14:51:46 chris-laptop kernel: [  628.240714]  [<ffffffff812dda58>] pciehp_disable_slot+0x78/0x230
Jan 19 14:51:46 chris-laptop kernel: [  628.240722]  [<ffffffff812de13c>] pciehp_power_thread+0xac/0x130
Jan 19 14:51:46 chris-laptop kernel: [  628.240730]  [<ffffffff812de090>] ? pciehp_power_thread+0x0/0x130
Jan 19 14:51:46 chris-laptop kernel: [  628.240740]  [<ffffffff8107fad7>] run_workqueue+0xc7/0x1a0
Jan 19 14:51:46 chris-laptop kernel: [  628.240748]  [<ffffffff8107fc53>] worker_thread+0xa3/0x110
Jan 19 14:51:46 chris-laptop kernel: [  628.240757]  [<ffffffff810846a0>] ? autoremove_wake_function+0x0/0x40
Jan 19 14:51:46 chris-laptop kernel: [  628.240765]  [<ffffffff8107fbb0>] ? worker_thread+0x0/0x110
Jan 19 14:51:46 chris-laptop kernel: [  628.240772]  [<ffffffff81084326>] kthread+0x96/0xa0
Jan 19 14:51:46 chris-laptop kernel: [  628.240782]  [<ffffffff810131ea>] child_rip+0xa/0x20
Jan 19 14:51:46 chris-laptop kernel: [  628.240789]  [<ffffffff81084290>] ? kthread+0x0/0xa0
Jan 19 14:51:46 chris-laptop kernel: [  628.240796]  [<ffffffff810131e0>] ? child_rip+0x0/0x20
Jan 19 14:51:46 chris-laptop kernel: [  628.240802] ---[ end trace 638ac95b619b413a ]---
Jan 19 14:51:46 chris-laptop kernel: [  628.270640] sd 7:0:0:0: [sdb] Synchronizing SCSI cache
Jan 19 14:51:46 chris-laptop kernel: [  628.271441] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jan 19 14:51:46 chris-laptop kernel: [  628.271452] sd 7:0:0:0: [sdb] Stopping disk
Jan 19 14:51:46 chris-laptop kernel: [  628.271477] sd 7:0:0:0: [sdb] START_STOP FAILED
Jan 19 14:51:46 chris-laptop kernel: [  628.271482] sd 7:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Jan 19 14:51:46 chris-laptop kernel: [  628.274068] sata_sil24 0000:04:00.0: PCI INT A disabled
```
I'm running 10.04, x64.

---

