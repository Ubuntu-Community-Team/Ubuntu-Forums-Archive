---
title: "External USB Issues"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by nanoga on 2007-04-06
Hey there.

Ever since I installed Kubuntu, I´ve had some problems with my USB connections.  Whenever I power on my external, dmesg shows something along the lines of:

```
Apr  6 10:54:22 Icepick kernel: [  968.142511] usb 2-2: new high speed USB device using ehci_hcd and address 9
Apr  6 10:54:33 Icepick kernel: [  979.473010] usb 2-2: configuration #1 chosen from 1 choice
Apr  6 10:54:33 Icepick kernel: [  979.473392] scsi5 : SCSI emulation for USB Mass Storage devices
Apr  6 10:54:38 Icepick kernel: [  984.476889]   Vendor: ST316002  Model: 3A                Rev: 0811
Apr  6 10:54:38 Icepick kernel: [  984.476896]   Type:   Direct-Access                      ANSI SCSI revision: 00
Apr  6 10:54:51 Icepick kernel: [  997.276901] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Apr  6 10:54:51 Icepick kernel: [  997.276905] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Apr  6 10:54:52 Icepick kernel: [  998.008602] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
Apr  6 10:54:52 Icepick kernel: [  998.008606] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
Apr  6 10:55:08 Icepick kernel: [ 1014.572556] usb 2-2: reset high speed USB device using ehci_hcd and address 9
Apr  6 10:55:13 Icepick kernel: [ 1019.701430] usb 2-2: device firmware changed
Apr  6 10:55:13 Icepick kernel: [ 1019.701453] usb 2-2: USB disconnect, address 9
Apr  6 10:55:13 Icepick kernel: [ 1019.701522] PGD a2805067 PUD a8c64067 PMD 0
Apr  6 10:55:13 Icepick kernel: [ 1019.701527] CPU 0
Apr  6 10:55:13 Icepick kernel: [ 1019.701529] Modules linked in: sg sd_mod usb_storage libusual rfcomm l2cap bluetooth ipv6 video tc1100_wmi sbs sony_acpi pcc_acpi i2c_ec hotkey dev_acpi button battery container ac asus_acpi ext2 sbp2 lp af_packet snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_emu10k1 snd_ac97_codec snd_ac97_bus snd_util_mem snd_hwdep snd_pcm_oss snd_pcm snd_page_alloc snd_mixer_oss tsdev snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq nvidia usblp snd_timer snd_seq_device snd soundcore i2c_nforce2 parport_pc parport psmouse i2c_core pcspkr serio_raw evdev floppy shpchp pci_hotplug usbhid ext3 jbd ohci1394 ieee1394 forcedeth ehci_hcd ohci_hcd usbcore ide_generic ide_cd cdrom ide_disk generic amd74xx sata_nv libata scsi_mod thermal processor fan vesafb capability commoncap vga16fb cfbcopyarea vgastate cfbimgblt cfbfillrect fbcon tileblit font bitblit softcursor
Apr  6 10:55:13 Icepick kernel: [ 1019.701564] Pid: 1841, comm: khubd Tainted: P      2.6.17-11-generic #2
Apr  6 10:55:13 Icepick kernel: [ 1019.701567] RIP: 0010:[strlen+2/32] <ffffffff80334212>{strlen+2}
Apr  6 10:55:13 Icepick kernel: [ 1019.701572] RSP: 0018:ffff8100bbf45c40  EFLAGS: 00010246
Apr  6 10:55:13 Icepick kernel: [ 1019.701574] RAX: 0000000000000000 RBX: ffffffff880780d0 RCX: 0000000000000002
Apr  6 10:55:13 Icepick kernel: [ 1019.701577] RDX: ffffffff8897fa80 RSI: ffffffff88988e80 RDI: 0000000000000000
Apr  6 10:55:13 Icepick kernel: [ 1019.701580] RBP: ffff8100a6eafb28 R08: 0000000000000000 R09: 0000000000000001
Apr  6 10:55:13 Icepick kernel: [ 1019.701583] R10: 0000000000000000 R11: ffffffff803928b0 R12: ffffffff880780d0
Apr  6 10:55:13 Icepick kernel: [ 1019.701586] R13: ffff8100a6eafb38 R14: ffffffff88078000 R15: 0000000000000000
Apr  6 10:55:13 Icepick kernel: [ 1019.701590] FS:  0000000043007950(0000) GS:ffffffff805f3000(0000) knlGS:00000000f719d980
Apr  6 10:55:13 Icepick kernel: [ 1019.701593] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Apr  6 10:55:13 Icepick kernel: [ 1019.701595] CR2: 0000000000000000 CR3: 00000000accc5000 CR4: 00000000000006e0
Apr  6 10:55:13 Icepick kernel: [ 1019.701599] Process khubd (pid: 1841, threadinfo ffff8100bbf44000, task ffff810037dfb790)
Apr  6 10:55:13 Icepick kernel: [ 1019.701601] Stack: ffffffff80394272 ffffffff880780e0 ffffffff880780d0 ffff8100a6eafb28
Apr  6 10:55:13 Icepick kernel: [ 1019.701607]        ffffffff8039454b 0000000000000000 ffff8100a6eafb28 ffff8100a6eaf8e8
Apr  6 10:55:13 Icepick kernel: [ 1019.701612]        0000000000000246 ffff8100bbc87820
Apr  6 10:55:13 Icepick kernel: [ 1019.701615] Call Trace: <ffffffff80394272>{make_class_name+18} <ffffffff8039454b>{class_device_del+187}
Apr  6 10:55:13 Icepick kernel: [ 1019.701631]        <ffffffff80394669>{class_device_unregister+9} <ffffffff88057bb2>{:scsi_mod:__scsi_remove_device+50}
Apr  6 10:55:13 Icepick kernel: [ 1019.701662]        <ffffffff88054edd>{:scsi_mod:scsi_forget_host+77} <ffffffff8804ee3c>{:scsi_mod:scsi_remove_host+124}
Apr  6 10:55:13 Icepick kernel: [ 1019.701693]        <ffffffff88961ec0>{:usb_storage:storage_disconnect+16}
Apr  6 10:55:13 Icepick kernel: [ 1019.701705]        <ffffffff880c8fa5>{:usbcore:usb_unbind_interface+69}
Apr  6 10:55:13 Icepick kernel: [ 1019.701729]        <ffffffff80393667>{__device_release_driver+135} <ffffffff803939e3>{device_release_driver+51}
Apr  6 10:55:13 Icepick kernel: [ 1019.701738]        <ffffffff80392d82>{bus_remove_device+146} <ffffffff80391bb6>{device_del+70}
Apr  6 10:55:13 Icepick kernel: [ 1019.701747]        <ffffffff880c700f>{:usbcore:usb_disable_device+143}
Apr  6 10:55:13 Icepick kernel: [ 1019.701764]        <ffffffff880c2b5b>{:usbcore:usb_disconnect+171} <ffffffff880c3dca>{:usbcore:hub_thread+1130}
Apr  6 10:55:13 Icepick kernel: [ 1019.701802]        <ffffffff802a3ad0>{autoremove_wake_function+0} <ffffffff880c3960>{:usbcore:hub_thread+0}
Apr  6 10:55:13 Icepick kernel: [ 1019.701824]        <ffffffff802a3880>{keventd_create_kthread+0} <ffffffff80235459>{kthread+217}
Apr  6 10:55:13 Icepick kernel: [ 1019.701834]        <ffffffff80266622>{child_rip+8} <ffffffff802a3880>{keventd_create_kthread+0}
Apr  6 10:55:13 Icepick kernel: [ 1019.701846]        <ffffffff80235380>{kthread+0} <ffffffff8026661a>{child_rip+0}
Apr  6 10:55:13 Icepick kernel: [ 1019.701854]
Apr  6 10:55:13 Icepick kernel: [ 1019.701855] Code: 80 3f 00 74 15 48 89 f8 66 66 90 66 66 90 48 83 c0 01 80 38
Apr  6 10:55:13 Icepick kernel: [ 1019.701869]  <6>sd 5:0:0:0: scsi: Device offlined - not ready after error recovery
Apr  6 10:55:13 Icepick kernel: [ 1019.708590] sda : READ CAPACITY failed.
Apr  6 10:55:13 Icepick kernel: [ 1019.708592] sda : status=0, message=00, host=1, driver=00
Apr  6 10:55:13 Icepick kernel: [ 1019.708595] sda : sense not available.
Apr  6 10:55:13 Icepick kernel: [ 1019.708942] sda: Write Protect is off
Apr  6 10:55:13 Icepick kernel: [ 1019.709001] sd 5:0:0:0: Attached scsi disk sda
Apr  6 10:55:13 Icepick kernel: [ 1019.709042] sd 5:0:0:0: Attached scsi generic sg0 type 0
```

Before I attach it, lsusb shows:
Bus 001 Device 002: ID 413c:5109 Dell Computer Corp.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

But afterwords it only seems to freeze.

Any thoughts or suggestions?

---

### Post by kidders on 2007-04-07
Ewww... this is nasty. :-(

It looks as though **khubd** (part of the kernel's USB subsystem, responsible for device configuration) is crashing. I'm not intimately familiar with the exact processes involved in probing USB devices, so I'm afraid I can't be much more precise without guessing.

This sort of thing is unusual, and most often points to a hardware fault. Other possibilities include a highly hardware-specific flaw in the Linux kernel, or a combination of both problems, where previous kernel versions may have been able to handle the hardware problem more gracefully than your current one.

My suggestions:

[LIST]
[*]Take a wander through kernel.org's & (K)ubuntu's bug databases for similar issues. The code that's apparently causing your problem is in /drivers/usb/core/hub.c (part of the source code of your kernel).
[*]Normally, I would suggest downgrading to the last kernel version that *didn't* exhibit this issue, but your post seems to suggest it's always been happening. :-(
[*]*Upgrade* to the most recent kernel release. If the problem still occurs, you might consider filing a bug report. Doing so would give you access to people who *realllly* know their stuff when it comes to USB issues, and (if you have indeed found a bug) could lead to a fix ... something which the entire Linux community would thank you for.[/LIST]Beyond that, try to eliminate hardware issues, perhaps by using different cables, powering on your device *before* connecting it, or trying a different USB controller (ie not just the other port on the same controller).

Your system _appears_ to recover from the failure properly, so you shouldn't experience any major problems after it. Even so, it is still worth bearing in mind that, in general, odd things can happen as a result of a low-level error such as this. Keep an eye out in your logs for phrases such as "oops" or "reboot needed".

---

### Post by nanoga on 2007-04-07
I've been experimenting with the results of dmesg after several different reboots.  The behavior seems to be one of the following.

[LIST]
[*]It just works (and I don't know why)
[*]It would appear from dmesg that it's working, but no sd* devices show up in /dev, and no prompts from kde about what to do with newly attached hardware
[*]It definitely doesn't work, and dmesg shows the device continually receiving new addresses
[*]It doesn't work, dmesg shows it receiving a couple new addresses, and the blurts out the error message.
[/LIST]

I'm home for the weekend and the computers at school, so I can't try different power on timings, but is there anything you could think of that might cause it to sometimes work?

---

### Post by kidders on 2007-04-08
Yeah, that can happen. Sometimes, the cause is down to the order in which you plug things in. A kernel module loaded as a result of connecting one USB device can upset others. Another common cause of intermittent problems is faulty cabling.

---

