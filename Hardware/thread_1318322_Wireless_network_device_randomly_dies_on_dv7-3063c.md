---
title: "Wireless network device randomly dies on dv7-3063cl on Ubuntu 9.10"
date: 2009-11-07
forum: Hardware
---

### Post by Andrew.Z on 2009-11-07
I just bought a dv7-3063cl with Windows 7 and installed Kubuntu 9.10 (Karmic Koala, 64-bit), **but after a few minutes (and especially after closing the lid and suspending to RAM), the wireless dies.  KDE keeps asking me for the password, which I know is right, and the network won't come back up until I reboot the PC**.  Windows 7 doesn't have this problem, and my router is fine because I have 3 other wifi devices working perfectly.


lspci shows

08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

The driver is ath9k.


I don't see anything interesting in the log


```
$sudo grep -E "(ath|lan|eth)" /var/log/messages
Nov  7 11:36:13 dv7 kernel: [    1.184548] device-mapper: multipath: version 1.1.0 loaded
Nov  7 11:36:13 dv7 kernel: [    1.184550] device-mapper: multipath round-robin: version 1.0.0 loaded
Nov  7 11:36:13 dv7 kernel: [    1.634960] eth0: RTL8102e at 0xffffc90000676000, 00:26:9e:56:86:4d, XID 24c00000 IRQ 28
Nov  7 11:36:13 dv7 kernel: [    6.123139] ath9k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov  7 11:36:13 dv7 kernel: [    6.718436] Registered led device: ath9k-phy0::radio
Nov  7 11:36:13 dv7 kernel: [    6.718449] Registered led device: ath9k-phy0::assoc
Nov  7 11:36:13 dv7 kernel: [    6.718461] Registered led device: ath9k-phy0::tx
Nov  7 11:36:13 dv7 kernel: [    6.718473] Registered led device: ath9k-phy0::rx
Nov  7 11:36:16 dv7 kernel: [   10.171314] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  7 11:36:16 dv7 kernel: [   10.210367] r8169: eth0: link down
Nov  7 11:36:16 dv7 kernel: [   10.210837] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov  7 11:36:55 dv7 kernel: [   48.849816] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

---

