---
title: "help formating HDD"
date: 2016-06-12
forum: Hardware
---

### Post by anthoney on 2016-06-12
hello ubuntu forums, i hope i'm posting this in the correct place if not inform me. i'm having a issue with some hardware for my PC. i'm currently running ubuntu 14.04 and my PC has only has 80 GB  HDD. i have an other PC ,Burnt Motherboard, with a Western Digital HDD model number WD6400AAKS-65A7B0 which is a 640GB HDD and came with Windows Vista. im trying to format the device via Disks but device shows up as image 1 below. i also have tried GParted and the HDD just doesn't show up in it nor in BIOS. any clue whats going on here or what im missing?

---

### Post by X-RED_Tech on 2016-06-12
> **anthoney said:**
> i also have tried GParted and the HDD just doesn't show up in it nor in BIOS. any clue whats going on here or what im missing?

If it isn't seen in BIOS it can't be seen by the OS.
The HDD must be old. Have you tested before?

---

### Post by anthoney on 2016-06-12
by the way found a forum here with some terminal commands and will post results below. the red colered ones is the device port

```
tony@tony-ED865AA-ABA-SR1610NX-NA540:~$ dmesg | grep usb
[    0.102747] usbcore: registered new interface driver usbfs
[    0.102767] usbcore: registered new interface driver hub
[    0.102788] usbcore: registered new device driver usb
[    1.021156] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.021160] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.021162] usb usb1: Product: EHCI Host Controller
[    1.021165] usb usb1: Manufacturer: Linux 3.19.0-49-generic ehci_hcd
[    1.021168] usb usb1: SerialNumber: 0000:00:13.2
[    1.156825] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.156829] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.156832] usb usb2: Product: OHCI PCI host controller
[    1.156835] usb usb2: Manufacturer: Linux 3.19.0-49-generic ohci_hcd
[    1.156838] usb usb2: SerialNumber: 0000:00:13.0
[    1.216087] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.216091] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.216094] usb usb3: Product: OHCI PCI host controller
[    1.216097] usb usb3: Manufacturer: Linux 3.19.0-49-generic ohci_hcd
[    1.216099] usb usb3: SerialNumber: 0000:00:13.1
[    1.664025] usb 2-2: new low-speed USB device number 2 using ohci-pci
[    1.728031] usb 1-5: new high-speed USB device number 4 using ehci-pci
[    1.768024] usb 3-2: new full-speed USB device number 2 using ohci-pci
[    1.862292] usb 1-5: New USB device found, idVendor=05e3, idProduct=0718
[    1.862295] usb 1-5: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[    1.862298] usb 1-5: Product: USB Storage
[    1.862301] usb 1-5: SerialNumber: 000000000033
[    1.889079] usb 2-2: New USB device found, idVendor=04d9, idProduct=1702
[    1.889085] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.889088] usb 2-2: Product: USB Keyboard
[    1.889090] usb 2-2: Manufacturer:  
[    1.962127] usbcore: registered new interface driver usbhid
[    1.962132] usbhid: USB HID core driver
[    1.973365] usb 1-6: new high-speed USB device number 5 using ehci-pci
[    1.974267] input:   USB Keyboard as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/0003:04D9:1702.0001/input/input5
[    1.986093] usb 3-2: New USB device found, idVendor=046d, idProduct=c52f
[    1.986097] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.986100] usb 3-2: Product: USB Receiver
[    1.986103] usb 3-2: Manufacturer: Logitech
[    1.995327] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/0003:046D:C52F.0003/input/input6
[    2.028431] hid-generic 0003:046D:C52F.0003: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.1-2/input0
[    2.028807] hid-generic 0003:04D9:1702.0001: input,hidraw1: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:13.0-2/input0
[    2.038507] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.1/0003:046D:C52F.0004/input/input7
[    2.048302] input:   USB Keyboard as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.1/0003:04D9:1702.0002/input/input8
[    2.092301] hid-generic 0003:046D:C52F.0004: input,hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.1-2/input1
[    2.107072] usb 1-6: New USB device found, idVendor=22b8, idProduct=2e76
[    2.107079] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.107082] usb 1-6: Product: XT1031
[    2.107085] usb 1-6: Manufacturer: motorola
[    2.107088] usb 1-6: SerialNumber: TA9650AEOW
[    2.148207] hid-generic 0003:04D9:1702.0002: input,hidraw3: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:13.0-2/input1
[    2.468025] usb 3-4: new full-speed USB device number 3 using ohci-pci
[    2.677092] usb 3-4: New USB device found, idVendor=058f, idProduct=9360
[    2.677096] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.677100] usb 3-4: Product: USB Reader
[    2.677103] usb 3-4: Manufacturer:  
[    2.677105] usb 3-4: SerialNumber: 2004888
[    2.691074] usb-storage 1-5:1.0: USB Mass Storage device detected
[    2.691194] scsi host4: usb-storage 1-5:1.0
[    2.691472] usb-storage 3-4:1.0: USB Mass Storage device detected
[    2.691554] scsi host5: usb-storage 3-4:1.0
[    2.691994] usbcore: registered new interface driver usb-storage
[    2.698935] usbcore: registered new interface driver uas
[   88.001724] usb 1-6: USB disconnect, device number 5
[   88.308057] usb 1-6: new high-speed USB device number 7 using ehci-pci
[   88.441975] usb 1-6: New USB device found, idVendor=22b8, idProduct=2e25
[   88.441986] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   88.441992] usb 1-6: Product: XT1031
[   88.441998] usb 1-6: Manufacturer: motorola
[   88.442003] usb 1-6: SerialNumber: TA9650AEOW
[   88.600134] usbcore: registered new interface driver cdc_ether
[   88.614492] rndis_host 1-6:1.0 usb0: register 'rndis_host' at usb-0000:00:13.2-6, RNDIS device, 02:64:00:7c:79:62
[   88.618257] usbcore: registered new interface driver rndis_host
tony@tony-ED865AA-ABA-SR1610NX-NA540:~$ dmesg | grep sd
[    1.988661] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.988734] sd 2:0:0:0: [sda] Write Protect is off
[    1.988738] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.988769] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.989234] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.032674]  sda: sda1 sda2 < sda5 >
[    2.033271] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.335402] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.335409] EXT4-fs (sda1): write access will be enabled during recovery
[    3.690625] sd 4:0:0:0: Attached scsi generic sg2 type 0
[COLOR=#ff0000][    3.693820] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled[/COLOR]
[COLOR=#ff0000][    3.694793] sd 4:0:0:0: [sdb] Asking for cache data failed[/COLOR]
[COLOR=#ff0000][    3.694797] sd 4:0:0:0: [sdb] Assuming drive cache: write through[/COLOR]
[COLOR=#ff0000][    3.700448] sd 4:0:0:0: [sdb] Attached SCSI disk[/COLOR]
[    3.713576] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    3.713885] sd 5:0:0:1: Attached scsi generic sg4 type 0
[    3.714217] sd 5:0:0:2: Attached scsi generic sg5 type 0
[    3.714546] sd 5:0:0:3: Attached scsi generic sg6 type 0
[    3.943117] sd 5:0:0:2: [sde] Attached SCSI removable disk
[    3.993119] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[    4.003117] sd 5:0:0:1: [sdd] Attached SCSI removable disk
[    4.013142] sd 5:0:0:3: [sdf] Attached SCSI removable disk
[    4.454507] EXT4-fs (sda1): orphan cleanup on readonly fs
[    4.454855] EXT4-fs (sda1): 14 orphan inodes deleted
[    4.454858] EXT4-fs (sda1): recovery complete
[    4.570152] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.957020] Adding 2028540k swap on /dev/sda5.  Priority:-1 extents:1 across:2028540k FS
[   16.906669] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   18.958139] audit: type=1400 audit(1465765470.216:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=564 comm="apparmor_parser"
[   18.958876] audit: type=1400 audit(1465765470.216:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=564 comm="apparmor_parser"
[   49.136404] audit: type=1400 audit(1465765500.396:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1872 comm="apparmor_parser"
[   49.137155] audit: type=1400 audit(1465765500.396:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1872 comm="apparmor_parser
```

> **X-RED_Tech said:**
> If it isn't seen in BIOS it can't be seen by the OS.
The HDD must be old. Have you tested before?
not sinse the motherboard fried. it seems to function, spins, heats up as well

---

### Post by weatherman2 on 2016-06-12
> **anthoney said:**
> hello ubuntu forums, i hope i'm posting this in the correct place if not inform me. i'm having a issue with some hardware for my PC. i'm currently running ubuntu 14.04 and my PC has only has 80 GB  HDD. i have an other PC ,Burnt Motherboard, with a Western Digital HDD model number WD6400AAKS-65A7B0 which is a 640GB HDD and came with Windows Vista. im trying to format the device via Disks but device shows up as image 1 below. i also have tried GParted and the HDD just doesn't show up in it nor in BIOS. any clue whats going on here or what im missing?

It looks like you have connected the 640GB hard drive via a USB adapter?  Then in that case, it may not show up in the BIOS at all.

Try opening a terminal and typing this command:

```

dmesg | grep sdb

```

and post the results here.  Perhaps the USB adapter isn't compatible with Ubuntu?

Are you sure the hard drive is healthy?  If it has failed, it may not show up in Ubuntu at all.

---

### Post by X-RED_Tech on 2016-06-12
Please post the specs of the machine where it is presently connected, namely motherboard...
Are you sure it doesn't show up in BIOS? There's nothing you can do from Ubuntu if it doesn't, regardless of the cause (yet to be determined).

---

### Post by weatherman2 on 2016-06-12
I see you already ran a grep of dmesg since my post.  I don't see anything there indicating an obvious problem.

What happened to the motherboard?  If it fried due to a power surge, it may have fried the hard drive as well.  Fairly common.

---

### Post by anthoney on 2016-06-12
the device its currently pluged into is a compaq presario (ran windows 2000) sr1610nx. it has a connection that goes from the board to the HDD and the usb to HDD cable i purchased. reason the last pc motherboared got fried, i guess would be because i ran a game on it without upgrading it. defanatly wasnt a shourt. got this from command 
tony@tony-ED865AA-ABA-SR1610NX-NA540:~$ dmesg | grep sdb
[    3.693820] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    3.694793] sd 4:0:0:0: [sdb] Asking for cache data failed
[    3.694797] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    3.700448] sd 4:0:0:0: [sdb] Attached SCSI disk

---

### Post by X-RED_Tech on 2016-06-12
> **anthoney said:**
> it has a connection that goes from the board to the HDD and the usb to HDD cable i purchased.
At the same time??? How is that even possible?

> reason the last pc motherboared got fried, i guess would be because i ran a game on it without upgrading it.
No, usually software don't "fry boards".

---

### Post by anthoney on 2016-06-12
> **X-RED_Tech said:**
> At the same time??? How is that even possible?


No, usually software don't "fry boards".

Not both connections to one HDD. Has a extra plug in for an extra HDD. Bought the USB to HDD because I wasn't aware of it.  Now to why it fried, I'm not sure. Was bone stock CPU. No upgrades. Never taken apart for any reason except to be checked by a repair shop after it fried

I tried both connections but gave the same results that are in the images posted above. The grey highlighted one in the Disk screenshot is the drive that I'm trying to format. Somehow it picks up the device but gparted doesnt

---

