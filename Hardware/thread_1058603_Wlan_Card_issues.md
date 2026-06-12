---
title: "Wlan Card issues"
date: 2009-02-03
forum: Hardware
---

### Post by dhavalbbhatt on 2009-02-03
Hi,
I seem to be having an interesting problem. I recently bought a laptop (HP dv5-1004nr, Windows Vista 64bit, Atheros wlan card 5007). I did a clean install of Ubuntu 8.10 64bit and used the How to from <http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/#comment-796> to get the wlan working. The wlan works fine (basically detecting the wireless network allowing me to connect to the internet at the right speeds), until it stops working unexpectedly (I don&#8217;t reboot my machine or anything). The wlan won&#8217;t even work in Windows at this point (basically, the card can&#8217;t find any wireless networks, even when they are working on my other [Apple] laptop). My first guess was that Windows disables (un-installs) the wlan card (or maybe it might even be Ubuntu). I run the Windows recovery CD and everything starts working fine at that point (basically, the wireless card can detect all available wireless networks and I can now connect to the internet again).

Anyone knows / has similar experience? I was wondering if someone can shed any light on the above issue. I don&#8217;t want to be running the Vista recovery CD every day or two.

Thanks,
Dhaval

---

### Post by Crafty Kisses on 2009-02-03
When the wireless card stops working, run this command and post the results back here on the forums:
```
iwconfig
```

---

### Post by dhavalbbhatt on 2009-02-03
> **Codename said:**
> When the wireless card stops working, run this command and post the results back here on the forums:
```
iwconfig
```

Basically, the iwconfig result is the same as when my wireless card detects the wireless networks, except that the ESSID won't be detected (which is obvious since I can't see networks). I have tried to simulate the iwconfig output below =

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point:   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=  Signal level:-  Noise level=-
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The above essentially tells me that the wlan card is being detected by the kernel, but somehow, I can't turn it on (or enable it) to detect any wireless networks.

---

