---
title: "Ath9k intermittent wifi connection"
date: 2013-02-03
forum: Hardware
---

### Post by tereshkosg on 2013-02-03
Hi can someone point me to a right direction, I have an Aspire v3-571g laptop with:

```
03:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)
```

Wifi works ... sort of :(

Wifi could be stable for several hours or several minutes, but then an avalanche of re-connects happen almost every 30 secs to 1 minute. Kern.log contains: 

```
dmesg -T | grep Found

[Sun Feb  3 10:46:06 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:46:11 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:46:18 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:46:23 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:46:58 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:47:05 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:47:10 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:47:21 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:47:26 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:48:08 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:48:45 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:50:39 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:51:17 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:52:05 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:52:13 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:52:57 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:53:57 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:54:57 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:55:47 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 10:56:53 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 11:15:10 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 11:19:10 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0
[Sun Feb  3 11:19:26 2013] cfg80211: Found new beacon on frequency: 5825 MHz (Ch 165) on phy0



```

could someone help with an advise, the wifi is almost unusable during these episodes.

---

