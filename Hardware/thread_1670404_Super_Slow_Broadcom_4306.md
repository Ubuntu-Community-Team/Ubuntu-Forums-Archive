---
title: "Super Slow Broadcom 4306"
date: 2011-01-18
forum: Hardware
---

### Post by fishinman on 2011-01-18
Hello,

This has probably been dealt with but I can't find the answer..

I have a Compaq Presario using the Broadcom 4306 wireless chipset. I have successfully got it working and talking to my network and the internet. Many thanks to this forum.

However it seemed slow so I ran the bandwidth test at speedtest.net multiple times and the result is around 1 to 1.25 Mbps. When I check speedtest.net from the desktop I'm using with the Netgear WG311v3 and ndiswrapper I consistently get from 18 to +20 Mbps (at about a 30-50% signal as reported by iwlist).

sudo iwlist scan

Both are running Ubuntu 10.10 32-bit.

The laptop is using the b43/b43legacy drivers (no ndiswrapper). I checked this by:

modprobe -r b43
modprobe -r b43legacy

I then re-enabed and re-connected.

I also looked for the Broadcom STA driver to see if it was installed and it was not:
modprobe -r wl

I can set the laptop next to the wireless router and get a 90-100% signal so I don't think that is the problem. 

Is there a better driver (the Broadcom STA) or some hardware conflict to look for or something else which could be gumming up the works?

I know the hardware is somewhat old but I would expect better than 1 Mbps.

---

