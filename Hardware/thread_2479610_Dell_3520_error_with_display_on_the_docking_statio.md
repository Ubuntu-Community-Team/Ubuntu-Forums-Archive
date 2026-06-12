---
title: "Dell 3520 error with display on the docking station"
date: 2022-09-30
forum: Hardware
---

### Post by darosm1 on 2022-09-30
Hello, 
I have problem with my Dell 3520 and doc station DELL P2422HE.
Connect with USB-C. 
Version Ubuntu 20.04 

After starting the laptop in the docking station, the device starts up but does not read the monitor. After disconnecting and reconnecting, the system starts detecting the monitor (DP-1) and then everything works.
LAN, USB works from the beginning.
I am asking for help in solving the problem.

```
Sep 30 07:26:23 lubuntu kernel: [  417.912290] usb 2-1: USB disconnect, device number 10
Sep 30 07:26:23 lubuntu kernel: [  417.912294] usb 2-1.3: USB disconnect, device number 11
Sep 30 07:26:23 lubuntu kernel: [  418.184783] usb 3-2: new high-speed USB device number 11 using xhci_hcd
Sep 30 07:26:24 lubuntu kernel: [  418.335709] usb 3-2: New USB device found, idVendor=0424, idProduct=2806, bcdDevice= 2.10
Sep 30 07:26:24 lubuntu kernel: [  418.335713] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 30 07:26:24 lubuntu kernel: [  418.335715] usb 3-2: Product: USB2806 Smart Hub
Sep 30 07:26:24 lubuntu kernel: [  418.335717] usb 3-2: Manufacturer: Microchip
Sep 30 07:26:24 lubuntu kernel: [  418.336913] hub 3-2:1.0: USB hub found
Sep 30 07:26:24 lubuntu kernel: [  418.336969] hub 3-2:1.0: 6 ports detected
Sep 30 07:26:24 lubuntu kernel: [  419.064779] usb 3-2.6: new high-speed USB device number 12 using xhci_hcd
Sep 30 07:26:24 lubuntu kernel: [  419.168667] usb 3-2.6: New USB device found, idVendor=0424, idProduct=284c, bcdDevice= 2.00
Sep 30 07:26:24 lubuntu kernel: [  419.168670] usb 3-2.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 30 07:26:24 lubuntu kernel: [  419.168672] usb 3-2.6: Product: Hub Feature Controller
Sep 30 07:26:24 lubuntu kernel: [  419.168674] usb 3-2.6: Manufacturer: Microchip
Sep 30 07:26:24 lubuntu kernel: [  419.171927] hid-generic 0003:0424:284C.0007: hiddev0,hidraw1: USB HID v1.10 Device [Microchip Hub Feature Controller] on usb-0000:00:14.0-2.6/input1
Sep 30 07:26:24 lubuntu kernel: [  419.256773] usb 2-1: new SuperSpeed Gen 1 USB device number 12 using xhci_hcd
Sep 30 07:26:24 lubuntu kernel: [  419.277201] usb 2-1: New USB device found, idVendor=0424, idProduct=5806, bcdDevice= 2.10
Sep 30 07:26:24 lubuntu kernel: [  419.277204] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 30 07:26:24 lubuntu kernel: [  419.277206] usb 2-1: Product: USB5806 Smart Hub
Sep 30 07:26:24 lubuntu kernel: [  419.277208] usb 2-1: Manufacturer: Microchip
Sep 30 07:26:24 lubuntu kernel: [  419.278134] hub 2-1:1.0: USB hub found
Sep 30 07:26:24 lubuntu kernel: [  419.278480] hub 2-1:1.0: 5 ports detected
Sep 30 07:26:27 lubuntu kernel: [  421.440993] usb 2-1.3: new SuperSpeed Gen 1 USB device number 13 using xhci_hcd
Sep 30 07:26:27 lubuntu kernel: [  421.461600] usb 2-1.3: New USB device found, idVendor=0bda, idProduct=8153, bcdDevice=31.00
Sep 30 07:26:27 lubuntu kernel: [  421.461604] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=6
Sep 30 07:26:27 lubuntu kernel: [  421.461606] usb 2-1.3: Product: USB 10/100/1000 LAN
Sep 30 07:26:27 lubuntu kernel: [  421.461608] usb 2-1.3: Manufacturer: Realtek
Sep 30 07:26:27 lubuntu kernel: [  421.461609] usb 2-1.3: SerialNumber: 001000001
Sep 30 07:26:27 lubuntu kernel: [  421.540987] usb 2-1.3: reset SuperSpeed Gen 1 USB device number 13 using xhci_hcd
Sep 30 07:26:27 lubuntu kernel: [  421.564587] r8152 2-1.3:1.0 (unnamed net_device) (uninitialized): Using pass-thru MAC addr b4:45:06:26:f1:dc
Sep 30 07:26:27 lubuntu kernel: [  421.581083] r8152 2-1.3:1.0: load rtl8153b-2 v1 10/23/19 successfully
Sep 30 07:26:27 lubuntu kernel: [  421.615426] r8152 2-1.3:1.0 eth0: v1.11.11
Sep 30 07:26:27 lubuntu kernel: [  421.664494] r8152 2-1.3:1.0 enxb4450626f1dc: renamed from eth0
Sep 30 07:26:28 lubuntu kernel: [  423.274027] usb 3-2: USB disconnect, device number 11
Sep 30 07:26:28 lubuntu kernel: [  423.274032] usb 3-2.6: USB disconnect, device number 12
Sep 30 07:26:29 lubuntu kernel: [  423.365584] r8152 2-1.3:1.0 enxb4450626f1dc: Stop submitting intr, status -71
Sep 30 07:26:29 lubuntu kernel: [  424.032858] usb 2-1: USB disconnect, device number 12
Sep 30 07:26:29 lubuntu kernel: [  424.032863] usb 2-1.3: USB disconnect, device number 13
Sep 30 07:26:37 lubuntu kernel: [  431.796790] usb 3-2: new high-speed USB device number 13 using xhci_hcd
Sep 30 07:26:37 lubuntu kernel: [  431.947541] usb 3-2: New USB device found, idVendor=0424, idProduct=2806, bcdDevice= 2.10
Sep 30 07:26:37 lubuntu kernel: [  431.947545] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 30 07:26:37 lubuntu kernel: [  431.947547] usb 3-2: Product: USB2806 Smart Hub
Sep 30 07:26:37 lubuntu kernel: [  431.947549] usb 3-2: Manufacturer: Microchip
Sep 30 07:26:37 lubuntu kernel: [  431.949752] hub 3-2:1.0: USB hub found
Sep 30 07:26:37 lubuntu kernel: [  431.949821] hub 3-2:1.0: 6 ports detected
Sep 30 07:26:37 lubuntu kernel: [  432.093185] usb 3-2: USB disconnect, device number 13
Sep 30 07:26:37 lubuntu kernel: [  432.107686] usb 2-1: Device not responding to setup address.
Sep 30 07:26:38 lubuntu kernel: [  432.312896] usb 2-1: new SuperSpeed Gen 1 USB device number 14 using xhci_hcd
Sep 30 07:26:38 lubuntu kernel: [  432.333538] usb 2-1: New USB device found, idVendor=0424, idProduct=5806, bcdDevice= 2.10
Sep 30 07:26:38 lubuntu kernel: [  432.333542] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 30 07:26:38 lubuntu kernel: [  432.333545] usb 2-1: Product: USB5806 Smart Hub
Sep 30 07:26:38 lubuntu kernel: [  432.333547] usb 2-1: Manufacturer: Microchip
Sep 30 07:26:38 lubuntu kernel: [  432.334453] hub 2-1:1.0: USB hub found
Sep 30 07:26:38 lubuntu kernel: [  432.334494] hub 2-1:1.0: 5 ports detected
Sep 30 07:26:38 lubuntu kernel: [  432.404675] usb 3-2: new high-speed USB device number 14 using xhci_hcd
Sep 30 07:26:38 lubuntu kernel: [  432.558811] usb 3-2: New USB device found, idVendor=0424, idProduct=2806, bcdDevice= 2.10
Sep 30 07:26:38 lubuntu kernel: [  432.558815] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 30 07:26:38 lubuntu kernel: [  432.558817] usb 3-2: Product: USB2806 Smart Hub
Sep 30 07:26:38 lubuntu kernel: [  432.558818] usb 3-2: Manufacturer: Microchip
Sep 30 07:26:38 lubuntu kernel: [  432.559814] hub 3-2:1.0: USB hub found
Sep 30 07:26:38 lubuntu kernel: [  432.559844] hub 3-2:1.0: 6 ports detected
Sep 30 07:26:38 lubuntu kernel: [  433.044836] usb 2-1.3: new SuperSpeed Gen 1 USB device number 15 using xhci_hcd
Sep 30 07:26:38 lubuntu kernel: [  433.065618] usb 2-1.3: New USB device found, idVendor=0bda, idProduct=8153, bcdDevice=31.00
Sep 30 07:26:38 lubuntu kernel: [  433.065622] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=6
Sep 30 07:26:38 lubuntu kernel: [  433.065624] usb 2-1.3: Product: USB 10/100/1000 LAN
Sep 30 07:26:38 lubuntu kernel: [  433.065626] usb 2-1.3: Manufacturer: Realtek
Sep 30 07:26:38 lubuntu kernel: [  433.065627] usb 2-1.3: SerialNumber: 001000001
Sep 30 07:26:38 lubuntu kernel: [  433.149072] usb 2-1.3: reset SuperSpeed Gen 1 USB device number 15 using xhci_hcd
Sep 30 07:26:38 lubuntu kernel: [  433.172756] r8152 2-1.3:1.0 (unnamed net_device) (uninitialized): Using pass-thru MAC addr b4:45:06:26:f1:dc
Sep 30 07:26:38 lubuntu kernel: [  433.188890] r8152 2-1.3:1.0: load rtl8153b-2 v1 10/23/19 successfully
Sep 30 07:26:38 lubuntu kernel: [  433.223700] r8152 2-1.3:1.0 eth0: v1.11.11
Sep 30 07:26:38 lubuntu kernel: [  433.268677] usb 3-2.6: new high-speed USB device number 15 using xhci_hcd
Sep 30 07:26:39 lubuntu kernel: [  433.373067] usb 3-2.6: New USB device found, idVendor=0424, idProduct=284c, bcdDevice= 2.00
Sep 30 07:26:39 lubuntu kernel: [  433.373071] usb 3-2.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 30 07:26:39 lubuntu kernel: [  433.373073] usb 3-2.6: Product: Hub Feature Controller
Sep 30 07:26:39 lubuntu kernel: [  433.373075] usb 3-2.6: Manufacturer: Microchip
Sep 30 07:26:39 lubuntu kernel: [  433.376431] hid-generic 0003:0424:284C.0008: hiddev0,hidraw1: USB HID v1.10 Device [Microchip Hub Feature Controller] on usb-0000:00:14.0-2.6/input1
Sep 30 07:26:39 lubuntu kernel: [  433.428706] r8152 2-1.3:1.0 enxb4450626f1dc: renamed from eth0
Sep 30 07:26:43 lubuntu kernel: [  437.741100] IPv6: ADDRCONF(NETDEV_CHANGE): enxb4450626f1dc: link becomes ready
Sep 30 07:26:43 lubuntu kernel: [  437.741635] r8152 2-1.3:1.0 enxb4450626f1dc: carrier on
```

---

