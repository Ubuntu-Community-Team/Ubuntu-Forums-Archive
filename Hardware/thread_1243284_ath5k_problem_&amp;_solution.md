---
title: "ath5k problem &amp; solution"
date: 2009-08-18
forum: Hardware
---

### Post by katletz on 2009-08-18
Hi ubuntu users,

I had the problem with the ath5k drivers for my atheros wlan card on 9.04. It flooded my log file with "ath5k phy0: noise floor calibration timeout" errors. Strangly wlan still worked for me, only (the messages or the driver) slowed down my machine considerably (I already thought about going back to 8.04).

I could enable the madwifi drivers through System->Administration->Hardware Drivers. Only the NetworkManager Applet won't support the wireless interface anymore, so now I am using Wifi-radar.

There seems to be a patch available for ath5k. Maybe someone at Canonical could include it in the next kernel update? Or how can I use NetworkManager with the madwifi drivers (this was possible in older releases)?

Jaunty on an Asus P4_L3C
2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

description: Wireless interface
                product: Atheros AR5001X+ Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: wifi0
                version: 01
                serial: xx:xx:xx:xx:xx:xx
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.1.24 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

---

