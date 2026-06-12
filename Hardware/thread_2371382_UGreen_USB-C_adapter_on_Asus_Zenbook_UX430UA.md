---
title: "UGreen USB-C adapter on Asus Zenbook UX430UA"
date: 2017-09-14
forum: Hardware
---

### Post by abpabab on 2017-09-14
I'm using Ubuntu 17.04 and trying to connect my UGreen USB-C Adapter (UGreen 30440) to my laptop. The OS see the adapter for a while and disconnect immediately. In /var/log/kern.log:

```
Sep 13 13:36:09 System911 kernel: [ 1474.712617] usb 2-4: new SuperSpeed USB device number 2 using xhci_hcd
Sep 13 13:36:09 System911 kernel: [ 1474.819432] usb 2-4: New USB device found, idVendor=2109, idProduct=0210
Sep 13 13:36:09 System911 kernel: [ 1474.819435] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 13 13:36:09 System911 kernel: [ 1474.819438] usb 2-4: Product: USB3.0 Hub             
Sep 13 13:36:09 System911 kernel: [ 1474.819440] usb 2-4: Manufacturer: VIA Labs, Inc.         
Sep 13 13:36:09 System911 kernel: [ 1474.821492] hub 2-4:1.0: USB hub found
Sep 13 13:36:09 System911 kernel: [ 1474.821954] hub 2-4:1.0: 1 port detected
Sep 13 13:36:09 System911 kernel: [ 1474.936215] usb 1-4: new high-speed USB device number 7 using xhci_hcd
Sep 13 13:36:09 System911 kernel: [ 1475.223833] usb 1-4: New USB device found, idVendor=2109, idProduct=2210
Sep 13 13:36:09 System911 kernel: [ 1475.223837] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 13 13:36:09 System911 kernel: [ 1475.223840] usb 1-4: Product: USB2.0 Hub             
Sep 13 13:36:09 System911 kernel: [ 1475.223842] usb 1-4: Manufacturer: VIA Labs, Inc.         
Sep 13 13:36:09 System911 kernel: [ 1475.226241] hub 1-4:1.0: USB hub found
Sep 13 13:36:09 System911 kernel: [ 1475.226341] hub 1-4:1.0: 4 ports detected
Sep 13 13:36:10 System911 kernel: [ 1475.772273] usb 1-4.2: new high-speed USB device number 8 using xhci_hcd
Sep 13 13:36:10 System911 kernel: [ 1475.887993] usb 1-4.2: New USB device found, idVendor=0b95, idProduct=772a
Sep 13 13:36:10 System911 kernel: [ 1475.887997] usb 1-4.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep 13 13:36:10 System911 kernel: [ 1475.888000] usb 1-4.2: Product: AX88772A
Sep 13 13:36:10 System911 kernel: [ 1475.888002] usb 1-4.2: Manufacturer: ASIX Elec. Corp.
Sep 13 13:36:10 System911 kernel: [ 1475.888004] usb 1-4.2: SerialNumber: 000366
Sep 13 13:36:10 System911 kernel: [ 1476.332295] asix 1-4.2:1.0 eth0: register 'asix' at usb-0000:00:14.0-4.2, ASIX AX88772 USB 2.0 Ethernet, 00:0e:c6:d2:14:51
Sep 13 13:36:10 System911 kernel: [ 1476.332361] usbcore: registered new interface driver asix
Sep 13 13:36:10 System911 kernel: [ 1476.337397] asix 1-4.2:1.0 enx000ec6d21451: renamed from eth0
Sep 13 13:36:10 System911 kernel: [ 1476.375640] IPv6: ADDRCONF(NETDEV_UP): enx000ec6d21451: link is not ready
Sep 13 13:36:10 System911 kernel: [ 1476.380174] IPv6: ADDRCONF(NETDEV_UP): enx000ec6d21451: link is not ready
Sep 13 13:36:11 System911 kernel: [ 1477.224284] usb 1-4.3: new high-speed USB device number 9 using xhci_hcd
Sep 13 13:36:12 System911 kernel: [ 1477.719396] usb 1-4.3: New USB device found, idVendor=2109, idProduct=0100
Sep 13 13:36:12 System911 kernel: [ 1477.719402] usb 1-4.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep 13 13:36:12 System911 kernel: [ 1477.719406] usb 1-4.3: Product: USB 2.0 BILLBOARD             
Sep 13 13:36:12 System911 kernel: [ 1477.719409] usb 1-4.3: Manufacturer: VIA Technologies Inc.         
Sep 13 13:36:12 System911 kernel: [ 1477.719412] usb 1-4.3: SerialNumber: 0000000000000001
Sep 13 13:36:13 System911 kernel: [ 1479.277160] usb 1-4: USB disconnect, device number 7
Sep 13 13:36:13 System911 kernel: [ 1479.277164] usb 1-4.2: USB disconnect, device number 8
Sep 13 13:36:13 System911 kernel: [ 1479.277379] asix 1-4.2:1.0 enx000ec6d21451: unregister 'asix' usb-0000:00:14.0-4.2, ASIX AX88772 USB 2.0 Ethernet
Sep 13 13:36:13 System911 kernel: [ 1479.293403] usb 1-4.3: USB disconnect, device number 9
Sep 13 13:36:13 System911 kernel: [ 1479.384920] usb 2-4: USB disconnect, device number 2


```

How can I know what exactly problem is?

---

