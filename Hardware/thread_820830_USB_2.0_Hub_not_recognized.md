---
title: "USB 2.0 Hub not recognized"
date: 2008-06-06
forum: Hardware
---

### Post by bignickel on 2008-06-06
I bought a USB 2.0 hub to replace my old 1.0 hub because I wanted to get better speeds off of my external drive.  It doesn't seem to be recognized properly though.  Here's the dmesg output:

```
[  172.995995] usb 2-1: new full speed USB device using uhci_hcd and address 7
[  173.115816] usb 2-1: device descriptor read/64, error -71
[  173.339728] usb 2-1: device descriptor read/64, error -71
[  173.443790] usb 2-1: new full speed USB device using uhci_hcd and address 8
[  173.448215] usb 2-1: device descriptor read/64, error -71
[  173.457784] usb 2-1: device descriptor read/64, error -71
[  173.465553] usb 2-1: new full speed USB device using uhci_hcd and address 9
[  173.479401] usb 2-1: device not accepting address 9, error -71
[  173.483025] usb 2-1: new full speed USB device using uhci_hcd and address 10
[  173.498520] usb 2-1: device not accepting address 10, error -71
```

I'm running Hardy on an Apple TV.  Everything's been updated including the kernel and still no luck.  Should this be working?  I kind of assumed it would and didn't check any hardware specs before I bought it.

---

### Post by cwmoser on 2008-09-06
I bought a USB Hub extender and getting similar dmesg output:

[232959.706074] usb 5-4.1: device descriptor read/64, error -71
[232959.869564] usb 5-4.1: device descriptor read/64, error -71
[232960.032398] usb 5-4.1: new high speed USB device using ehci_hcd and address 41
[232960.060167] usb 5-4.1: configuration #1 chosen from 1 choice
[232960.060718] hub 5-4.1:1.0: USB hub found
[232960.060988] hub 5-4.1:1.0: 1 port detected
[232960.329902] usb 5-4.1.1: new high speed USB device using ehci_hcd and address 42
[232960.393814] usb 5-4.1.1: device descriptor read/64, error -71
[232960.557526] usb 5-4.1.1: device descriptor read/64, error -71
[232960.720374] usb 5-4.1.1: new high speed USB device using ehci_hcd and address 43
[232960.783518] usb 5-4.1.1: device descriptor read/64, error -71
[232960.947142] usb 5-4.1.1: device descriptor read/64, error -71
[232961.110107] usb 5-4.1.1: new high speed USB device using ehci_hcd and address 44
[232961.511122] usb 5-4.1.1: device not accepting address 44, error -71
[232961.573200] usb 5-4.1.1: new high speed USB device using ehci_hcd and address 45
[232961.974756] usb 5-4.1.1: device not accepting address 45, error -71


I got my thumb drive to work but my Western Digital USB hard drive is not recognized.

Carl

---

