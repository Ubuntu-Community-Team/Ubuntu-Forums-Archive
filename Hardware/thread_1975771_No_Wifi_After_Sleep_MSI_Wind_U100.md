---
title: "No Wifi After Sleep MSI Wind U100"
date: 2012-05-07
forum: Hardware
---

### Post by pSYcl0Ne on 2012-05-07
MSI Wind U100+ with Ralink RT2700E on 12.04 32bit.

The problem was also present in 10.04 - but I was able to fix it by editing /etc/modprobe.d/blacklist-rt2800.conf and adding
# This is to fix wifi on the MSI Wind with the Ralink RT2700E.
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib

But blacklist-rt2800.conf is no longer there.

---

