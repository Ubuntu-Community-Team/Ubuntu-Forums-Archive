---
title: "Scanner not working on USB3 ports"
date: 2014-05-15
forum: Hardware
---

### Post by mla.rue on 2014-05-15
My scanner (tried 4 different scanners) do not work when plugged to an USB 3.0 port (mice, keyboard, printer... tried at least a dozen... do).

```
lsusb:
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse (M-BT58)
Bus 003 Device 005: ID 04c5:11fc Fujitsu, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 2232:1029  
Bus 002 Device 003: ID 8087:07da Intel Corp. 

```

```
/var/log/messages
2014-05-15T08:44:24.288351+02:00 linux kernel: [ 2767.070042] usb 3-2: new high-speed USB device number 5 using xhci_hcd
2014-05-15T08:44:24.306331+02:00 linux kernel: [ 2767.088918] usb 3-2: New USB device found, idVendor=04c5, idProduct=11fc
2014-05-15T08:44:24.306363+02:00 linux kernel: [ 2767.088924] usb 3-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
2014-05-15T08:44:24.306537+02:00 linux kernel: [ 2767.089136] usb 3-2: ep 0x81 - rounding interval to 128 microframes, ep desc says 255 microframes
2014-05-15T08:44:24.306578+02:00 linux kernel: [ 2767.089145] usb 3-2: ep 0x2 - rounding interval to 128 microframes, ep desc says 255 microframes
```

sane-find-scanners also finds the scanner all the time
scanimage runs once, a second time it just do not find any device (this means for every scan I have to unplug the scanner)

It works just fine on USB 2.0 ports.

To me it appears to be a driver problem (sane), but I would hope there is a "work around"... like disabling usb 3.0 and turn it to 2.0 (when the motherboard does not support this function).

Thanks for reading, maybe you also have a solution :)

---

