---
title: "[SOLVED] my log is overflowing with &amp;quot;new high speed USB device using ehci_hcd and add"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by MountainX on 2008-03-26
Any ideas why I would continually get these messages?

```
[   31.678656] usb 1-4: configuration #1 chosen from 1 choice
[   31.927177] usb 2-9: new high speed USB device using ehci_hcd and address 6
[   31.987418] usbcore: registered new interface driver hiddev
[   31.993494] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input1
[   32.008132] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.0-2
[   32.025435] input: P.I. Engineering PC Keyboard/Mouse to USB  Adapter as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input2
[   32.044090] input,hidraw1: USB HID v1.00 Keyboard [P.I. Engineering PC Keyboard/Mouse to USB  Adapter] on usb-0000:00:02.0-3
[   32.075385] input: P.I. Engineering PC Keyboard/Mouse to USB  Adapter as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.1/input/input3
[   32.084069] input,hidraw2: USB HID v1.00 Mouse [P.I. Engineering PC Keyboard/Mouse to USB  Adapter] on usb-0000:00:02.0-3
[   32.095377] input: Contour Design RollerMouse Pro as /devices/pci0000:00/0000:00:02.0/usb1/1-4/1-4:1.0/input/input4
[   32.112042] input,hidraw3: USB HID v1.10 Mouse [Contour Design RollerMouse Pro] on usb-0000:00:02.0-4
[   32.112051] usbcore: registered new interface driver usbhid
[   32.112054] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   32.258913] usb 2-9: new high speed USB device using ehci_hcd and address 7
[   32.590644] usb 2-9: new high speed USB device using ehci_hcd and address 8
[   32.922379] usb 2-9: new high speed USB device using ehci_hcd and address 9
[   33.254114] usb 2-9: new high speed USB device using ehci_hcd and address 10
[   33.585849] usb 2-9: new high speed USB device using ehci_hcd and address 11
[   33.917585] usb 2-9: new high speed USB device using ehci_hcd and address 12
[   34.253317] usb 2-9: new high speed USB device using ehci_hcd and address 13
[   34.589049] usb 2-9: new high speed USB device using ehci_hcd and address 14
[   34.924781] usb 2-9: new high speed USB device using ehci_hcd and address 15
[   35.260513] usb 2-9: new high speed USB device using ehci_hcd and address 16
[   35.596245] usb 2-9: new high speed USB device using ehci_hcd and address 17
[   35.931977] usb 2-9: new high speed USB device using ehci_hcd and address 18
[   36.267709] usb 2-9: new high speed USB device using ehci_hcd and address 19
[   36.603441] usb 2-9: new high speed USB device using ehci_hcd and address 20
[   36.939173] usb 2-9: new high speed USB device using ehci_hcd and address 21
[   37.274905] usb 2-9: new high speed USB device using ehci_hcd and address 22
[   37.610637] usb 2-9: new high speed USB device using ehci_hcd and address 23
[   37.946369] usb 2-9: new high speed USB device using ehci_hcd and address 24
[   38.282101] usb 2-9: new high speed USB device using ehci_hcd and address 25
[   38.617833] usb 2-9: new high speed USB device using ehci_hcd and address 26
[   38.953565] usb 2-9: new high speed USB device using ehci_hcd and address 27
[   39.289297] usb 2-9: new high speed USB device using ehci_hcd and address 28
[   39.625028] usb 2-9: new high speed USB device using ehci_hcd and address 29
[   39.961753] usb 2-9: new high speed USB device using ehci_hcd and address 30
[   40.296493] usb 2-9: new high speed USB device using ehci_hcd and address 31
[   40.632225] usb 2-9: new high speed USB device using ehci_hcd and address 32
[   40.967957] usb 2-9: new high speed USB device using ehci_hcd and address 33
[   41.303689] usb 2-9: new high speed USB device using ehci_hcd and address 34
[   41.635424] usb 2-9: new high speed USB device using ehci_hcd and address 35
[   41.967160] usb 2-9: new high speed USB device using ehci_hcd and address 36
[   42.298894] usb 2-9: new high speed USB device using ehci_hcd and address 37
[   42.630629] usb 2-9: new high speed USB device using ehci_hcd and address 38
[   42.962360] usb 2-9: new high speed USB device using ehci_hcd and address 39
[   43.294100] usb 2-9: new high speed USB device using ehci_hcd and address 40
[   43.625835] usb 2-9: new high speed USB device using ehci_hcd and address 41
[   43.958562] usb 2-9: new high speed USB device using ehci_hcd and address 42
[   44.293302] usb 2-9: new high speed USB device using ehci_hcd and address 43
[   44.625037] usb 2-9: new high speed USB device using ehci_hcd and address 44
[   44.956772] usb 2-9: new high speed USB device using ehci_hcd and address 45
[   45.288507] usb 2-9: new high speed USB device using ehci_hcd and address 46
[   45.620242] usb 2-9: new high speed USB device using ehci_hcd and address 47
[   45.951979] usb 2-9: new high speed USB device using ehci_hcd and address 48
[   46.283713] usb 2-9: new high speed USB device using ehci_hcd and address 49
[   46.615448] usb 2-9: new high speed USB device using ehci_hcd and address 50
[   46.947183] usb 2-9: new high speed USB device using ehci_hcd and address 51
[   47.278918] usb 2-9: new high speed USB device using ehci_hcd and address 52
[   47.610654] usb 2-9: new high speed USB device using ehci_hcd and address 53
[   47.942389] usb 2-9: new high speed USB device using ehci_hcd and address 54
[   48.274126] usb 2-9: new high speed USB device using ehci_hcd and address 55
[   48.605859] usb 2-9: new high speed USB device using ehci_hcd and address 56
[   48.937594] usb 2-9: new high speed USB device using ehci_hcd and address 57
[   49.269330] usb 2-9: new high speed USB device using ehci_hcd and address 58
[   49.601065] usb 2-9: new high speed USB device using ehci_hcd and address 59
[   49.932815] usb 2-9: new high speed USB device using ehci_hcd and address 60
[   50.264535] usb 2-9: new high speed USB device using ehci_hcd and address 61
[   50.596270] usb 2-9: new high speed USB device using ehci_hcd and address 62
[   50.928005] usb 2-9: new high speed USB device using ehci_hcd and address 63
[   51.259741] usb 2-9: new high speed USB device using ehci_hcd and address 64
[   51.591475] usb 2-9: new high speed USB device using ehci_hcd and address 65
[   51.899230] usb 2-9: new high speed USB device using ehci_hcd and address 66
[   52.234962] usb 2-9: new high speed USB device using ehci_hcd and address 67
[   52.570694] usb 2-9: new high speed USB device using ehci_hcd and address 68
[   52.906426] usb 2-9: new high speed USB device using ehci_hcd and address 69
[   53.242158] usb 2-9: new high speed USB device using ehci_hcd and address 70
[   53.577890] usb 2-9: new high speed USB device using ehci_hcd and address 71
[   53.913622] usb 2-9: new high speed USB device using ehci_hcd and address 72
[   54.249354] usb 2-9: new high speed USB device using ehci_hcd and address 73
[   54.585086] usb 2-9: new high speed USB device using ehci_hcd and address 74
[   54.920818] usb 2-9: new high speed USB device using ehci_hcd and address 75
[   55.256550] usb 2-9: new high speed USB device using ehci_hcd and address 76
[   55.564304] usb 2-9: new high speed USB device using ehci_hcd and address 77
[   55.900034] usb 2-9: new high speed USB device using ehci_hcd and address 78
[   56.235765] usb 2-9: new high speed USB device using ehci_hcd and address 79
[   56.571498] usb 2-9: new high speed USB device using ehci_hcd and address 80
[   56.907231] usb 2-9: new high speed USB device using ehci_hcd and address 81
[   57.242964] usb 2-9: new high speed USB device using ehci_hcd and address 82
[   57.578695] usb 2-9: new high speed USB device using ehci_hcd and address 83
[   57.914428] usb 2-9: new high speed USB device using ehci_hcd and address 84
[   58.250158] usb 2-9: new high speed USB device using ehci_hcd and address 85
[   58.585892] usb 2-9: new high speed USB device using ehci_hcd and address 86
[   58.921624] usb 2-9: new high speed USB device using ehci_hcd and address 87
[   59.253359] usb 2-9: new high speed USB device using ehci_hcd and address 88
[   59.585094] usb 2-9: new high speed USB device using ehci_hcd and address 89
[   59.925814] usb 2-9: new high speed USB device using ehci_hcd and address 90
[   60.261546] usb 2-9: new high speed USB device using ehci_hcd and address 91
[   60.597279] usb 2-9: new high speed USB device using ehci_hcd and address 92
[   60.828881] padlock: VIA PadLock Hash Engine not detected.
[   60.933037] usb 2-9: new high speed USB device using ehci_hcd and address 93
[   61.158504] Attempting manual resume
[   61.158508] swsusp: Resume From Partition 254:1
[   61.158510] PM: Checking swsusp image.
[   61.158660] PM: Resume from disk failed.
[   61.172885] EXT3-fs: INFO: recovery required on readonly filesystem.
[   61.172889] EXT3-fs: write access will be enabled during recovery.
[   61.268317] usb 2-9: new high speed USB device using ehci_hcd and address 94
[   61.285008] kjournald starting.  Commit interval 5 seconds
[   61.285032] EXT3-fs: dm-2: orphan cleanup on readonly fs
[   61.285039] ext3_orphan_cleanup: deleting unreferenced inode 228492
[   61.285063] EXT3-fs: dm-2: 1 orphan inode deleted
[   61.285065] EXT3-fs: recovery complete.
[   61.300781] EXT3-fs: mounted filesystem with ordered data mode.
[   61.604479] usb 2-9: new high speed USB device using ehci_hcd and address 95
[   61.940204] usb 2-9: new high speed USB device using ehci_hcd and address 96
[   62.275932] usb 2-9: new high speed USB device using ehci_hcd and address 97
[   62.615662] usb 2-9: new high speed USB device using ehci_hcd and address 98
[   62.951394] usb 2-9: new high speed USB device using ehci_hcd and address 99
[   63.291109] usb 2-9: new high speed USB device using ehci_hcd and address 100
[   63.627723] usb 2-9: new high speed USB device using ehci_hcd and address 101
[   63.961583] usb 2-9: new high speed USB device using ehci_hcd and address 102
[   64.270327] usb 2-9: new high speed USB device using ehci_hcd and address 103
[   64.606053] usb 2-9: new high speed USB device using ehci_hcd and address 104
[   64.914601] usb 2-9: new high speed USB device using ehci_hcd and address 105
[   65.252708] usb 2-9: new high speed USB device using ehci_hcd and address 106
[   65.588258] usb 2-9: new high speed USB device using ehci_hcd and address 107
[   65.921112] usb 2-9: new high speed USB device using ehci_hcd and address 108
[   66.259493] usb 2-9: new high speed USB device using ehci_hcd and address 109
[   66.596454] usb 2-9: new high speed USB device using ehci_hcd and address 110
[   66.896111] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   66.936191] usb 2-9: new high speed USB device using ehci_hcd and address 111
[   66.963309] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[snip]
[   68.922619] usb 2-9: new high speed USB device using ehci_hcd and address 117
[   69.258325] usb 2-9: new high speed USB device using ehci_hcd and address 118
[   69.596229] usb 2-9: new high speed USB device using ehci_hcd and address 119
[   69.929781] usb 2-9: new high speed USB device using ehci_hcd and address 120
[   70.264517] usb 2-9: new high speed USB device using ehci_hcd and address 121
[   70.600250] usb 2-9: new high speed USB device using ehci_hcd and address 122
[   70.726231] loop: module loaded
[   70.744830] lp0: using parport0 (interrupt-driven).
[   70.836743] Adding 3583992k swap ...
[   70.940979] usb 2-9: new high speed USB device using ehci_hcd and address 123
[   71.275879] usb 2-9: new high speed USB device using ehci_hcd and address 124
[   71.421436] EXT3 FS on dm-2, internal journal
[   71.612445] usb 2-9: new high speed USB device using ehci_hcd and address 125
[   71.995134] usb 2-9: new high speed USB device using ehci_hcd and address 126
[   72.330863] usb 2-9: new high speed USB device using ehci_hcd and address 127
[   72.666596] usb 2-9: new high speed USB device using ehci_hcd and address 2
[   72.974349] usb 2-9: new high speed USB device using ehci_hcd and address 3
[   73.282105] usb 2-9: new high speed USB device using ehci_hcd and address 4
[   73.589859] usb 2-9: new high speed USB device using ehci_hcd and address 5
[   73.925591] usb 2-9: new high speed USB device using ehci_hcd and address 6
[   74.261320] usb 2-9: new high speed USB device using ehci_hcd and address 7
[   74.597056] usb 2-9: new high speed USB device using ehci_hcd and address 8
[   74.933778] usb 2-9: new high speed USB device using ehci_hcd and address 9
[   75.268515] usb 2-9: new high speed USB device using ehci_hcd and address 10
[   75.604248] usb 2-9: new high speed USB device using ehci_hcd and address 11
[   75.939981] usb 2-9: new high speed USB device using ehci_hcd and address 12
[   76.275712] usb 2-9: new high speed USB device using ehci_hcd and address 13
[   76.607447] usb 2-9: new high speed USB device using ehci_hcd and address 14
[   76.939185] usb 2-9: new high speed USB device using ehci_hcd and address 15
[   77.270918] usb 2-9: new high speed USB device using ehci_hcd and address 16
[   77.602653] usb 2-9: new high speed USB device using ehci_hcd and address 17
[   77.935382] usb 2-9: new high speed USB device using ehci_hcd and address 18
[   78.267118] usb 2-9: new high speed USB device using ehci_hcd and address 19
[   78.598853] usb 2-9: new high speed USB device using ehci_hcd and address 20
[   78.930594] usb 2-9: new high speed USB device using ehci_hcd and address 21
[   79.265327] usb 2-9: new high speed USB device using ehci_hcd and address 22
[   79.569085] usb 2-9: new high speed USB device using ehci_hcd and address 23
[   79.872842] usb 2-9: new high speed USB device using ehci_hcd and address 24
[   80.204578] usb 2-9: new high speed USB device using ehci_hcd and address 25
[   80.536314] usb 2-9: new high speed USB device using ehci_hcd and address 26
[   80.868046] usb 2-9: new high speed USB device using ehci_hcd and address 27
[   81.199783] usb 2-9: new high speed USB device using ehci_hcd and address 28
[   81.531516] usb 2-9: new high speed USB device using ehci_hcd and address 29
[   81.863252] usb 2-9: new high speed USB device using ehci_hcd and address 30
[   82.194989] usb 2-9: new high speed USB device using ehci_hcd and address 31
[   82.526724] usb 2-9: new high speed USB device using ehci_hcd and address 32
[   82.858459] usb 2-9: new high speed USB device using ehci_hcd and address 33
[   83.190194] usb 2-9: new high speed USB device using ehci_hcd and address 34
[   83.521930] usb 2-9: new high speed USB device using ehci_hcd and address 35
[   83.825687] usb 2-9: new high speed USB device using ehci_hcd and address 36
[   84.158416] usb 2-9: new high speed USB device using ehci_hcd and address 37
[   84.462174] usb 2-9: new high speed USB device using ehci_hcd and address 38
[   84.793910] usb 2-9: new high speed USB device using ehci_hcd and address 39
[   85.125652] usb 2-9: new high speed USB device using ehci_hcd and address 40
[   85.461384] usb 2-9: new high speed USB device using ehci_hcd and address 41
```

---

### Post by MountainX on 2008-03-26
I'm finding some other posts about this problem, but no solutions. Can someone clue me in about this?

[http://ubuntuforums.org/archive/index.php/t-497682.html](http://ubuntuforums.org/archive/index.php/t-497682.html)
[http://lkml.org/lkml/2007/7/14/64](http://lkml.org/lkml/2007/7/14/64)
etc.

---

### Post by MountainX on 2008-03-27
It looks like this is a well-known and very serious bug.
Bug #88746 (ehci-hcd), first reported on 2007-02-28

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746)

A solution is to unload the ehci_hcd module, which is loaded every time the computer starts, using the command 'sudo modprobe -r ehci_hcd'. This works fine but unfortunatly ehci-hcd is necessary for using USB 2.0, so you lose USB 2.0 features.

The solution worked for me, but I can't live without USB 2.0 features. :(

The bug is marked as "won't fix" for Hardy.

---

### Post by MountainX on 2008-03-27
I hate to mark a thread as "solved" when the bug is outstanding and not solved. But I take it the correct thing to do is mark this as solved because I found the answer -- it's a bug. (Admins, if this isn't the way you want me to mark this thread, please let me know.)

---

### Post by MountainX on 2008-05-05
Does anyone know if there is a workaround for this ehci_hcd USB 2.0 bug?

---

