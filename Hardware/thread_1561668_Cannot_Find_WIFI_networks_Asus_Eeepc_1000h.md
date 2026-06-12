---
title: "Cannot Find WIFI networks Asus Eeepc 1000h"
date: 2010-08-26
forum: Hardware
---

### Post by Leigen_Zero on 2010-08-26
Hey guys, long time since an issue came up so be gentle!

So I've just installed the latest Ubuntu NBR on my Asus Eeepc100-h, after switching from Eeebuntu (now Aurora, as yet unreleased).  Everything is fine except for one issue:

My WIFI card seems to be recognised and functioning, however it cannot see any wireless networks (despite being on the opposite end of a desk to the router).

lshw -C network gives me:
```

*-network
    description: Wireless interface
    product: RT2860
    vendor: RaLink
    physical id: 0
    bus_info: pci@0000:01:00.0
    logical name: wlan0
    version: 00
    serial: 00:22:43:6e:13:08
    width: 32 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
    configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
    resources: irq:19 memory:fbef0000 fbefffff
```

and iwconfig shows:
```

lo    no wireless extention
eth0  no wireless extention
wlan0 RT2860 Wireless ESSID="" Nickname="RT2860STA"
      Mode:Auto Frequency=2.412GHz Bit Rate=1Mb/s
      RTS thr:off Fragment thr:off
      Link Quality 10/100 Signal Level:0 dBm Noise Level: -87dBm
      Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
      Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```

Have googled around and such, but can only find references to cards not working at all, not card is working fine but can't find the network, ethernet works swimmingly.  Any help is much appreciated!

---

