---
title: "PPA 1455 USB Sound card - Soft Lockup"
date: 2010-11-26
forum: Hardware
---

### Post by fuzzylunkinz on 2010-11-26
I'm running "XBMC Dharma RC1," which uses a generic Ubuntu kernel.  I've got a cheap USB Sound card that locks up the system when I plug it in and/or when the system boots up.

Here is a link to the sound card.  I couldn't find an official site for it anywhere.
[PPA 1455 - Sound card - 48 kHz - 5.1 - USB]("http://www.amazon.com/PPA-1455-Sound-card-kHz/dp/B001LLX6QW/")

This is what I get from the syslog:
```
Nov 26 15:58:34 livecd kernel: [ 2496.452322] BUG: soft lockup - CPU#1 stuck for 61s! [modprobe:706]
Nov 26 15:58:34 livecd kernel: [ 2496.452324] Modules linked in: dm_crypt snd_hda_codec_nvhdmi snd_hda_codec_realtek nfs lockd nfs_acl auth_rpcgss sunrpc lirc_mceusb snd_usb_audio(+) snd_usbmidi_lib snd_hda_intel snd_hda_codec snd_hwdep $
Nov 26 15:58:34 livecd kernel: [ 2496.452334]
Nov 26 15:58:34 livecd kernel: [ 2496.452334] Pid: 706, comm: modprobe Tainted: P           (2.6.32-25-generic #45-Ubuntu) System Product Name
Nov 26 15:58:34 livecd kernel: [ 2496.452334] EIP: 0060:[<f8658ac0>] EFLAGS: 00000297 CPU: 1
Nov 26 15:58:34 livecd kernel: [ 2496.452334] EIP is at snd_usb_find_desc+0x0/0x70 [snd_usb_audio]
Nov 26 15:58:34 livecd kernel: [ 2496.452334] EAX: f70e1c12 EBX: f59ddd78 ECX: f70e1c34 EDX: 000000c8
Nov 26 15:58:34 livecd kernel: [ 2496.452334] ESI: 00000009 EDI: f59ddcd4 EBP: f59ddc4c ESP: f59ddc3c
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Nov 26 15:58:34 livecd kernel: [ 2496.452334] CR0: 8005003b CR2: 00384820 CR3: 35947000 CR4: 000006d0
Nov 26 15:58:34 livecd kernel: [ 2496.452334] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Nov 26 15:58:34 livecd kernel: [ 2496.452334] DR6: ffff0ff0 DR7: 00000400
Nov 26 15:58:34 livecd kernel: [ 2496.452334] Call Trace:
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<f864fe3a>] ? find_audio_control_unit+0x2a/0x70 [snd_usb_audio]
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<f864fead>] check_input_term+0x2d/0x240 [snd_usb_audio]
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<f8651c84>] parse_audio_unit+0x5d4/0xce0 [snd_usb_audio]
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c034c57a>] ? idr_get_empty_slot+0x9a/0x130
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<f8651802>] parse_audio_unit+0x152/0xce0 [snd_usb_audio]
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c02605e4>] ? __sysfs_add_one+0x24/0xc0
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c021ccb5>] ? iput+0x25/0x60
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c058fa53>] ? notifier_call_chain+0x43/0x60
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<f8652418>] ? snd_usb_create_mixer+0x88/0x370 [snd_usb_audio]
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<f86524fa>] snd_usb_create_mixer+0x16a/0x370 [snd_usb_audio]
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<f864f637>] usb_audio_probe+0x227/0x7b0 [snd_usb_audio]
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c044ba80>] usb_probe_interface+0xc0/0x180
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c0260be7>] ? sysfs_create_link+0x17/0x20
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c03e7e9d>] really_probe+0x4d/0x140
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c03ee7ae>] ? pm_runtime_barrier+0x4e/0xc0
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c03e7fcc>] driver_probe_device+0x3c/0x60
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c03e8071>] __driver_attach+0x81/0x90
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c03e74b3>] bus_for_each_dev+0x53/0x80
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c03e7d6e>] driver_attach+0x1e/0x20
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c03e7ff0>] ? __driver_attach+0x0/0x90
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c03e7735>] bus_add_driver+0xd5/0x280
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c03e836a>] driver_register+0x6a/0x130
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c044b821>] usb_register_driver+0x81/0xf0
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c01a78b7>] ? tracepoint_module_notify+0x27/0x30
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c058fa53>] ? notifier_call_chain+0x43/0x60
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<f855903a>] snd_usb_audio_init+0x3a/0x3c [snd_usb_audio]
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c016cd14>] ? __blocking_notifier_call_chain+0x54/0x70
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c0101131>] do_one_initcall+0x31/0x190
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<f8559000>] ? snd_usb_audio_init+0x0/0x3c [snd_usb_audio]
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c01826b0>] sys_init_module+0xb0/0x210
Nov 26 15:58:34 livecd kernel: [ 2496.452334]  [<c01033ec>] syscall_call+0x7/0xb
```

I've never dealt with something like this, and I don't know what to do with the output.  How can I get this working?

---

### Post by solarbird on 2011-12-12
Not just your card. Also on TASCAM US-800. Appears related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576496](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576496)

Here is a very similar callstack fail on completely different hardware. (This is actually the entire boot-to-crash log but you can see the issues.) The NOACPI workaround does NOT solve this problem, sadly.

---

### Post by solarbird on 2011-12-12
Well, I _tried_ to attach, and it just dumped spew. The log from connection of device on down is below. Full log here:

[http://solarbird.net/Livejournal/2011-12/gotcha.log](http://solarbird.net/Livejournal/2011-12/gotcha.log)

---

### Post by solarbird on 2011-12-12
```
Dec 12 15:41:29 kahvi kernel: [ 1367.444521] usb 1-1: new high speed USB device using ehci_hcd and address 2
Dec 12 15:41:29 kahvi kernel: [ 1367.576421] usb 1-1: config 1 interface 4 altsetting 0 bulk endpoint 0x4 has invalid maxpacket 64
Dec 12 15:41:29 kahvi kernel: [ 1367.576428] usb 1-1: config 1 interface 4 altsetting 0 bulk endpoint 0x85 has invalid maxpacket 64
Dec 12 15:41:29 kahvi kernel: [ 1367.576922] usb 1-1: configuration #1 chosen from 1 choice
Dec 12 15:42:01 kahvi kernel: [ 1400.000017] ata3: lost interrupt (Status 0x58)
Dec 12 15:42:01 kahvi kernel: [ 1400.004008] ata3: drained 32768 bytes to clear DRQ.
Dec 12 15:42:01 kahvi kernel: [ 1400.043839] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec 12 15:42:01 kahvi kernel: [ 1400.046519] sr 2:0:1:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Dec 12 15:42:01 kahvi kernel: [ 1400.046538] ata3.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Dec 12 15:42:01 kahvi kernel: [ 1400.046540]          res 40/00:02:00:08:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Dec 12 15:42:01 kahvi kernel: [ 1400.051836] ata3.01: status: { DRDY }
Dec 12 15:42:01 kahvi kernel: [ 1400.054467] ata3: soft resetting link
Dec 12 15:42:02 kahvi kernel: [ 1400.240750] ata3.01: configured for UDMA/100
Dec 12 15:42:02 kahvi kernel: [ 1400.241290] ata3: EH complete
Dec 12 15:42:34 kahvi kernel: [ 1432.372000] BUG: soft lockup - CPU#0 stuck for 61s! [khubd:29]
Dec 12 15:42:34 kahvi kernel: [ 1432.373308] Modules linked in: binfmt_misc snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_usb_audio snd_pcm_oss snd_mixer_oss fbcon tileblit font bitblit softcursor snd_pcm vga16fb vgastate snd_seq_dummy snd_seq_oss snd_hwdep snd_usbmidi_lib snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_timer snd_seq_device ppdev i915 drm_kms_helper parport_pc drm snd psmouse serio_raw lp pcspkr atl1c intel_agp soundcore snd_page_alloc i2c_algo_bit video output agpgart parport floppy
Dec 12 15:42:34 kahvi kernel: [ 1432.373308] 
Dec 12 15:42:34 kahvi kernel: [ 1432.373308] Pid: 29, comm: khubd Not tainted (2.6.32-35-generic #78-Ubuntu) G31M-ES2L
Dec 12 15:42:34 kahvi kernel: [ 1432.373308] EIP: 0060:[<f81deb21>] EFLAGS: 00000292 CPU: 0
Dec 12 15:42:34 kahvi kernel: [ 1432.373308] EIP is at snd_usb_find_desc+0x61/0x70 [snd_usb_audio]
Dec 12 15:42:34 kahvi kernel: [ 1432.373308] EAX: f3ffa43c EBX: f3ffa44d ECX: 00000024 EDX: f3ffa51b
Dec 12 15:42:34 kahvi kernel: [ 1432.373308] ESI: 00000024 EDI: f3ffa44d EBP: f71b5a4c ESP: f71b5a40
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Dec 12 15:42:34 kahvi kernel: [ 1432.373308] CR0: 8005003b CR2: 21dcb97c CR3: 34bbb000 CR4: 000006d0
Dec 12 15:42:34 kahvi kernel: [ 1432.373308] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Dec 12 15:42:34 kahvi kernel: [ 1432.373308] DR6: ffff0ff0 DR7: 00000400
Dec 12 15:42:34 kahvi kernel: [ 1432.373308] Call Trace:
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<f81d5e3a>] find_audio_control_unit+0x2a/0x70 [snd_usb_audio]
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<f81d5ead>] check_input_term+0x2d/0x240 [snd_usb_audio]
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<f81d7c84>] parse_audio_unit+0x5d4/0xce0 [snd_usb_audio]
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c015be60>] ? process_timeout+0x0/0x10
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<f81d5e3a>] ? find_audio_control_unit+0x2a/0x70 [snd_usb_audio]
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<f81d7c69>] parse_audio_unit+0x5b9/0xce0 [snd_usb_audio]
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c034f87d>] ? kref_put+0x2d/0x60
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c0449de6>] ? usb_free_urb+0x16/0x20
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<f81d84fa>] snd_usb_create_mixer+0x16a/0x370 [snd_usb_audio]
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c0300c22>] ? selinux_inode_mknod+0x22/0x80
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<f81d5637>] usb_audio_probe+0x227/0x7b0 [snd_usb_audio]
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c044d990>] usb_probe_interface+0xc0/0x180
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c02627a7>] ? sysfs_create_link+0x17/0x20
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e9cad>] really_probe+0x4d/0x140
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03f05be>] ? pm_runtime_barrier+0x4e/0xc0
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e9ddc>] driver_probe_device+0x3c/0x60
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e9ed9>] __device_attach+0x49/0x60
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e9003>] bus_for_each_drv+0x53/0x80
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e9fa2>] device_attach+0x72/0x90
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e9e90>] ? __device_attach+0x0/0x60
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e8e45>] bus_probe_device+0x25/0x40
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e78c4>] device_add+0x274/0x430
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c034ed44>] ? kobject_set_name_vargs+0x64/0x70
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c044c2af>] usb_set_configuration+0x41f/0x6a0
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c0454cae>] generic_probe+0x3e/0xb0
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c02627a7>] ? sysfs_create_link+0x17/0x20
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c044c5e4>] usb_probe_device+0x24/0x30
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e9cad>] really_probe+0x4d/0x140
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03f05be>] ? pm_runtime_barrier+0x4e/0xc0
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e9ddc>] driver_probe_device+0x3c/0x60
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e9ed9>] __device_attach+0x49/0x60
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e9003>] bus_for_each_drv+0x53/0x80
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e9fa2>] device_attach+0x72/0x90
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e9e90>] ? __device_attach+0x0/0x60
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e8e45>] bus_probe_device+0x25/0x40
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c03e78c4>] device_add+0x274/0x430
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c0444f6d>] usb_new_device+0x5d/0xc0
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c0445adf>] hub_port_connect_change+0x53f/0x890
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c0443208>] ? hub_port_status+0xb8/0x110
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c04465d5>] hub_events+0x1f5/0x510
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c01687ff>] ? finish_wait+0x4f/0x70
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c044692a>] hub_thread+0x3a/0x140
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c0168690>] ? autoremove_wake_function+0x0/0x50
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c04468f0>] ? hub_thread+0x0/0x140
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c0168404>] kthread+0x74/0x80
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c0168390>] ? kthread+0x0/0x80
Dec 12 15:42:34 kahvi kernel: [ 1432.373308]  [<c0104087>] kernel_thread_helper+0x7/0x10
```

---

### Post by solarbird on 2011-12-13
OKAY! I got it to work!

So this can be found in google: US-800 US800 TASCAM LINUX UBUNTU :D

Okay, so:

Plug the US-800 into an OSX machine, and run the included software right off CD-ROM (you don't have to install it and there are no drivers) to reset the device to factory. You can also do this on a Windows machine, but that involves installing drivers, so borrow a Macbook or something.

Even after that, plugging it in will crash many variants of the 2.6 kernel. HOWEVER! You can upgrade Linux kernels without upgrading the entire GNU/Linux OS. Directions for Ubuntu are here: [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds) Upgrade to version 3.1.5-generic, and restart the machine.

Plug the US-800 into an open USB port. There will be MANY complaints in syslog. That's… marginally okay. Better than crashing, anyway. We'll fix it below.

Launch JackAudio. Go into settings panel, create a new config, based on current actual configuration. THE RESULT WILL BE WRONG, but we'll fix it.

On the lower right there will be dropdowns for numbers of inputs and outputs. It will probably default to either 2/2 or automatic/automatic. This is wrong. Set those manually to 8/2.

Save those changes, then stop and restart JackAudio. This is ALSO important because I think we're either working around an ALSA device scanner bug where it gets the numbers of inputs wrong, or the hardware is buggy and Windows and OSX patch around it. One of those.

Go back into Jack settings, and on the lower right, near the number-of-inputs selectors, there will be physical device selectors for both input and output. Do NOT pick plughw, even tho' that should totally work. Click on the little down wedge icon that brings up the physical device names, and select “us800” for both inputs and outputs.

Save changes, stop and restart the server. You should now have at least all six analogue inputs, and both outputs, at least in things that talk to JackAudio. I can't validate the digital inputs because I lack the hardware.

I haven't tested multiple bitrates and other changes yet. But I had it working at 44.1Khz and the selector at least shows the other bitrate options and lets me pick them. :D

---

