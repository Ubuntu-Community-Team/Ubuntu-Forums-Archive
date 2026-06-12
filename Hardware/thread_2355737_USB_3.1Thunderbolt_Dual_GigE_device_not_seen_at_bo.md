---
title: "USB 3.1/Thunderbolt Dual GigE device not seen at boot"
date: 2017-03-16
forum: Hardware
---

### Post by walaj on 2017-03-16
I've built an Intel NUC with Ubuntu 16.04 LTS (Linux JonLabNUC 4.4.0-67-generic #88-Ubuntu SMP Wed Mar 8 16:34:45 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux) and I'm trying to add two more ethernet ports.

I've got a USB 3.1/Thunderbolt Dual GigE device by StarTech.com (USB-C to Dual Gigabit Ethernet Adapter with SUB (Type A) Port.

If I boot with the device connected, it isn't seen - unplugging or replugging has no impact:

```

walaj@JonLabNUC:~$ dmesg --human|grep 4-1
[  +0.103599] usb 4-1: new SuperSpeed USB device number 2 using xhci_hcd
[  +0.018552] usb 4-1: New USB device found, idVendor=2109, idProduct=8110
[  +0.000811] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  +0.000816] usb 4-1: Product: USB3.0 Hub
[  +0.000801] usb 4-1: Manufacturer: VIA Labs, Inc.
[  +0.002771] hub 4-1:1.0: USB hub found
[  +0.001144] hub 4-1:1.0: 4 ports detected
[  +0.205852] usb 4-1.1: new SuperSpeed USB device number 3 using xhci_hcd
[  +0.023280] usb 4-1.1: New USB device found, idVendor=0b95, idProduct=1790
[  +0.000648] usb 4-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  +0.000592] usb 4-1.1: Product: AX88179
[  +0.000602] usb 4-1.1: Manufacturer: ASIX Elec. Corp.
[  +0.000598] usb 4-1.1: SerialNumber: 00000000000797
[  +0.015773] usb 4-1.2: new SuperSpeed USB device number 4 using xhci_hcd
[  +0.023169] usb 4-1.2: New USB device found, idVendor=0b95, idProduct=1790
[  +0.000661] usb 4-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  +0.000631] usb 4-1.2: Product: AX88179
[  +0.000621] usb 4-1.2: Manufacturer: ASIX Elec. Corp.
[  +0.000627] usb 4-1.2: SerialNumber: 00000000000796
[  +0.529190] usb 4-1.1: Failed to set U1 timeout to 0x0,error code -110
[  +2.409894] usb 4-1.1: Set SEL for device-initiated U1 failed.
[  +5.000089] usb 4-1.1: Set SEL for device-initiated U2 failed.
[  +0.000003] ax88179_178a 4-1.1:1.0: usb_probe_interface Failed to disable LPM for driver ax88179_178a
[  +0.001013] ax88179_178a: probe of 4-1.1:1.0 failed with error -16
[  +0.999001] usb 4-1.2: Failed to set U1 timeout to 0x0,error code -110
[  +5.000142] usb 4-1.2: Set SEL for device-initiated U1 failed.
[  +5.000032] usb 4-1.2: Set SEL for device-initiated U2 failed.
[  +0.000004] ax88179_178a 4-1.2:1.0: usb_probe_interface Failed to disable LPM for driver ax88179_178a
[  +0.001047] ax88179_178a: probe of 4-1.2:1.0 failed with error -16

```

If I add once boot has finished it is seen:

```
[ 2138.363461] xhci_hcd 0000:3c:00.0: xHCI Host Controller
[ 2138.363465] xhci_hcd 0000:3c:00.0: new USB bus registered, assigned bus number 3
[ 2138.364594] xhci_hcd 0000:3c:00.0: hcc params 0x200077c1 hci version 0x110 quirks 0x00009810
[ 2138.364700] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[ 2138.364701] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 2138.364702] usb usb3: Product: xHCI Host Controller
[ 2138.364703] usb usb3: Manufacturer: Linux 4.4.0-67-generic xhci-hcd
[ 2138.364704] usb usb3: SerialNumber: 0000:3c:00.0
[ 2138.364857] hub 3-0:1.0: USB hub found
[ 2138.364867] hub 3-0:1.0: 2 ports detected
[ 2138.365036] xhci_hcd 0000:3c:00.0: xHCI Host Controller
[ 2138.365038] xhci_hcd 0000:3c:00.0: new USB bus registered, assigned bus number 4
[ 2138.365058] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[ 2138.365059] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 2138.365060] usb usb4: Product: xHCI Host Controller
[ 2138.365061] usb usb4: Manufacturer: Linux 4.4.0-67-generic xhci-hcd
[ 2138.365062] usb usb4: SerialNumber: 0000:3c:00.0
[ 2138.365253] hub 4-0:1.0: USB hub found
[ 2138.365275] hub 4-0:1.0: 2 ports detected
[ 2138.676886] usb 3-1: new high-speed USB device number 2 using xhci_hcd
[ 2138.806825] usb 3-1: New USB device found, idVendor=2109, idProduct=2811
[ 2138.806832] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2138.806836] usb 3-1: Product: USB2.0 Hub
[ 2138.806839] usb 3-1: Manufacturer: VIA Labs, Inc.
[ 2138.807899] hub 3-1:1.0: USB hub found
[ 2138.808827] hub 3-1:1.0: 4 ports detected
[ 2138.917078] usb 4-1: new SuperSpeed USB device number 2 using xhci_hcd
[ 2138.935670] usb 4-1: New USB device found, idVendor=2109, idProduct=8110
[ 2138.935673] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2138.935675] usb 4-1: Product: USB3.0 Hub
[ 2138.935676] usb 4-1: Manufacturer: VIA Labs, Inc.
[ 2138.937947] hub 4-1:1.0: USB hub found
[ 2138.938203] hub 4-1:1.0: 4 ports detected
[ 2139.309232] usb 4-1.1: new SuperSpeed USB device number 3 using xhci_hcd
[ 2139.331698] usb 4-1.1: New USB device found, idVendor=0b95, idProduct=1790
[ 2139.331706] usb 4-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2139.331711] usb 4-1.1: Product: AX88179
[ 2139.331715] usb 4-1.1: Manufacturer: ASIX Elec. Corp.
[ 2139.331718] usb 4-1.1: SerialNumber: 00000000000797
[ 2139.409204] usb 4-1.2: new SuperSpeed USB device number 4 using xhci_hcd
[ 2139.431910] usb 4-1.2: New USB device found, idVendor=0b95, idProduct=1790
[ 2139.431917] usb 4-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2139.431921] usb 4-1.2: Product: AX88179
[ 2139.431925] usb 4-1.2: Manufacturer: ASIX Elec. Corp.
[ 2139.431928] usb 4-1.2: SerialNumber: 00000000000796
[ 2139.677232] ax88179_178a 4-1.1:1.0 eth0: register 'ax88179_178a' at usb-0000:3c:00.0-1.1, ASIX AX88179 USB 3.0 Gigabit Ethernet, e8:ea:6a:12:52:db
[ 2139.760989] ax88179_178a 4-1.2:1.0 eth1: register 'ax88179_178a' at usb-0000:3c:00.0-1.2, ASIX AX88179 USB 3.0 Gigabit Ethernet, e8:ea:6a:12:52:da
[ 2139.761982] usbcore: registered new interface driver ax88179_178a
[ 2139.763810] ax88179_178a 4-1.1:1.0 enxe8ea6a1252db: renamed from eth0
[ 2139.777162] ax88179_178a 4-1.2:1.0 enxe8ea6a1252da: renamed from eth1
```

and

```
[ 4041.117142] usb 4-1: USB disconnect, device number 2
[ 4041.117146] usb 4-1.1: USB disconnect, device number 3
[ 4041.117235] ax88179_178a 4-1.1:1.0 enxe8ea6a1252db: unregister 'ax88179_178a' usb-0000:3c:00.0-1.1, ASIX AX88179 USB 3.0 Gigabit Ethernet
[ 4041.134190] ax88179_178a 4-1.1:1.0 enxe8ea6a1252db (unregistered): Failed to write reg index 0x0002: -19
[ 4041.134193] ax88179_178a 4-1.1:1.0 enxe8ea6a1252db (unregistered): Failed to write reg index 0x0001: -19
[ 4041.134194] ax88179_178a 4-1.1:1.0 enxe8ea6a1252db (unregistered): Failed to write reg index 0x0002: -19
[ 4041.135886] xhci_hcd 0000:3c:00.0: remove, state 1
[ 4041.135892] usb usb4: USB disconnect, device number 1
[ 4046.147202] xhci_hcd 0000:3c:00.0: Stopped the command ring failed, maybe the host is dead
[ 4046.147237] xhci_hcd 0000:3c:00.0: Host not halted after 16000 microseconds.
[ 4046.147238] xhci_hcd 0000:3c:00.0: Abort command ring failed
[ 4046.147256] xhci_hcd 0000:3c:00.0: HC died; cleaning up
[ 4046.147275] xhci_hcd 0000:3c:00.0: Timeout while waiting for configure endpoint command
[ 4046.147326] usb 3-1: USB disconnect, device number 2
[ 4046.147481] usb 4-1.2: USB disconnect, device number 4
[ 4046.147519] ax88179_178a 4-1.2:1.0 enxe8ea6a1252da: unregister 'ax88179_178a' usb-0000:3c:00.0-1.2, ASIX AX88179 USB 3.0 Gigabit Ethernet
[ 4046.174306] ax88179_178a 4-1.2:1.0 enxe8ea6a1252da (unregistered): Failed to write reg index 0x0002: -19
[ 4046.174315] ax88179_178a 4-1.2:1.0 enxe8ea6a1252da (unregistered): Failed to write reg index 0x0001: -19
[ 4046.174320] ax88179_178a 4-1.2:1.0 enxe8ea6a1252da (unregistered): Failed to write reg index 0x0002: -19
[ 4046.175221] xhci_hcd 0000:3c:00.0: Host not halted after 16000 microseconds.
[ 4046.176233] xhci_hcd 0000:3c:00.0: USB bus 4 deregistered
[ 4046.176250] xhci_hcd 0000:3c:00.0: remove, state 4
[ 4046.176266] usb usb3: USB disconnect, device number 1
[ 4046.176856] xhci_hcd 0000:3c:00.0: USB bus 3 deregistered
[ 4046.177799] pci_bus 0000:06: busn_res: [bus 06] is released
[ 4046.198300] pci_bus 0000:07: busn_res: [bus 07-3b] is released
[ 4046.254251] pci_bus 0000:3c: busn_res: [bus 3c] is released
[ 4046.270264] pci_bus 0000:05: busn_res: [bus 05-3c] is released
```



Of course this is no good if I need the 2nd and 3rd ports to be up after boot with no physical access.

SO - why isn't it being seen at boot?

---

### Post by walaj on 2017-04-10
Anyone? Happy to do some digging - just need to know what to do!

---

