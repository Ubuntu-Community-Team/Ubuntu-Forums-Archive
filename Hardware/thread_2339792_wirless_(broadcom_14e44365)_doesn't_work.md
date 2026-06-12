---
title: "wirless (broadcom 14e4:4365) doesn't work"
date: 2016-10-12
forum: Hardware
---

### Post by britton-kerin on 2016-10-12
I've gotten as far as making lshw -C network show it, the output includes this line:

     configuration:driver=bcma-pci-bridge latency=0

lsmod list b43 and bcma.  But sudo iwconfig shows only:

     enp7s0      no wireless extensions.

     lo               no wireless extensions.

Which doesn't look good.  No higher layer offers any working wireless options.
This document:

     [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers)

gives no indication what to try if sudo iwconfig shows wrong stuff and I haven't found
anything else that indicates what to try next.

Any clues?

Britton

---

### Post by wildmanne39 on 2016-10-12
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

