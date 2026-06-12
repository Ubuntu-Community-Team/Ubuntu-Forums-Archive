---
title: "BT v1.2"
date: 2011-04-05
forum: Hardware
---

### Post by asalockout on 2011-04-05
**Greetings **USB Bluetooth not accepting something.. kernel log... Kubuntu 10.10,  never apeard in lsusb
i don't know the brand of the USB** BT **but it has just written on it **BT** V1.2 it has a blue transparent cassing, when working used to flash a green light know its in a steady constant light, used it in older ubuntus the 9.04 and befour it was working fine if some one could tell if its a bug in the kernel || fix avaiable || if its broken the USB** BT** i don't know apriciate thanks!!  :)

p, li { white-space: pre-wrap; } Linux version 2.6.35-28-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 (Ubuntu 2.6.35-28.50-generic 2.6.35.11)


Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
                                                                                                         

2011-04-05 20:17:48    usb 1-5    new high speed USB device using ehci_hcd and address 5
2011-04-05 20:17:48    usb 4-1    new full speed USB device using uhci_hcd and address 2
2011-04-05 20:17:48    usb 4-1    device descriptor read/64, error -71
2011-04-05 20:17:48    usb 4-1    device descriptor read/64, error -71
2011-04-05 20:17:49    usb 4-1    new full speed USB device using uhci_hcd and address 3
2011-04-05 20:17:49    usb 4-1    device descriptor read/64, error -71
2011-04-05 20:17:49    usb 4-1    device descriptor read/64, error -71
2011-04-05 20:17:49    usb 4-1    new full speed USB device using uhci_hcd and address 4
2011-04-05 20:17:50    usb 4-1    device not accepting address 4, error -71
2011-04-05 20:17:50    usb 4-1    new full speed USB device using uhci_hcd and address 5
2011-04-05 20:17:50    usb 4-1    device not accepting address 5, error -71
2011-04-05 20:17:50    hub 4-0    .0: unable to enumerate USB device on port 1


Ps: Sometime ago i used debian Lenny and it would sometimes work and other times refuse to but i then  thought it was the software that wasen't up for it Thanks Again! Hastas Buenas !:guitar:
```

```

---

### Post by asalockout on 2011-04-05
**Greetings **USB Bluetooth not accepting something.. kernel log... Kubuntu 10.10,  never apeard in lsusb
i don't know the brand of the USB** BT **but it has just written on it **BT** V1.2 it has a blue transparent cassing, when working used to flash a green light know its in a steady constant light, used it in older ubuntus the 9.04 and befour it was working fine if some one could tell if its a bug in the kernel || fix avaiable || if its broken the USB** BT** i don't know apriciate thanks!!  :)

  Linux version 2.6.35-28-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 (Ubuntu 2.6.35-28.50-generic 2.6.35.11)
  Centrino Toshiba Satelite M70-122 1,7MHZ  1GBYT,M333MHZ Intel Corporation Mobile 915GM/GMS/910GML 256M.

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
                                                                                                         

2011-04-05 20:17:48    usb 1-5    new high speed USB device using ehci_hcd and address 5
2011-04-05 20:17:48    usb 4-1    new full speed USB device using uhci_hcd and address 2
2011-04-05 20:17:48    usb 4-1    device descriptor read/64, error -71
2011-04-05 20:17:48    usb 4-1    device descriptor read/64, error -71
2011-04-05 20:17:49    usb 4-1    new full speed USB device using uhci_hcd and address 3
2011-04-05 20:17:49    usb 4-1    device descriptor read/64, error -71
2011-04-05 20:17:49    usb 4-1    device descriptor read/64, error -71
2011-04-05 20:17:49    usb 4-1    new full speed USB device using uhci_hcd and address 4
2011-04-05 20:17:50    usb 4-1    device not accepting address 4, error -71
2011-04-05 20:17:50    usb 4-1    new full speed USB device using uhci_hcd and address 5
2011-04-05 20:17:50    usb 4-1    device not accepting address 5, error -71
2011-04-05 20:17:50    hub 4-0    .0: unable to enumerate USB device on port 1


Ps: Sometime ago i used Debian Lenny and it would sometimes work and other times refuse to but i then  thought it was the software that wasn't up for it Thanks Again! Hastas Buenas !:guitar:
[/QUOTE]

---

### Post by asalockout on 2011-04-15
Update kernel started recognizing the bluetooth pen but not always when its pluged in some times it still refuses to adressss.


2011-04-06 23:45:34    Laptop    kernel    [ 1795.588196] usb 2-1: new full speed USB device using uhci_hcd and address 21
2011-04-06 23:45:34    Laptop    kernel    [ 1796.004290] usb 2-1: device not accepting address 21, error -71
2011-04-06 23:45:34    Laptop    kernel    [ 1796.004322] hub 2-0:1.0: unable to enumerate USB device on port 1
2011-04-06 23:45:56    Laptop    kernel    [ 1817.804208] usb 2-1: new full speed USB device using uhci_hcd and address 22
2011-04-06 23:46:06    Laptop    kernel    [ 1828.268946] Bluetooth: Core ver 2.15
2011-04-06 23:46:06    Laptop    kernel    [ 1828.268978] NET: Registered protocol family 31
2011-04-06 23:46:06    Laptop    kernel    [ 1828.268980] Bluetooth: HCI device and connection manager initialized
2011-04-06 23:46:06    Laptop    kernel    [ 1828.268984] Bluetooth: HCI socket layer initialized
2011-04-06 23:46:06    Laptop    kernel    [ 1828.288239] Bluetooth: Generic Bluetooth USB driver ver 0.6
2011-04-06 23:46:06    Laptop    kernel    [ 1828.297917] usbcore: registered new interface driver btusb
2011-04-06 23:46:07    Laptop    bluetoothd[1949]    Bluetooth deamon 4.69
2011-04-06 23:46:07    Laptop    bluetoothd[1950]    Starting SDP server
2011-04-06 23:46:07    Laptop    kernel    [ 1828.502601] Bluetooth: L2CAP ver 2.14
2011-04-06 23:46:07    Laptop    kernel    [ 1828.502605] Bluetooth: L2CAP socket layer initialized
2011-04-06 23:46:07    Laptop    bluetoothd[1950]    Starting experimental netlink support
2011-04-06 23:46:07    Laptop    bluetoothd[1950]    Failed to find Bluetooth netlink family
2011-04-06 23:46:07    Laptop    bluetoothd[1950]    Failed to init netlink plugin
2011-04-06 23:46:07    Laptop    kernel    [ 1828.559220] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
2011-04-06 23:46:07    Laptop    kernel    [ 1828.559229] Bluetooth: BNEP filters: protocol multicast
2011-04-06 23:46:07    Laptop    bluetoothd[1950]    HCI dev 0 registered
2011-04-06 23:46:07    Laptop    kernel    [ 1828.581360] Bluetooth: SCO (Voice Link) ver 0.6
2011-04-06 23:46:07    Laptop    kernel    [ 1828.581368] Bluetooth: SCO socket layer initialized
2011-04-06 23:46:07    Laptop    bluetoothd[1950]    HCI dev 0 up
2011-04-06 23:46:07    Laptop    bluetoothd[1950]    Starting security manager 0
2011-04-06 23:46:07    Laptop    bluetoothd[1950]    ioctl(HCIUNBLOCKADDR): Invalid argument (22)
2011-04-06 23:46:07    Laptop    kernel    [ 1828.788058] Bluetooth: RFCOMM TTY layer initialized
2011-04-06 23:46:07    Laptop    kernel    [ 1828.788068] Bluetooth: RFCOMM socket layer initialized
2011-04-06 23:46:07    Laptop    kernel    [ 1828.788071] Bluetooth: RFCOMM ver 1.11

---

