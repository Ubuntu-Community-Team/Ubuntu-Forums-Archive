---
title: "Unable to detect external hdd enclosure"
date: 2010-07-04
forum: Hardware
---

### Post by kpuz on 2010-07-04
I have an external enclosure made by A-Tec which houses two 750GB hdds. I am able to connect this enclosure to my Windows Vista computer and have it detected but Ubuntu doesn't detect them. I have tried using the terminal fdisk -l but that doesn't detect anything. Can anyone help?

---

### Post by Will Shackleton on 2010-07-04
Hi,

Could you send the output of typing 'ls /dev' into the Terminal (without quotes) before plugging it in, and again after doing so?
This checks to see if the system has detected the device at all.

Even better, could you send the difference between the two (ie any items that appeared)

---

### Post by DkBybee on 2010-07-11
Same problem. HDD does not get recognized. I ran ls /dev before and after pluggin in and the results are exactly the same with no changes.

There are errors listed when I run dmesg. 
Results are: 

[   86.696062] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   86.868969] usb 1-1: configuration #1 chosen from 1 choice
[   86.968526] Initializing USB Mass Storage driver...
[   86.971366] scsi2 : SCSI emulation for USB Mass Storage devices
[   86.971922] usbcore: registered new interface driver usb-storage
[   86.971931] USB Mass Storage support registered.
[   86.973882] usb-storage: device found at 3
[   86.973892] usb-storage: waiting for device to settle before scanning
[   92.500355] usb-storage: device scan complete
[   93.064123] usb 1-1: reset full speed USB device using uhci_hcd and address 3
[   93.188225] usb 1-1: device descriptor read/64, error -71
[   93.422756] usb 1-1: device descriptor read/64, error -71
[   93.640161] usb 1-1: reset full speed USB device using uhci_hcd and address 3
[   93.760067] usb 1-1: device descriptor read/64, error -71
[   93.988613] usb 1-1: device descriptor read/64, error -71
[   94.212090] usb 1-1: reset full speed USB device using uhci_hcd and address 3
[   94.628052] usb 1-1: device not accepting address 3, error -71
[   94.742769] usb 1-1: reset full speed USB device using uhci_hcd and address 3
[   95.160084] usb 1-1: device not accepting address 3, error -71
[   95.161095] usb 1-1: USB disconnect, address 3
[   95.280122] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   95.408090] usb 1-1: device descriptor read/64, error -71
[   95.636109] usb 1-1: device descriptor read/64, error -71
[   95.852142] usb 1-1: new full speed USB device using uhci_hcd and address 5
[   95.980106] usb 1-1: device descriptor read/64, error -71
[   96.204053] usb 1-1: device descriptor read/64, error -71
[   96.420054] usb 1-1: new full speed USB device using uhci_hcd and address 6
[   96.828072] usb 1-1: device not accepting address 6, error -71
[   96.940076] usb 1-1: new full speed USB device using uhci_hcd and address 7
[   97.348078] usb 1-1: device not accepting address 7, error -71
[   97.348132] hub 1-0:1.0: unable to enumerate USB device on port 1
[  724.816079] usb 1-1: new full speed USB device using uhci_hcd and address 8
[  724.989418] usb 1-1: configuration #1 chosen from 1 choice
[  725.000510] scsi3 : SCSI emulation for USB Mass Storage devices
[  725.000828] usb-storage: device found at 8
[  725.000833] usb-storage: waiting for device to settle before scanning
[  730.515176] usb-storage: device scan complete
[  731.360102] usb 1-1: reset full speed USB device using uhci_hcd and address 8
[  731.480112] usb 1-1: device descriptor read/64, error -71
[  731.704092] usb 1-1: device descriptor read/64, error -71
[  731.920727] usb 1-1: reset full speed USB device using uhci_hcd and address 8
[  732.044106] usb 1-1: device descriptor read/64, error -71
[  732.272086] usb 1-1: device descriptor read/64, error -71
[  732.488073] usb 1-1: reset full speed USB device using uhci_hcd and address 8
[  732.896058] usb 1-1: device not accepting address 8, error -71
[  733.008103] usb 1-1: reset full speed USB device using uhci_hcd and address 8
[  733.416079] usb 1-1: device not accepting address 8, error -71
[  733.417067] usb 1-1: USB disconnect, address 8
[  733.528070] usb 1-1: new full speed USB device using uhci_hcd and address 9
[  733.648103] usb 1-1: device descriptor read/64, error -71
[  733.872099] usb 1-1: device descriptor read/64, error -71
[  734.088089] usb 1-1: new full speed USB device using uhci_hcd and address 10
[  734.212107] usb 1-1: device descriptor read/64, error -71
[  734.436098] usb 1-1: device descriptor read/64, error -71
[  734.652084] usb 1-1: new full speed USB device using uhci_hcd and address 11
[  735.060087] usb 1-1: device not accepting address 11, error -71
[  735.172297] usb 1-1: new full speed USB device using uhci_hcd and address 12
[  735.588085] usb 1-1: device not accepting address 12, error -71
[  735.588139] hub 1-0:1.0: unable to enumerate USB device on port 1

any help would be greatly appreciated.

---

### Post by kpuz on 2010-12-20
I totally forgot about this post I made. I am still having the problem. When I run ls /dev before and after attaching the usb drive I get the same output. But when I run dmesg as the poster above me mentioned I get a difference:
Without device:
```
[  149.972069] usb 1-3: new high speed USB device using ehci_hcd and address 3
[  150.105176] usb 1-3: configuration #1 chosen from 1 choice
[  150.173059] Initializing USB Mass Storage driver...
[  150.173266] scsi4 : SCSI emulation for USB Mass Storage devices
[  150.173445] usbcore: registered new interface driver usb-storage
[  150.173451] USB Mass Storage support registered.
[  150.174377] usb-storage: device found at 3
[  150.174382] usb-storage: waiting for device to settle before scanning
[  155.172340] usb-storage: device scan complete
[  325.260778] usb 1-3: USB disconnect, address 3
[  473.880063] usb 1-3: new high speed USB device using ehci_hcd and address 4
[  474.013117] usb 1-3: configuration #1 chosen from 1 choice
[  474.013572] scsi5 : SCSI emulation for USB Mass Storage devices
[  474.013878] usb-storage: device found at 4
[  474.013882] usb-storage: waiting for device to settle before scanning
[  479.012289] usb-storage: device scan complete
[  637.901252] usb 1-3: USB disconnect, address 4
```

with device:
```
[  149.972069] usb 1-3: new high speed USB device using ehci_hcd and address 3
[  150.105176] usb 1-3: configuration #1 chosen from 1 choice
[  150.173059] Initializing USB Mass Storage driver...
[  150.173266] scsi4 : SCSI emulation for USB Mass Storage devices
[  150.173445] usbcore: registered new interface driver usb-storage
[  150.173451] USB Mass Storage support registered.
[  150.174377] usb-storage: device found at 3
[  150.174382] usb-storage: waiting for device to settle before scanning
[  155.172340] usb-storage: device scan complete
[  325.260778] usb 1-3: USB disconnect, address 3
[  473.880063] usb 1-3: new high speed USB device using ehci_hcd and address 4
[  474.013117] usb 1-3: configuration #1 chosen from 1 choice
[  474.013572] scsi5 : SCSI emulation for USB Mass Storage devices
[  474.013878] usb-storage: device found at 4
[  474.013882] usb-storage: waiting for device to settle before scanning
[  479.012289] usb-storage: device scan complete
[  637.901252] usb 1-3: USB disconnect, address 4
[  672.396063] usb 1-3: new high speed USB device using ehci_hcd and address 5
[  672.529079] usb 1-3: configuration #1 chosen from 1 choice
[  672.529526] scsi6 : SCSI emulation for USB Mass Storage devices
[  672.529825] usb-storage: device found at 5
[  672.529829] usb-storage: waiting for device to settle before scanning
[  677.528262] usb-storage: device scan complete
```

So it appears that my drive is being detected at some level but it will not show up. How can I get this drive to mount. I don't see this disk listed when I use sudo fdisk -l command in the terminal. Any help or direction is appreciated. The sooner I can get this issue resolved, the sooner I can trash my vista partition. Thank you.

---

### Post by kpuz on 2010-12-20
Some more information: Running lsusb also sees the drive
Before attaching :
```
 lsusb
Bus 005 Device 002: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
After attaching usb drive:
```
lsusb
Bus 005 Device 002: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 1a4a:1670 Silicon Image 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by kpuz on 2010-12-25
Bump

More Information: 
The enclosure uses the SiI5744 chipset. I have been looking around for any other people that are having issues but haven't found much. I am only looking to use the USB to connect to my computer so I am not sure if I should look into port multiplier support (not sure if this support only matters for SATA connections. Maybe someone could enlighten me.)

---

