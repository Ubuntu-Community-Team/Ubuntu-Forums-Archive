---
title: "USB does not detect devices, causes some applications to hang"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by JimmyBEng on 2007-10-12
system:
Model: dv9500t
Processor: Intel Core 2 Duo T7500 (2.2 GHz)
Wireless Card: Intel PRO/wireless 4965 AGN with Bluetooth
Graphics Card: NVIDIA GeForce 8600M GS

The problem I am having is with the usb.  Devices don't work when plugged in (usb mouse and usb flash drive).  It worked once after disabling the bluetooth service on startup, but haven't had it work since.

Also any applications that would try to look for usb devices hang.  Gimp when configuring a xsane plug-in, Banshee when configuring the audio player plug-in, and the common one is the lsusb command.

Any idea on how to determine what is going on?

usb sections of lspci -vv
```
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at f8404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
```

dmesg output attached ( i believe most USB related parts are in the second file.

---

### Post by JimmyBEng on 2007-10-16
oh yea, this is on Gutsy.

I suspect that it might have something to do with the segfault within modprobe
```
[   30.883130] Modules linked in: uvcvideo snd_seq_oss compat_ioctl32 snd_seq_midi_event snd_seq snd_timer snd_seq_device iwl4965 videodev v4l1_compat v4l2_common iwlwifi_mac80211 nvidia(P) hci_usb sdhci bluetooth snd cfg80211 i2c_core psmouse mmc_core serio_raw intel_agp shpchp pci_hotplug soundcore evdev ext3 jbd mbcache sd_mod sg sr_mod cdrom r8169 ohci1394 ieee1394 ehci_hcd ahci uhci_hcd ata_piix ata_generic libata scsi_mod usbcore thermal processor fan fuse apparmor commoncap
[   30.886558] Pid: 4023, comm: modprobe Tainted: P       2.6.22-14-generic #1
[   30.886639] RIP: 0010:[<ffffffff8893e6ff>]  [<ffffffff8893e6ff>] :uvcvideo:uvc_get_video_ctrl+0x14f/0x1a0
[   30.886801] RSP: 0000:ffff8100759afaa8  EFLAGS: 00010246
[   30.886886] RAX: 0000000000000000 RBX: ffff810075a807c0 RCX: ffff81007782bbc8
[   30.886966] RDX: 0000000000000000 RSI: ffff81007fe298a0 RDI: ffffffff80571b10
[   30.887048] RBP: ffff810075ac8048 R08: 0000000000000000 R09: 0000000000000000
[   30.887128] R10: 0000000000072e83 R11: 0000000000000001 R12: 000000000000001a
[   30.887218] R13: ffff810075ac8048 R14: ffff810075ac8048 R15: ffff810075ac8000
[   30.887302] FS:  00002b6d0284a6e0(0000) GS:ffff81000102b280(0000) knlGS:0000000000000000
[   30.887396] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   30.887477] CR2: ffffffffffffffe8 CR3: 0000000078826000 CR4: 00000000000006e0
[   30.887562] Process modprobe (pid: 4023, threadinfo ffff8100759ae000, task ffff8100766d46e0)
[   30.887656] Stack:  000000000000001a ffffffff000003e8 0000000000000000 0000000000000000
[   30.888069]  0000000000000000 ffff810001240000 ffffffff80500778 0000000000000002
[   30.888415]  0000000000000001 ffff810075a809c0 ffff810075a807c0 ffffffff8893e8d7
[   30.888684] Call Trace:
[   30.888837]  [<ffffffff8893e8d7>] :uvcvideo:uvc_video_init+0x37/0x160
[   30.888921]  [<ffffffff8893990e>] :uvcvideo:uvc_register_video+0x45e/0x6a0
[   30.889003]  [<ffffffff8893fc92>] :uvcvideo:uvc_ctrl_init_device+0x192/0x1c0
[   30.889087]  [<ffffffff88939fe5>] :uvcvideo:uvc_probe+0x2b5/0x1a60
[   30.889172]  [<ffffffff80293393>] __slab_alloc+0x1d3/0x400
[   30.889253]  [<ffffffff802e837c>] __sysfs_new_dirent+0x1c/0x60
[   30.889334]  [<ffffffff80293621>] kmem_cache_zalloc+0x61/0x90
[   30.889427]  [<ffffffff8803dad1>] :usbcore:usb_probe_interface+0xd1/0x120
[   30.889512]  [<ffffffff80391063>] driver_probe_device+0xa3/0x1b0
[   30.889592]  [<ffffffff80391329>] __driver_attach+0xc9/0xd0
[   30.889673]  [<ffffffff80391260>] __driver_attach+0x0/0xd0
[   30.889753]  [<ffffffff8039023d>] bus_for_each_dev+0x4d/0x80
[   30.889834]  [<ffffffff8039069f>] bus_add_driver+0xaf/0x1f0
[   30.889921]  [<ffffffff8803d4a9>] :usbcore:usb_register_driver+0xa9/0x120
[   30.890003]  [<ffffffff880b9080>] :uvcvideo:uvc_init+0x80/0x98
[   30.890085]  [<ffffffff80256edb>] sys_init_module+0x19b/0x19b0
[   30.890169]  [<ffffffff80326a21>] __up_write+0x21/0x130
[   30.890252]  [<ffffffff80209e8e>] system_call+0x7e/0x83
[   30.890332] 
[   30.890405] 
[   30.890406] Code: 8b 40 e8 89 43 14 48 83 c4 40 31 c0 5b 5d 41 5c c3 31 c0 48 
[   30.891881] RIP  [<ffffffff8893e6ff>] :uvcvideo:uvc_get_video_ctrl+0x14f/0x1a0
[   30.892036]  RSP <ffff8100759afaa8>
[   30.892111] CR2: ffffffffffffffe8
```

Anybody have any ides? Or places to look for more information on USB and/or this uvcvideo module?

---

### Post by Ayuthia on 2007-10-17
```
[ 5931.911432] usb 7-2: new high speed USB device using ehci_hcd and address 5
[ 5932.044329] usb 7-2: configuration #1 chosen from 1 choice
```

It appears that a USB device was plugged in and recognized at the end of your submitted dmesg.  Is that the case?  You might try to plug in your flash drive and see if a message appears in dmesg saying that it was recognized.  If it finds it, you might try to see if you can mount the device manually.

---

### Post by JimmyBEng on 2007-10-19
Both the mouse and the USB flash drive show messages in dmesg when the are connected and disconnected.  i can't seem to mount the drive, because there doesn't seem to be any device listed in /dev for the flash drive

---

### Post by Ayuthia on 2007-10-20
Well, there are two things that I can think of right now.  The first one is this one:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/27889](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/27889)

It says to try to remove ehci-hcd (sudo rmmod ehci-hcd).  If it works, it will result in a slow response with the USB device.

The other option is that you can try to find the device for your USB device.  My USB flash drive is listed under /mount/disk, but I have also found it under /dev/sdb1.  I also have a hard drive listed under /dev/sda1 so I am not for sure if yours follows the same naming convention or not.  It is possible that yours will show up as /dev/sda1 (not for sure though--they might just be reserved for hard drives).  You might try and see if /dev/sdb* exists before putting your flash device in and then place it in and check again.  If it shows up, then you know that it is under the /dev/sdb*.  If that does work, you can try the following:
```
sudo mkdir /media/disk
sudo mount /dev/sdb1 /media/disk
```

The second option worked for me, but like I already knew that my device was under /dev/sdb1.  If you have a feisty live CD, you might try and see if your flash drive is recognized under there and see which device it is connected (cat /etc/fstab or cat /etc/mtab).

---

### Post by JimmyBEng on 2007-10-20
Thanks for the suggestions Ayuthia.  No joy though.

Like in the bug post, the command hangs.  Unlike in the bug report, a reboot does not make it work.  I suspect that this would  not solve all of my problems however.  When I plug in the USB mouse it shows up in dmesg as a uhci device, so I suspect this could be a general USB problem not just USB 2.0.

there is no drive entry in /dev for the USB drive, I have two hard drives which show up as /dev/sda and /dev/sdb.  I would expect a USB flash drive to show up as /dev/sdc, but that does not happen.  Without a /dev entry mounting the drive is not an option.

---

### Post by JimmyBEng on 2007-10-27
> **JimmyBEng said:**
> 
I suspect that it might have something to do with the segfault within modprobe

I tried blacklisting this uvcvideo module, so it wouldn't load during startup, and USB seems to be working now.  Should have trusted the first instinct.

---

