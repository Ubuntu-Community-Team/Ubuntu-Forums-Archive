---
title: "Bluetooth transfer speeds of ~50KB/sec"
date: 2020-11-07
forum: Hardware
---

### Post by mikeymikec on 2020-11-07
A quick google suggests that this is a pretty slow transfer speed?

Dmesg output:
```

[ 8007.255365] usb 3-7.1.3: new full-speed USB device number 8 using xhci_hcd
[ 8007.358537] usb 3-7.1.3: New USB device found, idVendor=050d, idProduct=016a
[ 8007.358538] usb 3-7.1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 8007.358540] usb 3-7.1.3: Product: BLUETOOTH USB +EDR ADAPTER v2.1 UHE
[ 8007.358540] usb 3-7.1.3: Manufacturer: Broadcom Corp
[ 8007.358541] usb 3-7.1.3: SerialNumber: 00190E08033B
[ 8007.384201] Bluetooth: Core ver 2.22
[ 8007.384215] NET: Registered protocol family 31
[ 8007.384216] Bluetooth: HCI device and connection manager initialized
[ 8007.384219] Bluetooth: HCI socket layer initialized
[ 8007.384220] Bluetooth: L2CAP socket layer initialized
[ 8007.384225] Bluetooth: SCO socket layer initialized
[ 8007.394971] usbcore: registered new interface driver btusb
[ 8007.409305] usb 3-7.1.1: input irq status -75 received
[ 8007.425309] usb 3-7.1.1: input irq status -75 received
[ 8007.441308] usb 3-7.1.1: input irq status -75 received
[ 8007.457309] usb 3-7.1.1: input irq status -75 received
[ 8007.458726] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 8007.458727] Bluetooth: BNEP filters: protocol multicast
[ 8007.458730] Bluetooth: BNEP socket layer initialized
[ 8007.473310] usb 3-7.1.1: input irq status -75 received
[ 8007.489311] usb 3-7.1.1: input irq status -75 received
[ 8007.505310] usb 3-7.1.1: input irq status -75 received
[ 8007.521316] usb 3-7.1.1: input irq status -75 received
[ 8007.537319] usb 3-7.1.1: input irq status -75 received
[ 8007.553307] usb 3-7.1.1: input irq status -75 received
[ 8007.569314] usb 3-7.1.1: input irq status -75 received
[ 8007.585321] usb 3-7.1.1: input irq status -75 received
[ 8012.799348] Bluetooth: RFCOMM TTY layer initialized
[ 8012.799352] Bluetooth: RFCOMM socket layer initialized
[ 8012.799356] Bluetooth: RFCOMM ver 1.11
[ 8068.242710] NET: Registered protocol family 38

```

I'm not sure how old the Bluetooth adapter is.

---

### Post by CelticWarrior on 2020-11-07
```
[COLOR=#000000][FONT=&quot]Product: BLUETOOTH USB +EDR ADAPTER v2.1 UHE[/FONT][/COLOR]
```

[It's a 2007 standard.]("https://en.wikipedia.org/wiki/Bluetooth#Bluetooth_2.1_+_EDR")

---

### Post by mikeymikec on 2020-11-07
Thanks for that information.  Though 3Mbit/sec suggests about 300KB/sec throughput?

---

