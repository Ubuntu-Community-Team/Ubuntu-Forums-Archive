---
title: "Microtek ScanMaker 4850 not detected by Sane (no success with wiki manual)"
date: 2015-12-04
forum: Hardware
---

### Post by Socza on 2015-12-04
Hi,

the Microtek ScanMaker 4850 scanner isn't officially supported by Sane, but the [wiki has instructions how to get it working](https://help.ubuntu.com/community/CheckIfScannerIsClone#Example_.232.2C_microtek_scan_maker_3800_4850). Unfortunately, after following them, ```
sudo sane-find-scanners -L
``` says 'No scanners were identified.'

```
lsusb
``` contains
```
Bus 002 Device 003: ID 05da:30d9 Microtek International, Inc. USB2400 Scanner
```

For the record, I am doing that with Xubuntu 14.04 in a VirtualBox (5.0.10).

Was that manual never working (fixed a typo in the device id) or did it break?

Thank you

---

