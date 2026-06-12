---
title: "Intel Wireless 5300 incorrectly recoginized as 5100"
date: 2009-04-18
forum: Hardware
---

### Post by tian.hack on 2009-04-18
I'm running Ubuntu 8.10 on Thinkpad X200.  I chose the Intel Wireless 5300 during purchase, and under Windows, it correctly shows up as 5300.  However, 'lshw' / 'lspci' lists it as 5100.  Is this due to some mis-configuration or should I upgrade the driver?  Help appreciated!

Here is part of the output from 'lshw -class network':
```
 *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:6a:04:3f:e0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.100 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn 
```

---

### Post by tian.hack on 2009-04-29
am i the only x200 owner experiencing this problem?  can anyone shed some light?  thanks!

---

### Post by HankB on 2009-04-29
When I first got my T500 I had the same issue. Well... At the moment lspci and lshw still ID it as a 5100. However the driver properly IDs it as 5300. From dmesg:
```
[   22.101089] iwlagn: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
```

So as long as the driver knows what the H/W is, I think all is well.

-hank

---

### Post by tian.hack on 2009-04-30
i got it.  thank you, HankB!

---

