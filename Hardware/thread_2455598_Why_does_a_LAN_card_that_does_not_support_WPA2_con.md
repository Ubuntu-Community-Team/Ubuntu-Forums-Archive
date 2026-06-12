---
title: "Why does a LAN card that does not support WPA2 connect to WPA3?"
date: 2020-12-23
forum: Hardware
---

### Post by korea1 on 2020-12-23
My laptop LAN card is Intel AC8265, This LAN card only supports WPA2, but I wonder why WPA3 is connected.
(N150UA2 (MT7601) LAN card can also be connected to WPA3.)


The router setting is only set to WPA3, not WPA2/WPA3 mode.


Does Linux support WPA3 connection even for LAN cards that do not support WPA3?
Or is my router a security flaw?


(Android, Windows could not connect to WPA3.)
Router model: AX2004BCM (WI-Fi 6)

[ATTACH=CONFIG]287609[/ATTACH]

---

### Post by #&amp;thj^% on 2020-12-23
According to the Wi-Fi Alliance, devices supporting WPA3 was released later in 2018. Qualcomm is already making chips for phones and tablets that supports WPA3, but it&#8217;ll take a while for them to be integrated into new devices. Devices must be certified for WPA3 to roll out these features&#8212;in other words, they must apply for and be granted the &#8220;Wi-Fi CERTIFIED&#8482; WPA3&#8482;&#8221; mark&#8212;so you&#8217;ll likely start seeing this logo on new routers and other wireless devices beginning in 2018.

[B]Even when you get a WPA3-enabled router, you&#8217;ll need WPA3-compatible client devices&#8212;your laptop, phone, and anything else that connects to Wi-Fi&#8212;to fully take advantage of these new features. The good news is that the same router can accept both WPA2 and WPA3 connections at the same time. 
[/B]
Network Manager version:
```
network-manager:
  Installed: 1.22.10-1ubuntu2.2
  Candidate: 1.22.10-1ubuntu2.2
  Version table:
 *** 1.22.10-1ubuntu2.2 500
        500 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.22.10-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu focal/main amd64 Packages

``` is ready for WPA3

---

