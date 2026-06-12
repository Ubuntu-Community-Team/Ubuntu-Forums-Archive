---
title: "How to make GPS work on HP Mini 5102 (Qualcomm Gobi 2000)"
date: 2010-11-28
forum: Hardware
---

### Post by mtinman on 2010-11-28
I have an HP Mini 5102, running Ubuntu 10.10 netbook remix, with the Qualcomm Gobi 2000 WWAN/GPS chipset. The chipset appears to be detected & the drivers loaded:

```
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:231d Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 03f0:241d Hewlett-Packard Gobi 2000 Wireless Modem (QDL mode)
Bus 001 Device 004: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
dmesg |grep -i qcs
[   15.325605] qcserial 1-5:1.1: Qualcomm USB modem converter detected
[   15.330216] usbcore: registered new interface driver qcserial
```

However, when I use GPSDrive or SWScanner from the repos, I get no gps response. How do I fix this, if possible? Thanks in advance.

---

