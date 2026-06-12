---
title: "Can't open USB flash drive, no error message just can't open."
date: 2008-09-30
forum: General Help
---

### Post by exutable on 2008-09-30
Hey guys,

When I try to open my USB flash drive I don't get an error message or anything but nothing happens, literally I don't get any error message or anything.  I am guessing it's an issue with mounting but I'm not positive, kind of new to Ubuntu as a desktop.

Thanks

---

### Post by dcstar on 2008-09-30
> **exutable said:**
> Hey guys,

When I try to open my USB flash drive I don't get an error message or anything but nothing happens, literally I don't get any error message or anything.  I am guessing it's an issue with mounting but I'm not positive, kind of new to Ubuntu as a desktop.

Thanks

Open a terminal, type the following command after you plug in the USB and post a screenshot of the results:
```
dmesg
```

---

### Post by exutable on 2008-09-30
```
[148459.612220] usb 1-1: device descriptor read/64, error -71
[148459.837668] usb 1-1: device descriptor read/64, error -71
[148460.053623] usb 1-1: new full speed USB device using uhci_hcd and address 83
[148460.180595] usb 1-1: device descriptor read/64, error -71
[148460.410492] usb 1-1: device descriptor read/64, error -71
[148460.626306] usb 1-1: new full speed USB device using uhci_hcd and address 84
[148461.042165] usb 1-1: device not accepting address 84, error -71
[148461.152387] usb 1-1: new full speed USB device using uhci_hcd and address 85
[148461.563803] usb 1-1: device not accepting address 85, error -71
[149775.135928] usb 1-2: new full speed USB device using uhci_hcd and address 86
[149775.260401] usb 1-2: device descriptor read/64, error -71
[149775.484852] usb 1-2: device descriptor read/64, error -71
[149775.699808] usb 1-2: new full speed USB device using uhci_hcd and address 87
[149775.821647] usb 1-2: device descriptor read/64, error -71
[149776.047734] usb 1-2: device descriptor read/64, error -71
[149776.263689] usb 1-2: new full speed USB device using uhci_hcd and address 88
[149776.672599] usb 1-2: device not accepting address 88, error -71
[149776.784575] usb 1-2: new full speed USB device using uhci_hcd and address 89
[149777.199986] usb 1-2: device not accepting address 89, error -71
[149987.054777] usb 7-2: new high speed USB device using ehci_hcd and address 28
[149987.188141] usb 7-2: configuration #1 chosen from 2 choices
[149987.244010] usbcore: registered new interface driver libusual
[149987.251646] Initializing USB Mass Storage driver...
[149987.252237] scsi8 : SCSI emulation for USB Mass Storage devices
[149987.252710] usbcore: registered new interface driver usb-storage
[149987.252714] USB Mass Storage support registered.
[149987.252784] usb-storage: device found at 28
[149987.252787] usb-storage: waiting for device to settle before scanning
[149992.656602] usb-storage: device scan complete
[149992.671337] scsi 8:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[149992.690192] sd 8:0:0:0: [sdd] Spinning up disk....ready
[149997.073896] sd 8:0:0:0: [sdd] 39023511 4096-byte hardware sectors (159840 MB)
[149997.075015] sd 8:0:0:0: [sdd] Write Protect is off
[149997.075018] sd 8:0:0:0: [sdd] Mode Sense: 68 00 00 08
[149997.075020] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[149997.077391] sd 8:0:0:0: [sdd] 39023511 4096-byte hardware sectors (159840 MB)
[149997.078635] sd 8:0:0:0: [sdd] Write Protect is off
[149997.078639] sd 8:0:0:0: [sdd] Mode Sense: 68 00 00 08
[149997.078641] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[149997.078644]  sdd: sdd1
[149997.139779] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[149997.139818] sd 8:0:0:0: Attached scsi generic sg4 type 0
[181686.473661] usb 7-2: USB disconnect, address 28
[181690.144012] usb 7-2: new high speed USB device using ehci_hcd and address 29
[181690.277254] usb 7-2: configuration #1 chosen from 2 choices
[181690.283887] scsi9 : SCSI emulation for USB Mass Storage devices
[181690.284000] usb-storage: device found at 29
[181690.284004] usb-storage: waiting for device to settle before scanning
[181695.284912] usb-storage: device scan complete
[181695.292284] scsi 9:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[181695.322264] sd 9:0:0:0: [sdd] Spinning up disk....ready
[181699.979784] sd 9:0:0:0: [sdd] 39023511 4096-byte hardware sectors (159840 MB)
[181699.980908] sd 9:0:0:0: [sdd] Write Protect is off
[181699.980912] sd 9:0:0:0: [sdd] Mode Sense: 68 00 00 08
[181699.980914] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[181699.983289] sd 9:0:0:0: [sdd] 39023511 4096-byte hardware sectors (159840 MB)
[181699.984407] sd 9:0:0:0: [sdd] Write Protect is off
[181699.984411] sd 9:0:0:0: [sdd] Mode Sense: 68 00 00 08
[181699.984412] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[181699.984418]  sdd: sdd1
[181700.010311] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[181700.010350] sd 9:0:0:0: Attached scsi generic sg4 type 0
[182879.958400] usb 7-2: USB disconnect, address 29
[182882.706422] usb 7-2: new high speed USB device using ehci_hcd and address 30
[182882.840268] usb 7-2: configuration #1 chosen from 2 choices
[182882.847526] scsi10 : SCSI emulation for USB Mass Storage devices
[182882.847811] usb-storage: device found at 30
[182882.847816] usb-storage: waiting for device to settle before scanning
[182887.845054] usb-storage: device scan complete
[182887.854543] scsi 10:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[182887.882518] sd 10:0:0:0: [sdd] Spinning up disk....ready
[182892.586033] sd 10:0:0:0: [sdd] 39023511 4096-byte hardware sectors (159840 MB)
[182892.587157] sd 10:0:0:0: [sdd] Write Protect is off
[182892.587160] sd 10:0:0:0: [sdd] Mode Sense: 68 00 00 08
[182892.587161] sd 10:0:0:0: [sdd] Assuming drive cache: write through
[182892.589665] sd 10:0:0:0: [sdd] 39023511 4096-byte hardware sectors (159840 MB)
[182892.590907] sd 10:0:0:0: [sdd] Write Protect is off
[182892.590910] sd 10:0:0:0: [sdd] Mode Sense: 68 00 00 08
[182892.590911] sd 10:0:0:0: [sdd] Assuming drive cache: write through
[182892.590915]  sdd: sdd1
[182892.627548] sd 10:0:0:0: [sdd] Attached SCSI removable disk
[182892.627580] sd 10:0:0:0: Attached scsi generic sg4 type 0
[182898.005957] usb 7-2: USB disconnect, address 30
[296285.748383] usb 7-2: new high speed USB device using ehci_hcd and address 31
[296285.880908] usb 7-2: configuration #1 chosen from 1 choice
[296285.881123] scsi11 : SCSI emulation for USB Mass Storage devices
[296285.881221] usb-storage: device found at 31
[296285.881224] usb-storage: waiting for device to settle before scanning
[296289.075175] usb 7-1: new high speed USB device using ehci_hcd and address 32
[296289.208133] usb 7-1: configuration #1 chosen from 1 choice
[296289.208387] scsi12 : SCSI emulation for USB Mass Storage devices
[296289.208497] usb-storage: device found at 32
[296289.208500] usb-storage: waiting for device to settle before scanning
[296290.879299] usb-storage: device scan complete
[296290.879792] scsi 11:0:0:0: Direct-Access     SanDisk  Cruzer           4.05 PQ: 0 ANSI: 2
[296290.881027] sd 11:0:0:0: [sdd] 8027789 512-byte hardware sectors (4110 MB)
[296290.881653] sd 11:0:0:0: [sdd] Write Protect is off
[296290.881656] sd 11:0:0:0: [sdd] Mode Sense: 03 00 00 00
[296290.881658] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[296290.884279] sd 11:0:0:0: [sdd] 8027789 512-byte hardware sectors (4110 MB)
[296290.884902] sd 11:0:0:0: [sdd] Write Protect is off
[296290.884906] sd 11:0:0:0: [sdd] Mode Sense: 03 00 00 00
[296290.884907] sd 11:0:0:0: [sdd] Assuming drive cache: write through
[296290.884910]  sdd: sdd1
[296290.886339] sd 11:0:0:0: [sdd] Attached SCSI removable disk
[296290.886364] sd 11:0:0:0: Attached scsi generic sg4 type 0
[296294.206402] usb-storage: device scan complete
[296294.206900] scsi 12:0:0:0: Direct-Access     SanDisk  Cruzer           4.05 PQ: 0 ANSI: 2
[296294.208758] sd 12:0:0:0: [sde] 8027789 512-byte hardware sectors (4110 MB)
[296294.209384] sd 12:0:0:0: [sde] Write Protect is off
[296294.209386] sd 12:0:0:0: [sde] Mode Sense: 03 00 00 00
[296294.209388] sd 12:0:0:0: [sde] Assuming drive cache: write through
[296294.211898] sd 12:0:0:0: [sde] 8027789 512-byte hardware sectors (4110 MB)
[296294.212510] sd 12:0:0:0: [sde] Write Protect is off
[296294.212513] sd 12:0:0:0: [sde] Mode Sense: 03 00 00 00
[296294.212515] sd 12:0:0:0: [sde] Assuming drive cache: write through
[296294.212519]  sde: sde1
[296294.213944] sd 12:0:0:0: [sde] Attached SCSI removable disk
[296294.213980] sd 12:0:0:0: Attached scsi generic sg5 type 0
[296421.727229] usb 7-2: USB disconnect, address 31
[296421.858894] usb 7-1: USB disconnect, address 32
[340362.576723] usb 1-1: new full speed USB device using uhci_hcd and address 90
[340362.700304] usb 1-1: device descriptor read/64, error -71
[340362.920649] usb 1-1: device descriptor read/64, error -71
[340363.136607] usb 1-1: new full speed USB device using uhci_hcd and address 91
[340363.257577] usb 1-1: device descriptor read/64, error -71
[340363.480531] usb 1-1: device descriptor read/64, error -71
[340363.696485] usb 1-1: new full speed USB device using uhci_hcd and address 92
[340364.104895] usb 1-1: device not accepting address 92, error -71
[340364.216874] usb 1-1: new full speed USB device using uhci_hcd and address 93
[340364.624281] usb 1-1: device not accepting address 93, error -71
[340494.260669] usb 1-1: new full speed USB device using uhci_hcd and address 94
[340494.381640] usb 1-1: device descriptor read/64, error -71
[340494.605596] usb 1-1: device descriptor read/64, error -71
[340494.821548] usb 1-1: new full speed USB device using uhci_hcd and address 95
[340494.941547] usb 1-1: device descriptor read/64, error -71
[340495.168969] usb 1-1: device descriptor read/64, error -71
[340495.384922] usb 1-1: new full speed USB device using uhci_hcd and address 96
[340495.796338] usb 1-1: device not accepting address 96, error -71
[340495.909815] usb 1-1: new full speed USB device using uhci_hcd and address 97
[340496.324224] usb 1-1: device not accepting address 97, error -71
[342628.985834] usb 1-1: new full speed USB device using uhci_hcd and address 98
[342629.105807] usb 1-1: device descriptor read/64, error -71
[342629.329758] usb 1-1: device descriptor read/64, error -71
[342629.546211] usb 1-1: new full speed USB device using uhci_hcd and address 99
[342629.674183] usb 1-1: device descriptor read/64, error -71
[342629.893636] usb 1-1: device descriptor read/64, error -71
[342630.109590] usb 1-1: new full speed USB device using uhci_hcd and address 100
[342630.517503] usb 1-1: device not accepting address 100, error -71
[342630.629981] usb 1-1: new full speed USB device using uhci_hcd and address 101
[342631.041892] usb 1-1: device not accepting address 101, error -71
[342760.346844] usb 1-1: new full speed USB device using uhci_hcd and address 102
[342760.469820] usb 1-1: device descriptor read/64, error -71
[342760.693770] usb 1-1: device descriptor read/64, error -71
[342760.909724] usb 1-1: new full speed USB device using uhci_hcd and address 103
[342761.030199] usb 1-1: device descriptor read/64, error -71
[342761.253653] usb 1-1: device descriptor read/64, error -71
[342761.469623] usb 1-1: new full speed USB device using uhci_hcd and address 104
[342761.877518] usb 1-1: device not accepting address 104, error -71
[342761.989497] usb 1-1: new full speed USB device using uhci_hcd and address 105
[342762.397408] usb 1-1: device not accepting address 105, error -71
[344838.327104] usb 1-1: new full speed USB device using uhci_hcd and address 106
[344838.447080] usb 1-1: device descriptor read/64, error -71
[344838.675029] usb 1-1: device descriptor read/64, error -71
[344838.890982] usb 1-1: new full speed USB device using uhci_hcd and address 107
[344839.010956] usb 1-1: device descriptor read/64, error -71
[344839.238906] usb 1-1: device descriptor read/64, error -71
[344839.450862] usb 1-1: new full speed USB device using uhci_hcd and address 108
[344839.867271] usb 1-1: device not accepting address 108, error -71
[344839.978750] usb 1-1: new full speed USB device using uhci_hcd and address 109
[344840.386662] usb 1-1: device not accepting address 109, error -71
[346638.527548] usb 1-1: new full speed USB device using uhci_hcd and address 110
[346638.649018] usb 1-1: device descriptor read/64, error -71
[346638.871478] usb 1-1: device descriptor read/64, error -71
[346639.087430] usb 1-1: new full speed USB device using uhci_hcd and address 111
[346639.207399] usb 1-1: device descriptor read/64, error -71
[346639.431351] usb 1-1: device descriptor read/64, error -71
[346639.648804] usb 1-1: new full speed USB device using uhci_hcd and address 112
[346640.055229] usb 1-1: device not accepting address 112, error -71
[346640.167199] usb 1-1: new full speed USB device using uhci_hcd and address 113
[346640.575108] usb 1-1: device not accepting address 113, error -71
[346770.083519] usb 1-1: new full speed USB device using uhci_hcd and address 114
[346770.204492] usb 1-1: device descriptor read/64, error -71
[346770.431940] usb 1-1: device descriptor read/64, error -71
[346770.647394] usb 1-1: new full speed USB device using uhci_hcd and address 115
[346770.767374] usb 1-1: device descriptor read/64, error -71
[346770.995819] usb 1-1: device descriptor read/64, error -71
[346771.211773] usb 1-1: new full speed USB device using uhci_hcd and address 116
[346771.620186] usb 1-1: device not accepting address 116, error -71
[346771.732167] usb 1-1: new full speed USB device using uhci_hcd and address 117
[346772.148574] usb 1-1: device not accepting address 117, error -71
[349357.736182] usb 1-1: new full speed USB device using uhci_hcd and address 118
[349357.856155] usb 1-1: device descriptor read/64, error -71
[349358.084106] usb 1-1: device descriptor read/64, error -71
[349358.300062] usb 1-1: new full speed USB device using uhci_hcd and address 119
[349358.420034] usb 1-1: device descriptor read/64, error -71
[349358.647989] usb 1-1: device descriptor read/64, error -71
[349358.863941] usb 1-1: new full speed USB device using uhci_hcd and address 120
[349359.271852] usb 1-1: device not accepting address 120, error -71
[349359.383830] usb 1-1: new full speed USB device using uhci_hcd and address 121
[349359.792739] usb 1-1: device not accepting address 121, error -71
[349489.176176] usb 1-1: new full speed USB device using uhci_hcd and address 122
[349489.296654] usb 1-1: device descriptor read/64, error -71
[349489.521100] usb 1-1: device descriptor read/64, error -71
[349489.736057] usb 1-1: new full speed USB device using uhci_hcd and address 123
[349489.856037] usb 1-1: device descriptor read/64, error -71
[349490.083986] usb 1-1: device descriptor read/64, error -71
[349490.295943] usb 1-1: new full speed USB device using uhci_hcd and address 124
[349490.707858] usb 1-1: device not accepting address 124, error -71
[349490.819825] usb 1-1: new full speed USB device using uhci_hcd and address 125
[349491.227739] usb 1-1: device not accepting address 125, error -71
[352146.923407] usb 1-1: new full speed USB device using uhci_hcd and address 126
[352147.045883] usb 1-1: device descriptor read/64, error -71
[352147.269840] usb 1-1: device descriptor read/64, error -71
[352147.486784] usb 1-1: new full speed USB device using uhci_hcd and address 127
[352147.609767] usb 1-1: device descriptor read/64, error -71
[352147.835212] usb 1-1: device descriptor read/64, error -71
[352148.049668] usb 1-1: new full speed USB device using uhci_hcd and address 2
[352148.458576] usb 1-1: device not accepting address 2, error -71
[352148.569555] usb 1-1: new full speed USB device using uhci_hcd and address 3
[352148.977471] usb 1-1: device not accepting address 3, error -71
[354095.282794] usb 1-1: new full speed USB device using uhci_hcd and address 4
[354095.406760] usb 1-1: device descriptor read/64, error -71
[354095.634708] usb 1-1: device descriptor read/64, error -71
[354095.852159] usb 1-1: new full speed USB device using uhci_hcd and address 5
[354095.975205] usb 1-1: device descriptor read/64, error -71
[354096.202592] usb 1-1: device descriptor read/64, error -71
[354096.418549] usb 1-1: new full speed USB device using uhci_hcd and address 6
[354096.826456] usb 1-1: device not accepting address 6, error -71
[354096.938432] usb 1-1: new full speed USB device using uhci_hcd and address 7
[354097.346342] usb 1-1: device not accepting address 7, error -71
[356063.523449] usb 1-1: new full speed USB device using uhci_hcd and address 8
[356063.643400] usb 1-1: device descriptor read/64, error -71
[356063.867349] usb 1-1: device descriptor read/64, error -71
[356064.083304] usb 1-1: new full speed USB device using uhci_hcd and address 9
[356064.203279] usb 1-1: device descriptor read/64, error -71
[356064.427233] usb 1-1: device descriptor read/64, error -71
[356064.644682] usb 1-1: new full speed USB device using uhci_hcd and address 10
[356065.055096] usb 1-1: device not accepting address 10, error -71
[356065.167073] usb 1-1: new full speed USB device using uhci_hcd and address 11
[356065.574985] usb 1-1: device not accepting address 11, error -71
[358016.647285] usb 1-1: new full speed USB device using uhci_hcd and address 12
[358016.767258] usb 1-1: device descriptor read/64, error -71
[358016.991211] usb 1-1: device descriptor read/64, error -71
[358017.208663] usb 1-1: new full speed USB device using uhci_hcd and address 13
[358017.332635] usb 1-1: device descriptor read/64, error -71
[358017.559091] usb 1-1: device descriptor read/64, error -71
[358017.775043] usb 1-1: new full speed USB device using uhci_hcd and address 14
[358018.182959] usb 1-1: device not accepting address 14, error -71
[358018.294947] usb 1-1: new full speed USB device using uhci_hcd and address 15
[358018.702845] usb 1-1: device not accepting address 15, error -71
[358146.528621] usb 1-1: new full speed USB device using uhci_hcd and address 16
[358146.649089] usb 1-1: device descriptor read/64, error -71
[358146.871544] usb 1-1: device descriptor read/64, error -71
[358147.087493] usb 1-1: new full speed USB device using uhci_hcd and address 17
[358147.208969] usb 1-1: device descriptor read/64, error -71
[358147.435421] usb 1-1: device descriptor read/64, error -71
[358147.651379] usb 1-1: new full speed USB device using uhci_hcd and address 18
[358148.063287] usb 1-1: device not accepting address 18, error -71
[358148.175260] usb 1-1: new full speed USB device using uhci_hcd and address 19
[358148.583172] usb 1-1: device not accepting address 19, error -71
[360812.531581] usb 1-1: new full speed USB device using uhci_hcd and address 20
[360812.651560] usb 1-1: device descriptor read/64, error -71
[360812.875509] usb 1-1: device descriptor read/64, error -71
[360813.091466] usb 1-1: new full speed USB device using uhci_hcd and address 21
[360813.211448] usb 1-1: device descriptor read/64, error -71
[360813.435396] usb 1-1: device descriptor read/64, error -71
[360813.651351] usb 1-1: new full speed USB device using uhci_hcd and address 22
[360814.059264] usb 1-1: device not accepting address 22, error -71
[360814.172241] usb 1-1: new full speed USB device using uhci_hcd and address 23
[360814.587143] usb 1-1: device not accepting address 23, error -71
[360944.059567] usb 1-1: new full speed USB device using uhci_hcd and address 24
[360944.181038] usb 1-1: device descriptor read/64, error -71
[360944.408989] usb 1-1: device descriptor read/64, error -71
[360944.624946] usb 1-1: new full speed USB device using uhci_hcd and address 25
[360944.748917] usb 1-1: device descriptor read/64, error -71
[360944.976871] usb 1-1: device descriptor read/64, error -71
[360945.191326] usb 1-1: new full speed USB device using uhci_hcd and address 26
[360945.600729] usb 1-1: device not accepting address 26, error -71
[360945.711214] usb 1-1: new full speed USB device using uhci_hcd and address 27
[360946.119123] usb 1-1: device not accepting address 27, error -71
[363457.556433] usb 1-1: new full speed USB device using uhci_hcd and address 28
[363457.681505] usb 1-1: device descriptor read/64, error -71
[363457.905456] usb 1-1: device descriptor read/64, error -71
[363458.119913] usb 1-1: new full speed USB device using uhci_hcd and address 29
[363458.239887] usb 1-1: device descriptor read/64, error -71
[363458.463836] usb 1-1: device descriptor read/64, error -71
[363458.679793] usb 1-1: new full speed USB device using uhci_hcd and address 30
[363459.088700] usb 1-1: device not accepting address 30, error -71
[363459.200680] usb 1-1: new full speed USB device using uhci_hcd and address 31
[363459.613088] usb 1-1: device not accepting address 31, error -71
[363589.004026] usb 1-1: new full speed USB device using uhci_hcd and address 32
[363589.124492] usb 1-1: device descriptor read/64, error -71
[363589.351942] usb 1-1: device descriptor read/64, error -71
[363589.567897] usb 1-1: new full speed USB device using uhci_hcd and address 33
[363589.688172] usb 1-1: device descriptor read/64, error -71
[363589.911831] usb 1-1: device descriptor read/64, error -71
[363590.127789] usb 1-1: new full speed USB device using uhci_hcd and address 34
[363590.536191] usb 1-1: device not accepting address 34, error -71
[363590.648172] usb 1-1: new full speed USB device using uhci_hcd and address 35
[363591.059580] usb 1-1: device not accepting address 35, error -71
[366115.645687] usb 1-1: new full speed USB device using uhci_hcd and address 36
[366115.767158] usb 1-1: device descriptor read/64, error -71
[366115.993612] usb 1-1: device descriptor read/64, error -71
[366116.209566] usb 1-1: new full speed USB device using uhci_hcd and address 37
[366116.329539] usb 1-1: device descriptor read/64, error -71
[366116.558489] usb 1-1: device descriptor read/64, error -71
[366116.773443] usb 1-1: new full speed USB device using uhci_hcd and address 38
[366117.181358] usb 1-1: device not accepting address 38, error -71
[366117.293836] usb 1-1: new full speed USB device using uhci_hcd and address 39
[366117.701245] usb 1-1: device not accepting address 39, error -71
[366247.249646] usb 1-1: new full speed USB device using uhci_hcd and address 40
[366247.369623] usb 1-1: device descriptor read/64, error -71
[366247.597572] usb 1-1: device descriptor read/64, error -71
[366247.813523] usb 1-1: new full speed USB device using uhci_hcd and address 41
[366247.933504] usb 1-1: device descriptor read/64, error -71
[366248.165459] usb 1-1: device descriptor read/64, error -71
[366248.381412] usb 1-1: new full speed USB device using uhci_hcd and address 42
[366248.789317] usb 1-1: device not accepting address 42, error -71
[366248.903256] usb 1-1: new full speed USB device using uhci_hcd and address 43
[366249.313210] usb 1-1: device not accepting address 43, error -71
[368782.537465] usb 1-1: new full speed USB device using uhci_hcd and address 44
[368782.657441] usb 1-1: device descriptor read/64, error -71
[368782.885392] usb 1-1: device descriptor read/64, error -71
[368783.102843] usb 1-1: new full speed USB device using uhci_hcd and address 45
[368783.226822] usb 1-1: device descriptor read/64, error -71
[368783.449270] usb 1-1: device descriptor read/64, error -71
[368783.665226] usb 1-1: new full speed USB device using uhci_hcd and address 46
[368784.073142] usb 1-1: device not accepting address 46, error -71
[368784.185122] usb 1-1: new full speed USB device using uhci_hcd and address 47
[368784.597025] usb 1-1: device not accepting address 47, error -71
[368914.002467] usb 1-1: new full speed USB device using uhci_hcd and address 48
[368914.125434] usb 1-1: device descriptor read/64, error -71
[368914.357380] usb 1-1: device descriptor read/64, error -71
[368914.569336] usb 1-1: new full speed USB device using uhci_hcd and address 49
[368914.690315] usb 1-1: device descriptor read/64, error -71
[368914.913269] usb 1-1: device descriptor read/64, error -71
[368915.129225] usb 1-1: new full speed USB device using uhci_hcd and address 50
[368915.541127] usb 1-1: device not accepting address 50, error -71
[368915.654610] usb 1-1: new full speed USB device using uhci_hcd and address 51
[368916.065018] usb 1-1: device not accepting address 51, error -71
[371553.938983] usb 1-1: new full speed USB device using uhci_hcd and address 52
[371554.058962] usb 1-1: device descriptor read/64, error -71
[371554.282917] usb 1-1: device descriptor read/64, error -71
[371554.498868] usb 1-1: new full speed USB device using uhci_hcd and address 53
[371554.618839] usb 1-1: device descriptor read/64, error -71
[371554.847294] usb 1-1: device descriptor read/64, error -71
[371555.063247] usb 1-1: new full speed USB device using uhci_hcd and address 54
[371555.478652] usb 1-1: device not accepting address 54, error -71
[371555.590632] usb 1-1: new full speed USB device using uhci_hcd and address 55
[371555.998544] usb 1-1: device not accepting address 55, error -71
[374087.791117] usb 1-1: new full speed USB device using uhci_hcd and address 56
[374087.911092] usb 1-1: device descriptor read/64, error -71
[374088.135044] usb 1-1: device descriptor read/64, error -71
[374088.351000] usb 1-1: new full speed USB device using uhci_hcd and address 57
[374088.470968] usb 1-1: device descriptor read/64, error -71
[374088.698918] usb 1-1: device descriptor read/64, error -71
[374088.914872] usb 1-1: new full speed USB device using uhci_hcd and address 58
[374089.322789] usb 1-1: device not accepting address 58, error -71
[374089.434768] usb 1-1: new full speed USB device using uhci_hcd and address 59
[374089.846674] usb 1-1: device not accepting address 59, error -71
[374219.191122] usb 1-1: new full speed USB device using uhci_hcd and address 60
[374219.311093] usb 1-1: device descriptor read/64, error -71
[374219.535046] usb 1-1: device descriptor read/64, error -71
[374219.751001] usb 1-1: new full speed USB device using uhci_hcd and address 61
[374219.870972] usb 1-1: device descriptor read/64, error -71
[374220.094927] usb 1-1: device descriptor read/64, error -71
[374220.310881] usb 1-1: new full speed USB device using uhci_hcd and address 62
[374220.718789] usb 1-1: device not accepting address 62, error -71
[374220.830774] usb 1-1: new full speed USB device using uhci_hcd and address 63
[374221.238686] usb 1-1: device not accepting address 63, error -71
[376777.106117] usb 1-1: new full speed USB device using uhci_hcd and address 64
[376777.227591] usb 1-1: device descriptor read/64, error -71
[376777.454044] usb 1-1: device descriptor read/64, error -71
[376777.669998] usb 1-1: new full speed USB device using uhci_hcd and address 65
[376777.789978] usb 1-1: device descriptor read/64, error -71
[376778.013928] usb 1-1: device descriptor read/64, error -71
[376778.233882] usb 1-1: new full speed USB device using uhci_hcd and address 66
[376778.641793] usb 1-1: device not accepting address 66, error -71
[376778.753778] usb 1-1: new full speed USB device using uhci_hcd and address 67
[376779.161678] usb 1-1: device not accepting address 67, error -71
[376908.654087] usb 1-1: new full speed USB device using uhci_hcd and address 68
[376908.774063] usb 1-1: device descriptor read/64, error -71
[376908.998016] usb 1-1: device descriptor read/64, error -71
[376909.214969] usb 1-1: new full speed USB device using uhci_hcd and address 69
[376909.338448] usb 1-1: device descriptor read/64, error -71
[376909.561896] usb 1-1: device descriptor read/64, error -71
[376909.777850] usb 1-1: new full speed USB device using uhci_hcd and address 70
[376910.185762] usb 1-1: device not accepting address 70, error -71
[376910.298737] usb 1-1: new full speed USB device using uhci_hcd and address 71
[376910.709651] usb 1-1: device not accepting address 71, error -71
[379383.862714] usb 1-1: new full speed USB device using uhci_hcd and address 72
[379383.982692] usb 1-1: device descriptor read/64, error -71
[379384.206656] usb 1-1: device descriptor read/64, error -71
[379384.422598] usb 1-1: new full speed USB device using uhci_hcd and address 73
[379384.542574] usb 1-1: device descriptor read/64, error -71
[379384.767024] usb 1-1: device descriptor read/64, error -71
[379384.982480] usb 1-1: new full speed USB device using uhci_hcd and address 74
[379385.395382] usb 1-1: device not accepting address 74, error -71
[379385.507360] usb 1-1: new full speed USB device using uhci_hcd and address 75
[379385.922273] usb 1-1: device not accepting address 75, error -71
[379515.334701] usb 1-1: new full speed USB device using uhci_hcd and address 76
[379515.454674] usb 1-1: device descriptor read/64, error -71
[379515.682633] usb 1-1: device descriptor read/64, error -71
[379515.898585] usb 1-1: new full speed USB device using uhci_hcd and address 77
[379516.018560] usb 1-1: device descriptor read/64, error -71
[379516.243011] usb 1-1: device descriptor read/64, error -71
[379516.458966] usb 1-1: new full speed USB device using uhci_hcd and address 78
[379516.870373] usb 1-1: device not accepting address 78, error -71
[379516.982356] usb 1-1: new full speed USB device using uhci_hcd and address 79
[379517.390263] usb 1-1: device not accepting address 79, error -71
[405430.492952] console-kit-dae[24619]: segfault at 0 rip 7fdc8b978110 rsp 7fff948ab818 error 4
[423452.866224] usb 7-1: new high speed USB device using ehci_hcd and address 62
[423452.998195] usb 7-1: configuration #1 chosen from 1 choice
[423452.998414] scsi13 : SCSI emulation for USB Mass Storage devices
[423452.998512] usb-storage: device found at 62
[423452.998516] usb-storage: waiting for device to settle before scanning
[423457.996474] usb-storage: device scan complete
[423457.996964] scsi 13:0:0:0: Direct-Access     SanDisk  Cruzer           4.05 PQ: 0 ANSI: 2
[423458.003443] sd 13:0:0:0: [sdd] 8027789 512-byte hardware sectors (4110 MB)
[423458.004064] sd 13:0:0:0: [sdd] Write Protect is off
[423458.004067] sd 13:0:0:0: [sdd] Mode Sense: 03 00 00 00
[423458.004069] sd 13:0:0:0: [sdd] Assuming drive cache: write through
[423458.006687] sd 13:0:0:0: [sdd] 8027789 512-byte hardware sectors (4110 MB)
[423458.007310] sd 13:0:0:0: [sdd] Write Protect is off
[423458.007313] sd 13:0:0:0: [sdd] Mode Sense: 03 00 00 00
[423458.007315] sd 13:0:0:0: [sdd] Assuming drive cache: write through
[423458.007318]  sdd: sdd1
[423458.008749] sd 13:0:0:0: [sdd] Attached SCSI removable disk
[423458.008783] sd 13:0:0:0: Attached scsi generic sg4 type 0
[423818.686715] usb 7-1: USB disconnect, address 62
[423827.470914] usb 7-1: new high speed USB device using ehci_hcd and address 63
[423827.606396] usb 7-1: configuration #1 chosen from 1 choice
[423827.606653] scsi14 : SCSI emulation for USB Mass Storage devices
[423827.606764] usb-storage: device found at 63
[423827.606768] usb-storage: waiting for device to settle before scanning
[423832.604539] usb-storage: device scan complete
[423832.605037] scsi 14:0:0:0: Direct-Access     SanDisk  Cruzer           4.05 PQ: 0 ANSI: 2
[423832.606280] sd 14:0:0:0: [sdd] 8027789 512-byte hardware sectors (4110 MB)
[423832.606896] sd 14:0:0:0: [sdd] Write Protect is off
[423832.606899] sd 14:0:0:0: [sdd] Mode Sense: 03 00 00 00
[423832.606902] sd 14:0:0:0: [sdd] Assuming drive cache: write through
[423832.609520] sd 14:0:0:0: [sdd] 8027789 512-byte hardware sectors (4110 MB)
[423832.610146] sd 14:0:0:0: [sdd] Write Protect is off
[423832.610149] sd 14:0:0:0: [sdd] Mode Sense: 03 00 00 00
[423832.610151] sd 14:0:0:0: [sdd] Assuming drive cache: write through
[423832.610155]  sdd: sdd1
[423832.611586] sd 14:0:0:0: [sdd] Attached SCSI removable disk
[423832.611621] sd 14:0:0:0: Attached scsi generic sg4 type 0
[425614.601190] UDF-fs: No VRS found
[425614.687247] ISO 9660 Extensions: Microsoft Joliet Level 3
[425614.687814] ISOFS: changing to secondary root
[425665.237917] nautilus[7083]: segfault at 9 rip 7fc41a446a24 rsp 7fff2cae7d80 error 4
[429274.208792] cdrom: This disc doesn't have any tracks I recognize!
[429463.545956] usb 7-1: USB disconnect, address 63
[429477.325188] UDF-fs: No VRS found
[429477.388947] ISO 9660 Extensions: Microsoft Joliet Level 3
[429477.397116] ISO 9660 Extensions: RRIP_1991A
[429607.339034] UDF-fs: No VRS found
[429607.402896] ISO 9660 Extensions: Microsoft Joliet Level 3
[429607.411230] ISO 9660 Extensions: RRIP_1991A
[429715.355913] usb 1-1: new full speed USB device using uhci_hcd and address 80
[429715.480387] usb 1-1: device descriptor read/64, error -71
[429715.706842] usb 1-1: device descriptor read/64, error -71
[429715.918797] usb 1-1: new full speed USB device using uhci_hcd and address 81
[429716.038773] usb 1-1: device descriptor read/64, error -71
[429716.262720] usb 1-1: device descriptor read/64, error -71
[429716.480175] usb 1-1: new full speed USB device using uhci_hcd and address 82
[429716.890587] usb 1-1: device not accepting address 82, error -71
[429717.002571] usb 1-1: new full speed USB device using uhci_hcd and address 83
[429717.410476] usb 1-1: device not accepting address 83, error -71
[429847.012363] usb 1-1: new full speed USB device using uhci_hcd and address 84
[429847.135835] usb 1-1: device descriptor read/64, error -71
[429847.358792] usb 1-1: device descriptor read/64, error -71
[429847.574747] usb 1-1: new full speed USB device using uhci_hcd and address 85
[429847.694717] usb 1-1: device descriptor read/64, error -71
[429847.918675] usb 1-1: device descriptor read/64, error -71
[429848.134627] usb 1-1: new full speed USB device using uhci_hcd and address 86
[429848.547034] usb 1-1: device not accepting address 86, error -71
[429848.659017] usb 1-1: new full speed USB device using uhci_hcd and address 87
[429849.067423] usb 1-1: device not accepting address 87, error -71
[430201.484137] usb 7-1: new high speed USB device using ehci_hcd and address 66
[430201.616938] usb 7-1: configuration #1 chosen from 1 choice
[430201.617295] scsi15 : SCSI emulation for USB Mass Storage devices
[430201.617415] usb-storage: device found at 66
[430201.617419] usb-storage: waiting for device to settle before scanning
[430206.615657] usb-storage: device scan complete
[430206.616199] scsi 15:0:0:0: Direct-Access     SanDisk  Cruzer           4.05 PQ: 0 ANSI: 2
[430206.617680] sd 15:0:0:0: [sdd] 8027789 512-byte hardware sectors (4110 MB)
[430206.618340] sd 15:0:0:0: [sdd] Write Protect is off
[430206.618345] sd 15:0:0:0: [sdd] Mode Sense: 03 00 00 00
[430206.618346] sd 15:0:0:0: [sdd] Assuming drive cache: write through
[430206.620923] sd 15:0:0:0: [sdd] 8027789 512-byte hardware sectors (4110 MB)
[430206.622821] sd 15:0:0:0: [sdd] Write Protect is off
[430206.622827] sd 15:0:0:0: [sdd] Mode Sense: 03 00 00 00
[430206.622828] sd 15:0:0:0: [sdd] Assuming drive cache: write through
[430206.622833]  sdd: sdd1
[430206.624118] sd 15:0:0:0: [sdd] Attached SCSI removable disk
[430206.624155] sd 15:0:0:0: Attached scsi generic sg4 type 0
dshea@dshea-desktop:~$ 


```

---

