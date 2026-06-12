---
title: "No usb audio support in kubuntu 16.10?"
date: 2016-10-14
forum: Hardware
---

### Post by markslaw2 on 2016-10-14
I'm not able to get sound out of my usb speakers since I upgraded to kubuntu 16.10. In system settings, under audio and video usb audio is greyed out. How can I fix this?

---

### Post by pontoffeltier on 2016-11-08
I'm having the same problem. I am using my Asus HZ-3A USB 3.0 dock since 16.04 and sound has been working just fine until 16.10. As soon as I plug it in, I get errors in my syslog and my system-settings freeze up on my. My /var/log/syslog from the point when I plug it in:
```
Nov  8 19:43:34 sebastian-P552LA kernel: [  717.751435] usb 2-1: new high-speed USB device number 19 using xhci_hcdNov  8 19:43:34 sebastian-P552LA kernel: [  717.926145] usb 2-1: New USB device found, idVendor=05e3, idProduct=0610
Nov  8 19:43:34 sebastian-P552LA kernel: [  717.926147] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov  8 19:43:34 sebastian-P552LA kernel: [  717.926148] usb 2-1: Product: USB2.0 Hub
Nov  8 19:43:34 sebastian-P552LA kernel: [  717.926149] usb 2-1: Manufacturer: GenesysLogic
Nov  8 19:43:34 sebastian-P552LA kernel: [  717.926925] hub 2-1:1.0: USB hub found
Nov  8 19:43:34 sebastian-P552LA kernel: [  717.927478] hub 2-1:1.0: 4 ports detected
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.039553] usb 3-1: new SuperSpeed USB device number 12 using xhci_hcd
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.062150] usb 3-1: New USB device found, idVendor=05e3, idProduct=0617
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.062152] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.062153] usb 3-1: Product: USB3.0 Hub
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.062154] usb 3-1: Manufacturer: GenesysLogic
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.064462] hub 3-1:1.0: USB hub found
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.064831] hub 3-1:1.0: 4 ports detected
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.215423] usb 2-1.2: new high-speed USB device number 20 using xhci_hcd
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.359467] usb 2-1.2: New USB device found, idVendor=05e3, idProduct=0610
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.359469] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.359470] usb 2-1.2: Product: USB2.0 Hub
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.359471] usb 2-1.2: Manufacturer: GenesysLogic
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.360328] hub 2-1.2:1.0: USB hub found
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.360800] hub 2-1.2:1.0: 4 ports detected
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.439479] usb 3-1.2: new SuperSpeed USB device number 13 using xhci_hcd
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.461842] usb 3-1.2: New USB device found, idVendor=05e3, idProduct=0617
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.461844] usb 3-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.461845] usb 3-1.2: Product: USB3.0 Hub
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.461846] usb 3-1.2: Manufacturer: GenesysLogic
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.464923] hub 3-1.2:1.0: USB hub found
Nov  8 19:43:34 sebastian-P552LA kernel: [  718.465251] hub 3-1.2:1.0: 4 ports detected
Nov  8 19:43:35 sebastian-P552LA kernel: [  718.751716] usb 3-1.2.2: new SuperSpeed USB device number 14 using xhci_hcd
Nov  8 19:43:35 sebastian-P552LA kernel: [  718.778890] usb 3-1.2.2: New USB device found, idVendor=0b95, idProduct=1790
Nov  8 19:43:35 sebastian-P552LA kernel: [  718.778893] usb 3-1.2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Nov  8 19:43:35 sebastian-P552LA kernel: [  718.778894] usb 3-1.2.2: Product: AX88179
Nov  8 19:43:35 sebastian-P552LA kernel: [  718.778895] usb 3-1.2.2: Manufacturer: ASIX Elec.
Nov  8 19:43:35 sebastian-P552LA kernel: [  718.778896] usb 3-1.2.2: SerialNumber: 0000051BAE01D4
Nov  8 19:43:35 sebastian-P552LA NetworkManager[970]: <warn>  [1478630615.6222] device (eth0): failed to find device 6 'eth0' with udev
Nov  8 19:43:35 sebastian-P552LA NetworkManager[970]: <info>  [1478630615.6232] manager: (eth0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/5)
Nov  8 19:43:35 sebastian-P552LA kernel: [  719.112116] ax88179_178a 3-1.2.2:1.0 eth0: register 'ax88179_178a' at usb-0000:00:14.0-1.2.2, ASIX AX88179 USB 3.0 Gigabit Ethernet, 00:05:1b:ae:01:d4
Nov  8 19:43:35 sebastian-P552LA mtp-probe: checking bus 3, device 14: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.2/3-1.2.2"
Nov  8 19:43:35 sebastian-P552LA mtp-probe: bus: 3, device: 14 was not an MTP device
Nov  8 19:43:36 sebastian-P552LA kernel: [  719.859397] usb 3-1.1: new SuperSpeed USB device number 15 using xhci_hcd
Nov  8 19:43:36 sebastian-P552LA kernel: [  719.880875] usb 3-1.1: New USB device found, idVendor=0711, idProduct=5809
Nov  8 19:43:36 sebastian-P552LA kernel: [  719.880877] usb 3-1.1: New USB device strings: Mfr=1, Product=9, SerialNumber=0
Nov  8 19:43:36 sebastian-P552LA kernel: [  719.880878] usb 3-1.1: Product: USB3.0 External Graphics Device
Nov  8 19:43:36 sebastian-P552LA kernel: [  719.880879] usb 3-1.1: Manufacturer: MCT Corp.
Nov  8 19:43:36 sebastian-P552LA mtp-probe: checking bus 3, device 15: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.1"
Nov  8 19:43:36 sebastian-P552LA mtp-probe: bus: 3, device: 15 was not an MTP device
Nov  8 19:43:36 sebastian-P552LA kernel: [  719.959398] usb 3-1.2.1: new SuperSpeed USB device number 16 using xhci_hcd
Nov  8 19:43:36 sebastian-P552LA kernel: [  719.981257] usb 3-1.2.1: New USB device found, idVendor=0711, idProduct=5812
Nov  8 19:43:36 sebastian-P552LA kernel: [  719.981259] usb 3-1.2.1: New USB device strings: Mfr=1, Product=9, SerialNumber=0
Nov  8 19:43:36 sebastian-P552LA kernel: [  719.981260] usb 3-1.2.1: Product: USB3.0 External Graphics Device
Nov  8 19:43:36 sebastian-P552LA kernel: [  719.981261] usb 3-1.2.1: Manufacturer: MCT Corp.
Nov  8 19:43:36 sebastian-P552LA kernel: [  720.137823] ax88179_178a 3-1.2.2:1.0 enx00051bae01d4: renamed from eth0
Nov  8 19:43:36 sebastian-P552LA kernel: [  720.139369] usb 2-1.4: new low-speed USB device number 26 using xhci_hcd
Nov  8 19:43:36 sebastian-P552LA NetworkManager[970]: <info>  [1478630616.6695] device (eth0): interface index 6 renamed iface from 'eth0' to 'enx00051bae01d4'
Nov  8 19:43:36 sebastian-P552LA NetworkManager[970]: <info>  [1478630616.6756] devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.2/3-1.2.2/3-1.2.2:1.0/net/enx00051bae01d4, iface: enx00051bae01d4)
Nov  8 19:43:36 sebastian-P552LA NetworkManager[970]: <info>  [1478630616.6756] device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.2/3-1.2.2/3-1.2.2:1.0/net/enx00051bae01d4, iface: enx00051bae01d4): no ifupdown configuration found.
Nov  8 19:43:36 sebastian-P552LA NetworkManager[970]: <info>  [1478630616.6759] device (enx00051bae01d4): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov  8 19:43:36 sebastian-P552LA kernel: [  720.166326] IPv6: ADDRCONF(NETDEV_UP): enx00051bae01d4: link is not ready
Nov  8 19:43:36 sebastian-P552LA kernel: [  720.243076] usb 2-1.4: New USB device found, idVendor=0000, idProduct=0538
Nov  8 19:43:36 sebastian-P552LA kernel: [  720.243078] usb 2-1.4: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Nov  8 19:43:36 sebastian-P552LA kernel: [  720.243079] usb 2-1.4: Product:  USB OPTICAL MOUSE
Nov  8 19:43:36 sebastian-P552LA kernel: [  720.245927] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1.4/2-1.4:1.0/0003:0000:0538.0003/input/input23
Nov  8 19:43:36 sebastian-P552LA mtp-probe: checking bus 2, device 26: "/sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1.4"
Nov  8 19:43:36 sebastian-P552LA mtp-probe: bus: 2, device: 26 was not an MTP device
Nov  8 19:43:36 sebastian-P552LA kernel: [  720.303512] hid-generic 0003:0000:0538.0003: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:14.0-1.4/input0
Nov  8 19:43:37 sebastian-P552LA NetworkManager[970]: <info>  [1478630617.0036] keyfile: add connection in-memory (2a5a421a-ce7c-372a-8da4-85becfa3ce1d,"Wired connection 2")
Nov  8 19:43:37 sebastian-P552LA kernel: [  720.492382] IPv6: ADDRCONF(NETDEV_UP): enx00051bae01d4: link is not ready
Nov  8 19:43:37 sebastian-P552LA NetworkManager[970]: <info>  [1478630617.0043] settings: (enx00051bae01d4): created default wired connection 'Wired connection 2'
Nov  8 19:43:39 sebastian-P552LA ModemManager[1023]: <info>  Couldn't check support for device at '/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.2/3-1.2.2': not supported by any plugin
Nov  8 19:43:41 sebastian-P552LA kernel: [  725.063296] usb 3-1.2.1: 2:1: cannot get freq at ep 0x85
Nov  8 19:43:46 sebastian-P552LA kernel: [  730.183172] usb 3-1.2.1: 3:1: cannot get freq at ep 0x6
Nov  8 19:43:46 sebastian-P552LA mtp-probe: checking bus 3, device 16: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.2/3-1.2.1"
Nov  8 19:43:46 sebastian-P552LA mtp-probe: bus: 3, device: 16 was not an MTP device
Nov  8 19:43:51 sebastian-P552LA kernel: [  735.303046] usb 3-1.2.1: 2:1: cannot get freq at ep 0x85
Nov  8 19:44:02 sebastian-P552LA kernel: [  745.542796] usb 3-1.2.1: Set SEL for device-initiated U1 failed.
Nov  8 19:44:07 sebastian-P552LA kernel: [  750.662694] usb 3-1.2.1: Set SEL for device-initiated U2 failed.
Nov  8 19:44:17 sebastian-P552LA kernel: [  760.902362] usb 3-1.2.1: Set SEL for device-initiated U1 failed.
Nov  8 19:44:22 sebastian-P552LA kernel: [  766.022188] usb 3-1.2.1: Set SEL for device-initiated U2 failed.
Nov  8 19:44:22 sebastian-P552LA kernel: [  766.022192] usb 3-1.2.1: 3:1: usb_set_interface failed (-110)
Nov  8 19:44:32 sebastian-P552LA kernel: [  776.261780] usb 3-1.2.1: Set SEL for device-initiated U1 failed.
Nov  8 19:44:37 sebastian-P552LA kernel: [  781.381555] usb 3-1.2.1: Set SEL for device-initiated U2 failed.
Nov  8 19:44:37 sebastian-P552LA kernel: [  781.381558] usb 3-1.2.1: 3:1: usb_set_interface failed (-110)
Nov  8 19:44:48 sebastian-P552LA kernel: [  791.621008] usb 3-1.2.1: Set SEL for device-initiated U1 failed.
Nov  8 19:44:53 sebastian-P552LA kernel: [  796.740774] usb 3-1.2.1: Set SEL for device-initiated U2 failed.
Nov  8 19:44:53 sebastian-P552LA kernel: [  796.740782] usb 3-1.2.1: 3:1: usb_set_interface failed (-110)
Nov  8 19:45:03 sebastian-P552LA kernel: [  806.980342] usb 3-1.2.1: Set SEL for device-initiated U1 failed.
Nov  8 19:45:08 sebastian-P552LA kernel: [  812.100112] usb 3-1.2.1: Set SEL for device-initiated U2 failed.
Nov  8 19:45:08 sebastian-P552LA kernel: [  812.100114] usb 3-1.2.1: 3:1: usb_set_interface failed (-110)
Nov  8 19:45:18 sebastian-P552LA kernel: [  822.339464] usb 3-1.2.1: Set SEL for device-initiated U1 failed.

```

Also, I never got the HDMI and DVI ports working. But that's another story...

---

### Post by pontoffeltier on 2016-11-21
Also, this is my dmesg diff from before and after:

```
+[25480.678286] usb 2-3: new high-speed USB device number 7 using xhci_hcd+[25480.863527] usb 2-3: New USB device found, idVendor=05e3, idProduct=0610
+[25480.863528] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
+[25480.863530] usb 2-3: Product: USB2.0 Hub
+[25480.863531] usb 2-3: Manufacturer: GenesysLogic
+[25480.864377] hub 2-3:1.0: USB hub found
+[25480.864856] hub 2-3:1.0: 4 ports detected
+[25480.978400] usb 3-3: new SuperSpeed USB device number 2 using xhci_hcd
+[25481.001613] usb 3-3: New USB device found, idVendor=05e3, idProduct=0617
+[25481.001615] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
+[25481.001617] usb 3-3: Product: USB3.0 Hub
+[25481.001620] usb 3-3: Manufacturer: GenesysLogic
+[25481.003175] hub 3-3:1.0: USB hub found
+[25481.003462] hub 3-3:1.0: 4 ports detected
+[25481.154243] usb 2-3.2: new high-speed USB device number 8 using xhci_hcd
+[25481.303191] usb 2-3.2: New USB device found, idVendor=05e3, idProduct=0610
+[25481.303193] usb 2-3.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
+[25481.303194] usb 2-3.2: Product: USB2.0 Hub
+[25481.303195] usb 2-3.2: Manufacturer: GenesysLogic
+[25481.305096] hub 2-3.2:1.0: USB hub found
+[25481.305556] hub 2-3.2:1.0: 4 ports detected
+[25481.382475] usb 3-3.2: new SuperSpeed USB device number 3 using xhci_hcd
+[25481.405306] usb 3-3.2: New USB device found, idVendor=05e3, idProduct=0617
+[25481.405308] usb 3-3.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
+[25481.405309] usb 3-3.2: Product: USB3.0 Hub
+[25481.405310] usb 3-3.2: Manufacturer: GenesysLogic
+[25481.408862] hub 3-3.2:1.0: USB hub found
+[25481.409133] hub 3-3.2:1.0: 4 ports detected
+[25481.698526] usb 3-3.2.2: new SuperSpeed USB device number 4 using xhci_hcd
+[25481.724288] usb 3-3.2.2: New USB device found, idVendor=0b95, idProduct=1790
+[25481.724291] usb 3-3.2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
+[25481.724292] usb 3-3.2.2: Product: AX88179
+[25481.724293] usb 3-3.2.2: Manufacturer: ASIX Elec.
+[25481.724295] usb 3-3.2.2: SerialNumber: 0000051BAE01D4
+[25482.530360] usb 3-3.2.1: new SuperSpeed USB device number 5 using xhci_hcd
+[25482.552781] usb 3-3.2.1: New USB device found, idVendor=0711, idProduct=5812
+[25482.552783] usb 3-3.2.1: New USB device strings: Mfr=1, Product=9, SerialNumber=0
+[25482.552785] usb 3-3.2.1: Product: USB3.0 External Graphics Device
+[25482.552786] usb 3-3.2.1: Manufacturer: MCT Corp.
+[25482.630363] usb 3-3.1: new SuperSpeed USB device number 6 using xhci_hcd
+[25482.652400] usb 3-3.1: New USB device found, idVendor=0711, idProduct=5809
+[25482.652402] usb 3-3.1: New USB device strings: Mfr=1, Product=9, SerialNumber=0
+[25482.652404] usb 3-3.1: Product: USB3.0 External Graphics Device
+[25482.652405] usb 3-3.1: Manufacturer: MCT Corp.
+[25483.100469] ax88179_178a 3-3.2.2:1.0 eth0: register 'ax88179_178a' at usb-0000:00:14.0-3.2.2, ASIX AX88179 USB 3.0 Gigabit Ethernet, 00:05:1b:ae:01:d4
+[25483.101314] usbcore: registered new interface driver ax88179_178a
+[25483.105906] ax88179_178a 3-3.2.2:1.0 enx00051bae01d4: renamed from eth0
+[25483.142394] IPv6: ADDRCONF(NETDEV_UP): enx00051bae01d4: link is not ready
+[25483.468767] IPv6: ADDRCONF(NETDEV_UP): enx00051bae01d4: link is not ready
+[25487.794037] usb 3-3.2.1: 2:1: cannot get freq at ep 0x85



```

Please, anyone any idea?

---

### Post by pontoffeltier on 2016-11-21
Also, this is my dmesg diff from before and after:<br>
<br>
```
+[25480.678286] usb 2-3: new high-speed USB device number 7 using xhci_hcd+[25480.863527] usb 2-3: New USB device found, idVendor=05e3, idProduct=0610<br>
+[25480.863528] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0<br>
+[25480.863530] usb 2-3: Product: USB2.0 Hub<br>
+[25480.863531] usb 2-3: Manufacturer: GenesysLogic<br>
+[25480.864377] hub 2-3:1.0: USB hub found<br>
+[25480.864856] hub 2-3:1.0: 4 ports detected<br>
+[25480.978400] usb 3-3: new SuperSpeed USB device number 2 using xhci_hcd<br>
+[25481.001613] usb 3-3: New USB device found, idVendor=05e3, idProduct=0617<br>
+[25481.001615] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0<br>
+[25481.001617] usb 3-3: Product: USB3.0 Hub<br>
+[25481.001620] usb 3-3: Manufacturer: GenesysLogic<br>
+[25481.003175] hub 3-3:1.0: USB hub found<br>
+[25481.003462] hub 3-3:1.0: 4 ports detected<br>
+[25481.154243] usb 2-3.2: new high-speed USB device number 8 using xhci_hcd<br>
+[25481.303191] usb 2-3.2: New USB device found, idVendor=05e3, idProduct=0610<br>
+[25481.303193] usb 2-3.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0<br>
+[25481.303194] usb 2-3.2: Product: USB2.0 Hub<br>
+[25481.303195] usb 2-3.2: Manufacturer: GenesysLogic<br>
+[25481.305096] hub 2-3.2:1.0: USB hub found<br>
+[25481.305556] hub 2-3.2:1.0: 4 ports detected<br>
+[25481.382475] usb 3-3.2: new SuperSpeed USB device number 3 using xhci_hcd<br>
+[25481.405306] usb 3-3.2: New USB device found, idVendor=05e3, idProduct=0617<br>
+[25481.405308] usb 3-3.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0<br>
+[25481.405309] usb 3-3.2: Product: USB3.0 Hub<br>
+[25481.405310] usb 3-3.2: Manufacturer: GenesysLogic<br>
+[25481.408862] hub 3-3.2:1.0: USB hub found<br>
+[25481.409133] hub 3-3.2:1.0: 4 ports detected<br>
+[25481.698526] usb 3-3.2.2: new SuperSpeed USB device number 4 using xhci_hcd<br>
+[25481.724288] usb 3-3.2.2: New USB device found, idVendor=0b95, idProduct=1790<br>
+[25481.724291] usb 3-3.2.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3<br>
+[25481.724292] usb 3-3.2.2: Product: AX88179<br>
+[25481.724293] usb 3-3.2.2: Manufacturer: ASIX Elec.<br>
+[25481.724295] usb 3-3.2.2: SerialNumber: 0000051BAE01D4<br>
+[25482.530360] usb 3-3.2.1: new SuperSpeed USB device number 5 using xhci_hcd<br>
+[25482.552781] usb 3-3.2.1: New USB device found, idVendor=0711, idProduct=5812<br>
+[25482.552783] usb 3-3.2.1: New USB device strings: Mfr=1, Product=9, SerialNumber=0<br>
+[25482.552785] usb 3-3.2.1: Product: USB3.0 External Graphics Device<br>
+[25482.552786] usb 3-3.2.1: Manufacturer: MCT Corp.<br>
+[25482.630363] usb 3-3.1: new SuperSpeed USB device number 6 using xhci_hcd<br>
+[25482.652400] usb 3-3.1: New USB device found, idVendor=0711, idProduct=5809<br>
+[25482.652402] usb 3-3.1: New USB device strings: Mfr=1, Product=9, SerialNumber=0<br>
+[25482.652404] usb 3-3.1: Product: USB3.0 External Graphics Device<br>
+[25482.652405] usb 3-3.1: Manufacturer: MCT Corp.<br>
+[25483.100469] ax88179_178a 3-3.2.2:1.0 eth0: register 'ax88179_178a' at usb-0000:00:14.0-3.2.2, ASIX AX88179 USB 3.0 Gigabit Ethernet, 00:05:1b:ae:01:d4<br>
+[25483.101314] usbcore: registered new interface driver ax88179_178a<br>
+[25483.105906] ax88179_178a 3-3.2.2:1.0 enx00051bae01d4: renamed from eth0<br>
+[25483.142394] IPv6: ADDRCONF(NETDEV_UP): enx00051bae01d4: link is not ready<br>
+[25483.468767] IPv6: ADDRCONF(NETDEV_UP): enx00051bae01d4: link is not ready<br>
+[25487.794037] usb 3-3.2.1: 2:1: cannot get freq at ep 0x85<br>
<br>
<br>

```<br><br>Please, anyone any idea?

---

