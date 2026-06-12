---
title: "Wifi not connecting to any network"
date: 2011-09-23
forum: Hardware
---

### Post by Gohansan on 2011-09-23
So, I've been using Ubuntu for about a year now as my daily driver (on this machine anyway), but some weeks ago, an update got pushed through which completely messed up my wireless, which now refuses to connect to any network. Any idea what could have gone wrong? I suspect something has been messed up driver wise, but I'm not sure.

Laptop: Toshiba Equium A300d 13x
Wireless: Realtek
Running Ubuntu 11.04, everything up to date.
Lastly, here's my lshw output:

  *-network:0
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan0
       serial: 00:16:44:ce:c3:c2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=2.6.38-11-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg

---

### Post by An Sanct on 2011-09-24
I have the same problem with Oneiric, the update from 18th broke my USB WiFi key (LevelONE - rtl8187 based)

I did hear, that you can "fix" this by downgrading some package, so if anyone has any info, please let us two know. I can post more info, if needed.

PS. I also am connected with a cable - ethernet 100Mb, that is "gone" too, both from Oneiric and Maverick ... strange!

---

### Post by Gohansan on 2011-10-07
Bump, because this is getting silly :/
> I did hear, that you can "fix" this by downgrading some package, so if anyone has any info, please let us two know. I can post more info, if needed.
More info on this would be much appreciated!

---

