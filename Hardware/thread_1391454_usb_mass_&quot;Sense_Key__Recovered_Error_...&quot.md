---
title: "usb_mass &quot;Sense Key : Recovered Error ...&quot;"
date: 2010-01-26
forum: Hardware
---

### Post by zwz on 2010-01-26
OS: Ubuntu 9.10 (Karmic Koala)
Kernel: 2.6.31-17-generic

After I plug in USB external hard drives to my laptop, the linux kernel issues "Sense Key : Recovered Error ..." messages. Otherwise, the external hard drives work fine. The detailed messages are as follows:

```

[   83.104030] usb 1-3: new high speed USB device using ehci_hcd and address 3
[   83.238814] usb 1-3: configuration #1 chosen from 1 choice
[   83.313345] Initializing USB Mass Storage driver...
[   83.313423] usbcore: registered new interface driver usb-storage
[   83.313428] USB Mass Storage support registered.
[   83.316202] scsi2 : SCSI emulation for USB Mass Storage devices
[   83.316304] usbcore: registered new interface driver ums-cypress
[   83.323881] usb-storage: device found at 3
[   83.323886] usb-storage: waiting for device to settle before scanning
[   83.652048] Clocksource tsc unstable (delta = -152411920 ns)
[   88.320325] usb-storage: device scan complete
[   88.322815] scsi 2:0:0:0: Direct-Access     Hitachi  HTS541616J9AT00  0000 PQ: 0 ANSI: 0
[   88.323868] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   88.347380] sd 2:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[   88.348997] sd 2:0:0:0: [sdb] Write Protect is off
[   88.349009] sd 2:0:0:0: [sdb] Mode Sense: 27 00 00 00
[   88.349017] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   88.350635] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   88.350646]  sdb: sdb1 sdb2 sdb3 sdb4 < sdb5 sdb6 sdb7 sdb8 >
[   88.443043] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   88.443058] sd 2:0:0:0: [sdb] Attached SCSI disk
[   88.526007] sd 2:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[   88.526025] Descriptor sense data with sense descriptors (in hex):
[   88.526033]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[   88.526064]         00 00 00 00 e0 50 
[   88.526080] sd 2:0:0:0: [sdb] Add. Sense: ATA pass through information available
[   88.549005] sd 2:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[   88.549020] Descriptor sense data with sense descriptors (in hex):
[   88.549028]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[   88.549058]         00 4f 00 c2 e0 50 
[   88.549074] sd 2:0:0:0: [sdb] Add. Sense: ATA pass through information available
[   88.629516] sd 2:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[   88.629525] Descriptor sense data with sense descriptors (in hex):
[   88.629528]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[   88.629540]         00 00 00 00 e0 50 
[   88.629546] sd 2:0:0:0: [sdb] Add. Sense: ATA pass through information available
[   88.785032] sd 2:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[   88.785051] Descriptor sense data with sense descriptors (in hex):
[   88.785059]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[   88.785090]         00 4f 00 c2 e0 50 
[   88.785106] sd 2:0:0:0: [sdb] Add. Sense: ATA pass through information available
[   88.900035] sd 2:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[   88.900051] Descriptor sense data with sense descriptors (in hex):
[   88.900058]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 ff 00 00 
[   88.900089]         00 00 00 00 e0 50 
[   88.900105] sd 2:0:0:0: [sdb] Add. Sense: ATA pass through information available
[   89.013910] sd 2:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[   89.013925] Descriptor sense data with sense descriptors (in hex):
[   89.013933]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[   89.013963]         00 4f 00 c2 e0 50 
[   89.013979] sd 2:0:0:0: [sdb] Add. Sense: ATA pass through information available
[   89.113640] sd 2:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[   89.113649] Descriptor sense data with sense descriptors (in hex):
[   89.113652]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[   89.113664]         00 4f 00 c2 e0 50 
[   89.113670] sd 2:0:0:0: [sdb] Add. Sense: ATA pass through information available
[   89.596138] kjournald starting.  Commit interval 5 seconds
[   89.600220] EXT3 FS on sdb5, internal journal
[   89.600227] EXT3-fs: mounted filesystem with writeback data mode.
[   90.044444] kjournald starting.  Commit interval 5 seconds
[   90.058760] EXT3 FS on sdb3, internal journal
[   90.058769] EXT3-fs: mounted filesystem with writeback data mode.
[   90.183465] kjournald starting.  Commit interval 5 seconds
[   90.183479] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   90.188367] EXT3 FS on sdb8, internal journal
[   90.188378] EXT3-fs: mounted filesystem with writeback data mode.
[   90.474111] kjournald starting.  Commit interval 5 seconds
[   90.474123] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   90.476431] EXT3 FS on sdb7, internal journal
[   90.476438] EXT3-fs: mounted filesystem with writeback data mode.
[ 1865.412099] sd 2:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[ 1865.412117] Descriptor sense data with sense descriptors (in hex):
[ 1865.412126]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[ 1865.412352]         00 00 00 00 e0 50 
[ 1865.412368] sd 2:0:0:0: [sdb] Add. Sense: ATA pass through information available
[ 1865.802754] sd 2:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[ 1865.802774] Descriptor sense data with sense descriptors (in hex):
[ 1865.802782]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[ 1865.802813]         00 4f 00 c2 e0 50 
[ 1865.802829] sd 2:0:0:0: [sdb] Add. Sense: ATA pass through information available
[ 1865.803727] sd 2:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[ 1865.803741] Descriptor sense data with sense descriptors (in hex):
[ 1865.803749]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 ff 00 00 
[ 1865.803779]         00 00 00 00 e0 50 
[ 1865.803795] sd 2:0:0:0: [sdb] Add. Sense: ATA pass through information available
[ 1865.807864] sd 2:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[ 1865.807879] Descriptor sense data with sense descriptors (in hex):
[ 1865.807886]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[ 1865.807917]         00 4f 00 c2 e0 50 
[ 1865.807933] sd 2:0:0:0: [sdb] Add. Sense: ATA pass through information available
[ 1865.809902] sd 2:0:0:0: [sdb] Sense Key : Recovered Error [current] [descriptor]
[ 1865.809917] Descriptor sense data with sense descriptors (in hex):
[ 1865.809925]         72 01 00 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
[ 1865.809955]         00 4f 00 c2 e0 50 
[ 1865.809971] sd 2:0:0:0: [sdb] Add. Sense: ATA pass through information available
[ 2074.700596] kjournald starting.  Commit interval 5 seconds
[ 2074.706569] EXT3 FS on sda8, internal journal
[ 2074.706581] EXT3-fs: mounted filesystem with writeback data mode.

```

Is it OK to ignore those "Recoverd Error" messages? Or is it caused by a kernel bug?

---

