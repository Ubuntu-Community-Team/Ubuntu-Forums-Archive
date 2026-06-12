---
title: "USB Disconnect Message Repeatedly Occur"
date: 2017-04-07
forum: Hardware
---

### Post by sikpigs on 2017-04-07
Hi,

I have a Dell XPS 9550 with a Dell WD-15 and I am consistently seeing USB disconnect messages in system logs. These disconnects also resets any connections to peripherals on the bus, including a Realtek Ethernet port. These disconnects seem to happen randomly, here is the output from dmesg.

```

[14004.372415] r8152 4-1.2:1.0 enx847beb4e129e: Stop submitting intr, status -71
[14004.548870] usb 4-1: USB disconnect, device number 39
[14004.548874] usb 4-1.2: USB disconnect, device number 40
[14004.904964] usb 4-1: new SuperSpeed USB device number 41 using xhci_hcd
[14004.925296] usb 4-1: New USB device found, idVendor=0424, idProduct=5537
[14004.925300] usb 4-1: New USB device strings: Mfr=2, Product=3, SerialNumber=0
[14004.925303] usb 4-1: Product: USB5537B
[14004.925306] usb 4-1: Manufacturer: SMSC
[14004.926286] hub 4-1:1.0: USB hub found
[14004.926313] hub 4-1:1.0: 7 ports detected
[14005.212902] usb 4-1.2: new SuperSpeed USB device number 42 using xhci_hcd
[14005.233312] usb 4-1.2: New USB device found, idVendor=0bda, idProduct=8153
[14005.233316] usb 4-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=6
[14005.233319] usb 4-1.2: Product: USB 10/100/1000 LAN
[14005.233321] usb 4-1.2: Manufacturer: Realtek
[14005.233324] usb 4-1.2: SerialNumber: 000001000000
[14005.317254] usb 4-1.2: reset SuperSpeed USB device number 42 using xhci_hcd
[14005.339808] r8152 4-1.2:1.0 (unnamed net_device) (uninitialized): Using pass-thru MAC addr 84:7b:eb:4e:12:9e
[14005.393615] r8152 4-1.2:1.0 eth0: v1.08.6
[14006.434139] r8152 4-1.2:1.0 enx847beb4e129e: renamed from eth0
[14006.471031] IPv6: ADDRCONF(NETDEV_UP): enx847beb4e129e: link is not ready
[14006.499228] IPv6: ADDRCONF(NETDEV_UP): enx847beb4e129e: link is not ready
[14008.929893] IPv6: ADDRCONF(NETDEV_CHANGE): enx847beb4e129e: link becomes ready
[14047.380908] r8152 4-1.2:1.0 enx847beb4e129e: Stop submitting intr, status -71
[14047.556156] usb 4-1: USB disconnect, device number 41
[14047.556158] usb 4-1.2: USB disconnect, device number 42
[14047.912291] usb 4-1: new SuperSpeed USB device number 43 using xhci_hcd
[14047.932563] usb 4-1: New USB device found, idVendor=0424, idProduct=5537
[14047.932568] usb 4-1: New USB device strings: Mfr=2, Product=3, SerialNumber=0
[14047.932571] usb 4-1: Product: USB5537B
[14047.932574] usb 4-1: Manufacturer: SMSC
[14047.933562] hub 4-1:1.0: USB hub found
[14047.933588] hub 4-1:1.0: 7 ports detected
[14048.224339] usb 4-1.2: new SuperSpeed USB device number 44 using xhci_hcd
[14048.245020] usb 4-1.2: New USB device found, idVendor=0bda, idProduct=8153
[14048.245024] usb 4-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=6
[14048.245027] usb 4-1.2: Product: USB 10/100/1000 LAN
[14048.245030] usb 4-1.2: Manufacturer: Realtek
[14048.245032] usb 4-1.2: SerialNumber: 000001000000
[14048.328746] usb 4-1.2: reset SuperSpeed USB device number 44 using xhci_hcd
[14048.351530] r8152 4-1.2:1.0 (unnamed net_device) (uninitialized): Using pass-thru MAC addr 84:7b:eb:4e:12:9e
[14048.405111] r8152 4-1.2:1.0 eth0: v1.08.6
[14049.462074] r8152 4-1.2:1.0 enx847beb4e129e: renamed from eth0
[14049.507414] IPv6: ADDRCONF(NETDEV_UP): enx847beb4e129e: link is not ready
[14049.534436] IPv6: ADDRCONF(NETDEV_UP): enx847beb4e129e: link is not ready
[14051.858389] IPv6: ADDRCONF(NETDEV_CHANGE): enx847beb4e129e: link becomes ready

```

Does anybody else have a similar issues? Perhaps there's a fix or workaround?

Thanks

---

