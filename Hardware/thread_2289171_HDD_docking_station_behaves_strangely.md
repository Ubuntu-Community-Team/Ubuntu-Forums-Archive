---
title: "HDD docking station behaves strangely"
date: 2015-08-01
forum: Hardware
---

### Post by MFH86 on 2015-08-01
Hi everybody. I'm not really used to ask for help for my problems, but sometimes they are above my skills.
Here's my problem: More than a year ago I bought an HDD docking station, a SATA QuickPort Quattro by Sharkoon ([link]("http://www.sharkoon.com/?q=en/node/1825")). From the beginning it had a few problems, at random moments, rarely, one of the disks could shut down for no apparent reason and disappeared from the list of available disks, so I had to unplug the docking station and plug it in again. It was rare enough to be annoying but bearable. At a certain moment a kernel update created a much bigger problem: every time I tried to connect the dock to the USB3 port, it couldn't recognize the hardware. I didn't have much time to investigate, I just uninstalled the newest kernel and stopped any update. Not a good solution, I know... More recently I decided it was time for a complete renewal and I installed Ubuntu MATE 15.04, a new, pristine installation. I had enough time to forget I had good reasons not to update the system and the problem showed up really quickly. I've had more than a month to analyse the problem a little deeper. This is what I discovered:

[LIST]
[*]If I connect the DS to the USB3 port while the computer is running, the port crashes. I don't know any better way to describe what happens, some background process uses most of my CPU and every USB port stops working for a while, then everything returns to its original state, except the USB3 port, that stops working completely. 
[*]If I connect the DS to a USB2 port while the computer is running or if I connect the DS to the USB3 port before starting the computer, the dock is recognized and works properly. Well, I have to use the disks almost continuously, otherwise they go to some kind of sleep mode and sometimes trying to re-awaken them shuts down all disks. 
[/LIST]


I already tried to ask the same question [here]("http://askubuntu.com/questions/641004/bad-interaction-within-usb3-port-and-hdd-docking-station"), but had no luck.
About my computer:

[LIST]
[*]Laptop: Acer Aspire TimelineX 4830T 
[*]External disks: 4 HDD, 3 TB each. I can plug each disk separately using another device and there is no problem. 
[*]uname -a: ```
Linux *** 3.19.0-25-generic #26-Ubuntu SMP Fri Jul 24 21:17:31 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```
(Since the username is my first name, I replaced it with ***) 
[*]You can find a couple of dmesg selections in the link above. 
[*]Sadly I don't have any older information, nor a way to obtain them. 
[/LIST]
 If you need more informations I'll be happy to provide them.

What can I do to finally have the docking station work?
Thanks for your time. I hope everything I wrote makes sense in English. :)

**Edit**: I received right now an error message:
> Error mounting /dev/sdb at /media/***/HDD3: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb" "/media/***/HDD3"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb, missing codepage or helper program, or other error
In some cases useful info is found in syslog - try dmesg | tail or so.
I tried to access one of the disks and the whole DS disconnected. I shut two of the disks down and magically the OS noticed the other two. Then as I described above the computer paused for a few seconds and the error message appeared.
This is the last (relevant) part of dmesg:
> [50666.076453] usb 2-1: reset SuperSpeed USB device number 2 using xhci_hcd
[50666.093803] usb 2-1: device firmware changed
[50666.093953] usb 2-1: USB disconnect, device number 2
[50666.099507] sd 3:0:0:2: [sdd] FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[50666.099512] sd 3:0:0:2: [sdd] CDB: 
[50666.099514] Write(16): 8a 00 00 00 00 00 ae 84 58 58 00 00 00 10 00 00
[50666.099524] blk_update_request: I/O error, dev sdd, sector 2927908952
[50666.099646] Aborting journal on device sdd-8.
[50666.099667] EXT4-fs error (device sdd) in ext4_reserve_inode_write:4737: Journal has aborted
[50666.099668] JBD2: Error -5 detected when updating journal superblock for sdd-8.
[50666.099693] EXT4-fs error (device sdd) in ext4_dirty_inode:4856: Journal has aborted
[50666.099696] EXT4-fs (sdd): previous I/O error to superblock detected
[50666.100244] EXT4-fs error (device sdd) in ext4_reserve_inode_write:4737: Journal has aborted
[50666.100250] EXT4-fs (sdd): previous I/O error to superblock detected
[50666.100821] EXT4-fs error (device sdd) in ext4_dirty_inode:4856: Journal has aborted
[50666.100827] EXT4-fs (sdd): previous I/O error to superblock detected
[50666.139928] Buffer I/O error on dev sdc, logical block 365985792, lost sync page write
[50666.139935] JBD2: Error -5 detected when updating journal superblock for sdc-8.
[50666.151908] Buffer I/O error on dev sdb, logical block 365985792, lost sync page write
[50666.151914] JBD2: Error -5 detected when updating journal superblock for sdb-8.
[50666.187412] xhci_hcd 0000:05:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880252d46000
[50666.187417] xhci_hcd 0000:05:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff880252d46048
[50666.212180] Buffer I/O error on dev sde, logical block 365985792, lost sync page write
[50666.212187] JBD2: Error -5 detected when updating journal superblock for sde-8.
[50678.655822] EXT4-fs error (device sdd): ext4_put_super:780: Couldn't clean up the journal
[50678.655832] EXT4-fs (sdd): Remounting filesystem read-only
[50697.370402] usb 1-1: new high-speed USB device number 2 using xhci_hcd
[50697.534835] usb 2-1: new SuperSpeed USB device number 3 using xhci_hcd
[50697.555266] usb 2-1: New USB device found, idVendor=152d, idProduct=0539
[50697.555275] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[50697.555280] usb 2-1: Product: USB to ATA/ATAPI Bridge
[50697.555285] usb 2-1: Manufacturer: JMicron
[50697.555288] usb 2-1: SerialNumber: 1F40FFFFFFFF
[50697.556490] usb-storage 2-1:1.0: USB Mass Storage device detected
[50697.557161] usb-storage 2-1:1.0: Quirks match for vid 152d pid 0539: 4000000
[50697.557204] scsi host7: usb-storage 2-1:1.0
[50698.556479] scsi 7:0:0:0: Direct-Access     ST3000DM 001-1CH166            PQ: 0 ANSI: 5
[50698.556968] scsi 7:0:0:1: Direct-Access     ST3000DM 001-1ER166            PQ: 0 ANSI: 5
[50698.557644] sd 7:0:0:0: Attached scsi generic sg2 type 0
[50698.557834] sd 7:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[50698.558100] sd 7:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[50698.558123] sd 7:0:0:1: Attached scsi generic sg3 type 0
[50698.558658] sd 7:0:0:0: [sdb] Write Protect is off
[50698.558664] sd 7:0:0:0: [sdb] Mode Sense: 28 00 00 00
[50698.559311] sd 7:0:0:0: [sdb] No Caching mode page found
[50698.559329] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[50698.567392] sd 7:0:0:1: [sdc] Very big device. Trying to use READ CAPACITY(16).
[50698.567784] sd 7:0:0:1: [sdc] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[50698.567996] sd 7:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[50698.568595] sd 7:0:0:1: [sdc] Write Protect is off
[50698.568606] sd 7:0:0:1: [sdc] Mode Sense: 28 00 00 00
[50698.569427] sd 7:0:0:1: [sdc] No Caching mode page found
[50698.569434] sd 7:0:0:1: [sdc] Assuming drive cache: write through
[50698.570792] sd 7:0:0:1: [sdc] Very big device. Trying to use READ CAPACITY(16).
[50700.656296]  sdb: unknown partition table
[50700.656506]  sdc: unknown partition table
[50700.657873] sd 7:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
[50700.658084] sd 7:0:0:1: [sdc] Very big device. Trying to use READ CAPACITY(16).
[50700.660098] sd 7:0:0:0: [sdb] Attached SCSI disk
[50700.660592] sd 7:0:0:1: [sdc] Attached SCSI disk
[50701.290087] EXT4-fs (sdc): recovery complete
[50701.290526] EXT4-fs (sdc): mounted filesystem with ordered data mode. Opts: (null)
[50701.392749] EXT4-fs (sdb): recovery complete
[50701.393238] EXT4-fs (sdb): mounted filesystem with ordered data mode. Opts: (null)
[50707.382823] xhci_hcd 0000:05:00.0: xHCI host not responding to stop endpoint command.
[50707.382838] xhci_hcd 0000:05:00.0: Assuming host is dying, halting host.
[50707.456092] xhci_hcd 0000:05:00.0: Host not halted after 16000 microseconds.
[50707.456099] xhci_hcd 0000:05:00.0: Non-responsive xHCI host is not halting.
[50707.456101] xhci_hcd 0000:05:00.0: Completing active URBs anyway.
[50707.456116] xhci_hcd 0000:05:00.0: HC died; cleaning up
[50707.494935] sd 7:0:0:0: [sdb] FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[50707.494941] sd 7:0:0:0: [sdb] CDB: 
[50707.494952] Read(16): 88 00 00 00 00 00 00 00 00 08 00 00 00 08 00 00
[50707.494978] blk_update_request: I/O error, dev sdb, sector 8
[50707.495020] EXT4-fs (sdb): can't read group descriptor 0
[50731.319330] sd 7:0:0:1: [sdc] FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[50731.319338] sd 7:0:0:1: [sdc] CDB: 
[50731.319350] Write(16): 8a 00 00 00 00 00 00 00 21 08 00 00 00 08 00 00
[50731.319368] blk_update_request: I/O error, dev sdc, sector 8456
[50731.319374] Buffer I/O error on dev sdc, logical block 1057, lost async page write
[50731.359366] sd 7:0:0:1: [sdc] FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[50731.359372] sd 7:0:0:1: [sdc] CDB: 
[50731.359374] Write(16): 8a 00 00 00 00 00 75 40 01 00 00 00 00 08 00 00
[50731.359400] blk_update_request: I/O error, dev sdc, sector 1967128832
[50731.359404] Buffer I/O error on dev sdc, logical block 245891104, lost async page write
[50732.320148] NMI watchdog: BUG: soft lockup - CPU#2 stuck for 23s! [swapper/2:0]
[50732.320154] Modules linked in: pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) ctr ccm binfmt_misc bbswitch(OE) snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media snd_hda_intel snd_hda_controller intel_rapl snd_hda_codec iosf_mbi x86_pkg_temp_thermal intel_powerclamp snd_hwdep coretemp arc4 snd_pcm kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_seq_midi snd_seq_midi_event aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper ath9k cryptd snd_rawmidi ath9k_common ath9k_hw ath snd_seq mac80211 serio_raw i915 snd_seq_device snd_timer snd cfg80211 drm_kms_helper rtsx_pci_ms lpc_ich mei_me memstick mei drm soundcore i2c_algo_bit shpchp joydev acer_wmi mxm_wmi sparse_keymap
[50732.320224]  wmi video mac_hid parport_pc ppdev lp parport autofs4 hid_generic usbhid hid uas usb_storage rtsx_pci_sdmmc psmouse atl1c ahci sdhci_pci libahci rtsx_pci sdhci
[50732.320241] CPU: 2 PID: 0 Comm: swapper/2 Tainted: G           OE  3.19.0-25-generic #26-Ubuntu
[50732.320244] Hardware name: Acer Aspire 4830TG/JM40_HR, BIOS V1.05 06/08/2011
[50732.320246] task: ffff880256258000 ti: ffff880256260000 task.ti: ffff880256260000
[50732.320249] RIP: 0010:[<ffffffff815fc96d>]  [<ffffffff815fc96d>] xhci_handshake+0x3d/0x70
[50732.320256] RSP: 0018:ffff88025fa83df8  EFLAGS: 00000206
[50732.320258] RAX: 0000000000000008 RBX: 00000000aac05284 RCX: 000000006719b016
[50732.320260] RDX: 00006e6900000000 RSI: ffffc90010e84038 RDI: 0000000000000948
[50732.320262] RBP: ffff88025fa83e18 R08: 00000000004c4b40 R09: ffff8802563c4000
[50732.320264] R10: 0000000000000296 R11: 0000000000000497 R12: ffff88025fa83d68
[50732.320265] R13: ffffffff817cc67d R14: ffff88025fa83e18 R15: ffffc90010e84038
[50732.320268] FS:  0000000000000000(0000) GS:ffff88025fa80000(0000) knlGS:0000000000000000
[50732.320270] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[50732.320272] CR2: 0000000000b6b0a8 CR3: 0000000001c13000 CR4: 00000000000407e0
[50732.320273] Stack:
[50732.320275]  ffff880253320000 ffff880253320048 0000000000000296 ffffffff81607ff0
[50732.320278]  ffff88025fa83e48 ffffffff816080e4 ffff88004a3ec068 ffff8802533200a8
[50732.320281]  ffff8802533200a8 0000000000000100 ffff88025fa83e88 ffffffff810dd4e9
[50732.320284] Call Trace:
[50732.320286]  <IRQ> 

[50732.320293]  [<ffffffff81607ff0>] ? xhci_cleanup_command_queue+0xa0/0xa0
[50732.320297]  [<ffffffff816080e4>] xhci_handle_command_timeout+0xf4/0x1e0
[50732.320302]  [<ffffffff810dd4e9>] call_timer_fn+0x39/0x110
[50732.320306]  [<ffffffff81607ff0>] ? xhci_cleanup_command_queue+0xa0/0xa0
[50732.320309]  [<ffffffff810df350>] run_timer_softirq+0x250/0x320
[50732.320314]  [<ffffffff8107ae99>] __do_softirq+0x109/0x270
[50732.320317]  [<ffffffff8107b165>] irq_exit+0x95/0xa0
[50732.320322]  [<ffffffff817ce646>] smp_apic_timer_interrupt+0x46/0x60
[50732.320326]  [<ffffffff817cc67d>] apic_timer_interrupt+0x6d/0x80
[50732.320327]  <EOI> 

[50732.320332]  [<ffffffff816663b2>] ? cpuidle_enter_state+0x62/0x160
[50732.320335]  [<ffffffff816663a1>] ? cpuidle_enter_state+0x51/0x160
[50732.320338]  [<ffffffff81666597>] cpuidle_enter+0x17/0x20
[50732.320342]  [<ffffffff810b7ce1>] cpu_startup_entry+0x311/0x3b0
[50732.320347]  [<ffffffff81049107>] start_secondary+0x197/0x1c0
[50732.320349] Code: 41 89 d5 53 41 89 cc 48 89 f3 eb 1d 66 90 44 21 e8 44 39 e0 74 28 bf c7 10 00 00 41 83 ee 01 e8 4a 6c dc ff 45 85 f6 7e 25 8b 03 <83> f8 ff 75 de 5b b8 ed ff ff ff 41 5c 41 5d 41 5e 5d c3 5b 31 
[50733.863444] xhci_hcd 0000:05:00.0: Stopped the command ring failed, maybe the host is dead
[50733.937388] xhci_hcd 0000:05:00.0: Host not halted after 16000 microseconds.
[50733.937393] xhci_hcd 0000:05:00.0: Abort command ring failed
[50733.937397] xhci_hcd 0000:05:00.0: HC died; cleaning up
[50733.937663] sched: RT throttling activated
[50733.938527] usb usb1-port1: couldn't allocate usb_device
[50733.938718] usb 2-1: USB disconnect, device number 3
[50734.001834] Buffer I/O error on dev sdc, logical block 365985792, lost sync page write
[50734.001840] JBD2: Error -5 detected when updating journal superblock for sdc-8.

---

### Post by MFH86 on 2015-08-05
Can anyone help me? It's a really annoying problem, I can use my external disks only when I start the computer, after 5 minutes of inactivity the disks go in sleepmode and I have a 50% chance that they disconnect all together when one of them wakes up.
It's absurd I have to restart my computer every time I need to connect the disks to the USB3 port.

By the way, I tried sdparm and hdparm to solve the disconnection-on-wake-up problem. The first one says it can't do anything, the second modifies successfully the standby timeout and the advanced power management, but nonetheless after 5 minutes of inactivities the disks slow down and go to sleep. Seems like a firmware feature, but I found a topic elsewhere (can't find the page now, sorry) where the producers say there is no such function in the firmware for this product and blame some system settings.

---

