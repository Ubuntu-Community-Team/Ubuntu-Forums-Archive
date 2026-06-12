---
title: "external drive undetected"
date: 2009-08-28
forum: Hardware
---

### Post by mavicdog on 2009-08-28
I have a mybookworld 1tb usb drive. It was mounting fine until I suspended without unmounting it (I think), now it is not even detected - as far as I can tell (should be sdb). Can anyone help me please? thanks.
I am running jaunty.
uname -a
Linux xxxxxxxx-laptop 2.6.29.1 #1 SMP 

the output from fdisk -l:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1223     9823716   83  Linux
/dev/sda2           30159       30401     1951897+  82  Linux swap / Solaris
/dev/sda3            1224       30158   232420387+  83  Linux

Partition table entries are not in disk order

the output from dmesg | grep -i usb:
(I had posted the output from the wrong log file- note the "device descriptor read/64, error -110" about halfway down)

[    3.971457] usbcore: registered new interface driver usbfs
[    3.971529] usbcore: registered new interface driver hub
[    3.971614] usbcore: registered new device driver usb
[    3.977560] uhci_hcd: USB Universal Host Controller Interface driver
[    3.977796] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.977965] usb usb1: New USB device found, idVendor=1d6b, idProduct=0001
[    3.977973] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.977981] usb usb1: Product: UHCI Host Controller
[    3.977986] usb usb1: Manufacturer: Linux 2.6.29.1 uhci_hcd
[    3.977992] usb usb1: SerialNumber: 0000:00:1d.0
[    3.978163] usb usb1: configuration #1 chosen from 1 choice
[    3.978243] hub 1-0:1.0: USB hub found
[    3.978688] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.978850] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    3.978858] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.978865] usb usb2: Product: UHCI Host Controller
[    3.978871] usb usb2: Manufacturer: Linux 2.6.29.1 uhci_hcd
[    3.978877] usb usb2: SerialNumber: 0000:00:1d.1
[    3.979029] usb usb2: configuration #1 chosen from 1 choice
[    3.979113] hub 2-0:1.0: USB hub found
[    3.979544] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.979714] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    3.979722] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.979730] usb usb3: Product: UHCI Host Controller
[    3.979736] usb usb3: Manufacturer: Linux 2.6.29.1 uhci_hcd
[    3.979741] usb usb3: SerialNumber: 0000:00:1d.2
[    3.979905] usb usb3: configuration #1 chosen from 1 choice
[    3.979991] hub 3-0:1.0: USB hub found
[    3.980382] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.980540] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    3.980548] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.980555] usb usb4: Product: UHCI Host Controller
[    3.980561] usb usb4: Manufacturer: Linux 2.6.29.1 uhci_hcd
[    3.980567] usb usb4: SerialNumber: 0000:00:1d.3
[    3.980705] usb usb4: configuration #1 chosen from 1 choice
[    3.980784] hub 4-0:1.0: USB hub found
[    4.176665] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.176924] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.248070] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.248125] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
[    4.248133] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.248140] usb usb5: Product: EHCI Host Controller
[    4.248146] usb usb5: Manufacturer: Linux 2.6.29.1 ehci_hcd
[    4.248152] usb usb5: SerialNumber: 0000:00:1d.7
[    4.248333] usb usb5: configuration #1 chosen from 1 choice
[    4.248420] hub 5-0:1.0: USB hub found
[    4.969212] usb 5-1: new high speed USB device using ehci_hcd and address 2
[   20.085158] usb 5-1: device descriptor read/64, error -110
[   35.300180] usb 5-1: device descriptor read/64, error -110
[   35.516154] usb 5-1: new high speed USB device using ehci_hcd and address 3
[   50.628175] usb 5-1: device descriptor read/64, error -110
[   65.844177] usb 5-1: device descriptor read/64, error -110
[   66.060167] usb 5-1: new high speed USB device using ehci_hcd and address 4
[   71.080308] usb 5-1: device descriptor read/8, error -110
[   76.200288] usb 5-1: device descriptor read/8, error -110
[   76.416178] usb 5-1: new high speed USB device using ehci_hcd and address 5
[   81.436292] usb 5-1: device descriptor read/8, error -110
[   86.556294] usb 5-1: device descriptor read/8, error -110
[   86.660188] hub 5-0:1.0: unable to enumerate USB device on port 1
[   86.908165] usb 5-4: new high speed USB device using ehci_hcd and address 7
[   87.084547] usb 5-4: New USB device found, idVendor=04f2, idProduct=b071
[   87.084562] usb 5-4: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[   87.084572] usb 5-4: Product: CNF7129
[   87.084580] usb 5-4: Manufacturer: Chicony Electronics Co., Ltd.
[   87.084588] usb 5-4: SerialNumber: SN0001
[   87.084868] usb 5-4: configuration #1 chosen from 1 choice
[   87.184379] usbcore: registered new interface driver uvcvideo
[   87.184387] USB Video Class driver (v0.1.0)
[   87.552119] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  102.664118] usb 1-1: device descriptor read/64, error -110
[  117.880107] usb 1-1: device descriptor read/64, error -110
[  118.096111] usb 1-1: new full speed USB device using uhci_hcd and address 3
[  133.208119] usb 1-1: device descriptor read/64, error -110
[  148.424119] usb 1-1: device descriptor read/64, error -110
[  148.640116] usb 1-1: new full speed USB device using uhci_hcd and address 4
[  153.661255] usb 1-1: device descriptor read/8, error -110
[  158.781266] usb 1-1: device descriptor read/8, error -110
[  158.996121] usb 1-1: new full speed USB device using uhci_hcd and address 5
[  164.017261] usb 1-1: device descriptor read/8, error -110
[  169.137268] usb 1-1: device descriptor read/8, error -110
[  169.240130] hub 1-0:1.0: unable to enumerate USB device on port 1
[  169.480120] usb 1-2: new full speed USB device using uhci_hcd and address 6
[  169.646259] usb 1-2: New USB device found, idVendor=058f, idProduct=9254
[  169.646267] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  169.646273] usb 1-2: Product: Generic USB Hub
[  169.646277] usb 1-2: Manufacturer: ALCOR
[  169.646450] usb 1-2: configuration #1 chosen from 1 choice
[  169.650275] hub 1-2:1.0: USB hub found
[  169.768114] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  169.940204] usb 3-1: New USB device found, idVendor=147e, idProduct=1000
[  169.940212] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  169.940218] usb 3-1: Product: Fingerprint Sensor   
[  169.940222] usb 3-1: Manufacturer: TouchStrip        
[  169.940399] usb 3-1: configuration #1 chosen from 1 choice
[  170.052125] usb 4-2: new full speed USB device using uhci_hcd and address 2
[  170.297284] usb 4-2: New USB device found, idVendor=0b05, idProduct=1712
[  170.297294] usb 4-2: New USB device strings: Mfr=0, Product=0, SerialNumber=3
[  170.297302] usb 4-2: SerialNumber: 0194E8-5B-0002
[  170.297535] usb 4-2: configuration #1 chosen from 1 choice
[  170.383453] usb 1-2.2: new low speed USB device using uhci_hcd and address 7
[  170.410927] Bluetooth: Generic Bluetooth USB driver ver 0.4
[  170.411101] usbcore: registered new interface driver btusb
[  170.521254] usb 1-2.2: New USB device found, idVendor=046d, idProduct=c00e
[  170.521269] usb 1-2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  170.521281] usb 1-2.2: Product: USB-PS/2 Optical Mouse
[  170.521289] usb 1-2.2: Manufacturer: Logitech
[  170.521508] usb 1-2.2: configuration #1 chosen from 1 choice
[  170.605281] usb 1-2.4: new low speed USB device using uhci_hcd and address 8
[  170.648822] usbcore: registered new interface driver hiddev
[  170.662040] input: Logitech USB-PS/2 Optical Mouse as /class/input/input10
[  170.708315] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2.2/input0
[  170.708363] usbcore: registered new interface driver usbhid
[  170.708371] usbhid: v2.6:USB HID core driver
[  170.758224] usb 1-2.4: New USB device found, idVendor=04b3, idProduct=300a
[  170.758256] usb 1-2.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  170.758264] usb 1-2.4: Product: IBM USB Keyboard
[  170.758269] usb 1-2.4: Manufacturer: Silitek
[  170.758500] usb 1-2.4: configuration #1 chosen from 1 choice
[  170.793404] input: Silitek IBM USB Keyboard as /class/input/input11
[  170.824258] generic-usb 0003:04B3:300A.0002: input,hidraw1: USB HID v1.00 Keyboard [Silitek IBM USB Keyboard] on usb-0000:00:1d.0-2.4/input0
[  170.901465] input: Silitek IBM USB Keyboard as /class/input/input12
[  170.938368] generic-usb 0003:04B3:300A.0003: input,hidraw2: USB HID v1.10 Device [Silitek IBM USB Keyboard] on usb-0000:00:1d.0-2.4/input1

---

### Post by mavicdog on 2009-09-01
bump - I had posted the output from the wrong log file- note the "device descriptor read/64, error -110" about halfway down

> **mavicdog said:**
> I have a mybookworld 1tb usb drive. It was mounting fine until I suspended without unmounting it (I think), now it is not even detected - as far as I can tell (should be sdb). Can anyone help me please? thanks.
I am running jaunty.
uname -a
Linux xxxxxxxx-laptop 2.6.29.1 #1 SMP 

the output from fdisk -l:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1223     9823716   83  Linux
/dev/sda2           30159       30401     1951897+  82  Linux swap / Solaris
/dev/sda3            1224       30158   232420387+  83  Linux

Partition table entries are not in disk order

the output from dmesg | grep -i usb:

[    3.971457] usbcore: registered new interface driver usbfs
[    3.971529] usbcore: registered new interface driver hub
[    3.971614] usbcore: registered new device driver usb
[    3.977560] uhci_hcd: USB Universal Host Controller Interface driver
[    3.977796] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.977965] usb usb1: New USB device found, idVendor=1d6b, idProduct=0001
[    3.977973] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.977981] usb usb1: Product: UHCI Host Controller
[    3.977986] usb usb1: Manufacturer: Linux 2.6.29.1 uhci_hcd
[    3.977992] usb usb1: SerialNumber: 0000:00:1d.0
[    3.978163] usb usb1: configuration #1 chosen from 1 choice
[    3.978243] hub 1-0:1.0: USB hub found
[    3.978688] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.978850] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    3.978858] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.978865] usb usb2: Product: UHCI Host Controller
[    3.978871] usb usb2: Manufacturer: Linux 2.6.29.1 uhci_hcd
[    3.978877] usb usb2: SerialNumber: 0000:00:1d.1
[    3.979029] usb usb2: configuration #1 chosen from 1 choice
[    3.979113] hub 2-0:1.0: USB hub found
[    3.979544] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.979714] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    3.979722] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.979730] usb usb3: Product: UHCI Host Controller
[    3.979736] usb usb3: Manufacturer: Linux 2.6.29.1 uhci_hcd
[    3.979741] usb usb3: SerialNumber: 0000:00:1d.2
[    3.979905] usb usb3: configuration #1 chosen from 1 choice
[    3.979991] hub 3-0:1.0: USB hub found
[    3.980382] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.980540] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    3.980548] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    3.980555] usb usb4: Product: UHCI Host Controller
[    3.980561] usb usb4: Manufacturer: Linux 2.6.29.1 uhci_hcd
[    3.980567] usb usb4: SerialNumber: 0000:00:1d.3
[    3.980705] usb usb4: configuration #1 chosen from 1 choice
[    3.980784] hub 4-0:1.0: USB hub found
[    4.176665] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.176924] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.248070] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.248125] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
[    4.248133] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.248140] usb usb5: Product: EHCI Host Controller
[    4.248146] usb usb5: Manufacturer: Linux 2.6.29.1 ehci_hcd
[    4.248152] usb usb5: SerialNumber: 0000:00:1d.7
[    4.248333] usb usb5: configuration #1 chosen from 1 choice
[    4.248420] hub 5-0:1.0: USB hub found
[    4.969212] usb 5-1: new high speed USB device using ehci_hcd and address 2
[   20.085158] usb 5-1: device descriptor read/64, error -110
[   35.300180] usb 5-1: device descriptor read/64, error -110
[   35.516154] usb 5-1: new high speed USB device using ehci_hcd and address 3
[   50.628175] usb 5-1: device descriptor read/64, error -110
[   65.844177] usb 5-1: device descriptor read/64, error -110
[   66.060167] usb 5-1: new high speed USB device using ehci_hcd and address 4
[   71.080308] usb 5-1: device descriptor read/8, error -110
[   76.200288] usb 5-1: device descriptor read/8, error -110
[   76.416178] usb 5-1: new high speed USB device using ehci_hcd and address 5
[   81.436292] usb 5-1: device descriptor read/8, error -110
[   86.556294] usb 5-1: device descriptor read/8, error -110
[   86.660188] hub 5-0:1.0: unable to enumerate USB device on port 1
[   86.908165] usb 5-4: new high speed USB device using ehci_hcd and address 7
[   87.084547] usb 5-4: New USB device found, idVendor=04f2, idProduct=b071
[   87.084562] usb 5-4: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[   87.084572] usb 5-4: Product: CNF7129
[   87.084580] usb 5-4: Manufacturer: Chicony Electronics Co., Ltd.
[   87.084588] usb 5-4: SerialNumber: SN0001
[   87.084868] usb 5-4: configuration #1 chosen from 1 choice
[   87.184379] usbcore: registered new interface driver uvcvideo
[   87.184387] USB Video Class driver (v0.1.0)
[   87.552119] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  102.664118] usb 1-1: device descriptor read/64, error -110
[  117.880107] usb 1-1: device descriptor read/64, error -110
[  118.096111] usb 1-1: new full speed USB device using uhci_hcd and address 3
[  133.208119] usb 1-1: device descriptor read/64, error -110
[  148.424119] usb 1-1: device descriptor read/64, error -110
[  148.640116] usb 1-1: new full speed USB device using uhci_hcd and address 4
[  153.661255] usb 1-1: device descriptor read/8, error -110
[  158.781266] usb 1-1: device descriptor read/8, error -110
[  158.996121] usb 1-1: new full speed USB device using uhci_hcd and address 5
[  164.017261] usb 1-1: device descriptor read/8, error -110
[  169.137268] usb 1-1: device descriptor read/8, error -110
[  169.240130] hub 1-0:1.0: unable to enumerate USB device on port 1
[  169.480120] usb 1-2: new full speed USB device using uhci_hcd and address 6
[  169.646259] usb 1-2: New USB device found, idVendor=058f, idProduct=9254
[  169.646267] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  169.646273] usb 1-2: Product: Generic USB Hub
[  169.646277] usb 1-2: Manufacturer: ALCOR
[  169.646450] usb 1-2: configuration #1 chosen from 1 choice
[  169.650275] hub 1-2:1.0: USB hub found
[  169.768114] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  169.940204] usb 3-1: New USB device found, idVendor=147e, idProduct=1000
[  169.940212] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  169.940218] usb 3-1: Product: Fingerprint Sensor   
[  169.940222] usb 3-1: Manufacturer: TouchStrip        
[  169.940399] usb 3-1: configuration #1 chosen from 1 choice
[  170.052125] usb 4-2: new full speed USB device using uhci_hcd and address 2
[  170.297284] usb 4-2: New USB device found, idVendor=0b05, idProduct=1712
[  170.297294] usb 4-2: New USB device strings: Mfr=0, Product=0, SerialNumber=3
[  170.297302] usb 4-2: SerialNumber: 0194E8-5B-0002
[  170.297535] usb 4-2: configuration #1 chosen from 1 choice
[  170.383453] usb 1-2.2: new low speed USB device using uhci_hcd and address 7
[  170.410927] Bluetooth: Generic Bluetooth USB driver ver 0.4
[  170.411101] usbcore: registered new interface driver btusb
[  170.521254] usb 1-2.2: New USB device found, idVendor=046d, idProduct=c00e
[  170.521269] usb 1-2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  170.521281] usb 1-2.2: Product: USB-PS/2 Optical Mouse
[  170.521289] usb 1-2.2: Manufacturer: Logitech
[  170.521508] usb 1-2.2: configuration #1 chosen from 1 choice
[  170.605281] usb 1-2.4: new low speed USB device using uhci_hcd and address 8
[  170.648822] usbcore: registered new interface driver hiddev
[  170.662040] input: Logitech USB-PS/2 Optical Mouse as /class/input/input10
[  170.708315] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2.2/input0
[  170.708363] usbcore: registered new interface driver usbhid
[  170.708371] usbhid: v2.6:USB HID core driver
[  170.758224] usb 1-2.4: New USB device found, idVendor=04b3, idProduct=300a
[  170.758256] usb 1-2.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  170.758264] usb 1-2.4: Product: IBM USB Keyboard
[  170.758269] usb 1-2.4: Manufacturer: Silitek
[  170.758500] usb 1-2.4: configuration #1 chosen from 1 choice
[  170.793404] input: Silitek IBM USB Keyboard as /class/input/input11
[  170.824258] generic-usb 0003:04B3:300A.0002: input,hidraw1: USB HID v1.00 Keyboard [Silitek IBM USB Keyboard] on usb-0000:00:1d.0-2.4/input0
[  170.901465] input: Silitek IBM USB Keyboard as /class/input/input12
[  170.938368] generic-usb 0003:04B3:300A.0003: input,hidraw2: USB HID v1.10 Device [Silitek IBM USB Keyboard] on usb-0000:00:1d.0-2.4/input1

---

