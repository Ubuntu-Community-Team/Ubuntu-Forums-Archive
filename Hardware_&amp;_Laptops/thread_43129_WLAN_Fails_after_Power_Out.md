---
title: "WLAN Fails after Power Out"
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by dpod on 2005-06-20
I ran into a problem with my wlan access this morning after my battery ran down on me: I can't get my wlan back up. I am using an ACER Aspire 1410 notebook. My Wireless card is an Airconn Inprocom IPN 2220. It has worked well with WPA_PSK until the problem this morning. Before the battery died, I had internet access (I was browsing when it died).

I've tried rebooting; turning things off and waiting; ifdown and ifup, removing and restarting wla_supplicant. Nothing seems to work.

When I run iwconfig I get the following:

```

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:56/154  Noise level:0/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I've been reading around, and one suggestion seems to be that the power is off on  wlan0 and that I need to wake it up. I've looked into doing this, but can't seem to find a solution that works: acerhk (a hot key program for Acer) doesn't have one specifically for my model. I can't get it to work anyway.

Any suggestions, similar experiences? Nothing whatsoever changed on my system except for the battery running out of juice.

-d ](*,)

---

### Post by Davor281 on 2005-06-21
Did you try to reset the ESSID of your WLAN adapter? In your iwconfig ESSID is not set.
The command is - iwconfig wlan0 ESSID "your ESSID name here"


ENjoY!

Davor.

---

