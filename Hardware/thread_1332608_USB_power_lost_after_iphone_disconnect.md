---
title: "USB power lost after iphone disconnect"
date: 2009-11-20
forum: Hardware
---

### Post by ilyail3 on 2009-11-20
I saldom use my computer(LG's x110, a nettop) to charge my iphone.

Since I install 9.10, every time after I disconnect the device from my nettop , the nettop stops responding to any usb devices (the usb port simple power down , no power reaches connected devices), like the usb daemon crashes , I have no idea what this daemon is , so I cannot check this theory, however, I've checked similar thread that suggest checking system massages and lshal --monitor, both show no event what's so ever, not on disconnect, not on my attempts to connect any further device , any ideas?

---

### Post by ilyail3 on 2009-11-20
I've tried to collect more information to debug by, and found an interesting(and maybe helpful thing), this only happens if the device is connected on computer startup.

those several lines taken of /var/log/messages and lshal --monitor

```
on device connect

messages

Nov 20 21:32:37 ilya-mini kernel: [  188.796166] usb 1-3: new high speed USB device using ehci_hcd and address 4
Nov 20 21:32:38 ilya-mini kernel: [  188.936464] usb 1-3: configuration #1 chosen from 4 choices

lshal --monitor

21:32:38.191: usb_device_5ac_1294_f0d896758a2925e14f60660bf7bc259096016283 added
21:32:38.206: usb_device_ffffffff_ffffffff_noserial added
21:32:38.206: usb_device_ffffffff_ffffffff_noserial removed
21:32:38.218: usb_device_5ac_1294_f0d896758a2925e14f60660bf7bc259096016283_if1 added
21:32:38.218: usb_device_5ac_1294_f0d896758a2925e14f60660bf7bc259096016283_if0 added
21:32:38.219: usb_device_5ac_1294_f0d896758a2925e14f60660bf7bc259096016283_if2 added

after disconnect

messages

Nov 20 21:34:12 ilya-mini kernel: [  283.653389] usb 1-3: USB disconnect, address 4

lshal --monitor

21:34:12.827: usb_device_5ac_1294_f0d896758a2925e14f60660bf7bc259096016283 removed

```

So , if it's a boot related messages , dmsg with a strange error is provided

```
[    2.066337] [drm] Initialized drm 1.1.0 20060810
[    2.087924] usb 1-5: configuration #1 chosen from 1 choice
[    2.099405] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.099420] i915 0000:00:02.0: setting latency timer to 64
[    2.205858] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 59
[    2.205866] [drm:edid_is_valid] *ERROR* Raw EDID:
[    2.205874] <3>00 ff ff ff ff ff ff 00 22 64 e9 03 44 f5 02 00  ........"d..D...
[    2.205880] <3>12 12 01 03 80 16 0d 78 0a 80 36 9a 5e 5d 91 28  .......x..6.^].(
[    2.205886] <3>20 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01   OT.............
[    2.205892] <3>01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23  ..........@X. 5#
[    2.205898] <3>45 00 dc 81 00 00 00 19 00 00 00 fd 00 37 41 22  E............7A"
[    2.205904] <3>29 05 00 0a 20 20 20 20 20 20 00 00 00 fc 00 48  )...      .....H
[    2.205910] <3>53 44 31 30 30 49 46 57 31 0a 20 20 00 00 00 10  SD100IFW1.  ....
[    2.205916] <3>00 0a 20 20 20 20 20 20 20 20 20 20 20 20 00 81  ..            ..
[    2.205920] 
[    2.205926] i915 0000:00:02.0: LVDS-1: EDID invalid.
[    2.245056] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    2.327524] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 59
[    2.327532] [drm:edid_is_valid] *ERROR* Raw EDID:
[    2.327540] <3>00 ff ff ff ff ff ff 00 22 64 e9 03 44 f5 02 00  ........"d..D...
[    2.327546] <3>12 12 01 03 80 16 0d 78 0a 80 36 9a 5e 5d 91 28  .......x..6.^].(
[    2.327552] <3>20 4f 54 00 00 00 01 01 01 01 01 01 01 01 01 01   OT.............
[    2.327558] <3>01 01 01 01 01 01 94 11 00 b0 40 58 19 20 35 23  ..........@X. 5#
[    2.327564] <3>45 00 dc 81 00 00 00 19 00 00 00 fd 00 37 41 22  E............7A"
[    2.327570] <3>29 05 00 0a 20 20 20 20 20 20 00 00 00 fc 00 48  )...      .....H
[    2.327576] <3>53 44 31 30 30 49 46 57 31 0a 20 20 00 00 00 10  SD100IFW1.  ....
[    2.327582] <3>00 0a 20 20 20 20 20 20 20 20 20 20 20 20 00 81  ..            ..
[    2.327586] 
[    2.327592] i915 0000:00:02.0: LVDS-1: EDID invalid.
[    2.332941] [drm] fb0: inteldrmfb frame buffer device
[    2.332963] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.391292] usb 1-6: configuration #1 chosen from 1 choice
[    2.416138] Initializing USB Mass Storage driver...
[    2.416405] scsi2 : SCSI emulation for USB Mass Storage devices
[    2.416596] usbcore: registered new interface driver usb-storage
[    2.416604] USB Mass Storage support registered.
[    2.416789] usb-storage: device found at 3
[    2.416793] usb-storage: waiting for device to settle before scanning
[    2.659334] [drm] LVDS-8: set mode 1024x600 d
[    3.104079] Console: switching to colour frame buffer device 128x37
[    7.412552] usb-storage: device scan complete
[    7.414700] scsi 2:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    7.416070] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    7.423199] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    8.774050] EXT4-fs (sda1): barriers enabled
[    8.854520] kjournald2 starting: pid 442, dev sda1:8, commit interval 5 seconds
```

I think I have an msi motherboard.
what's that error? should I worry about it?

---

### Post by blur xc on 2009-11-20
Ok- I don't know what any of that mumbo jumbo is, but my 9.04 machine will do this whenever I unplug a usb device w/o unmounting first.  We have a few handheld devices that didn't come w/ wall chargers, only usb cables and the kids plug them in the charge them, they are automounted, and when they are done the kids just yank the usb cable.

My problem is that  I use a usb wireless keyboard  and mouse.  For the time that I'm logged in to my user, the keyboard and mouse stay responsive.  But one time, I had the idea to log out- and log back in to maybe revive the usb ports, but once logged out I lost my keyboard and mouse.  My only option I had left was to do a hard reset.  Maybe a PS/2 keyboard would have worked, I don't know.

I've not been in any hurry to replicate the results, but maybe I'll find out today.  My duaghter yanked her disney mix-max this morning before I could stop her, so we'll see...

BM

---

