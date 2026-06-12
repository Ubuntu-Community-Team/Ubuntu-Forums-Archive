---
title: "Video drivers not loaded correctly?"
date: 2016-10-18
forum: Hardware
---

### Post by Joost_Plas on 2016-10-18
I'm using a Gigabyte Brix 3205 (HD Graphics) as a standalone box for playing Google Chrome in kiosk mode.
Specs:
Ubuntu 14.04.5
4.1.6-01-04016-generic
OpenBox 3.5.2
Compton 

At this moment playing any video content is sky rocketing the CPU usage and the performance is terrible. In the past I had this problem intermittently (on some boots it was fine, and on some it was terrible). Currently the problem is there on all boots.
Looks to me that the proper drivers are not loaded. Unfortunately I have no idea how to debug this. I attached all the logs I thought were relevant. Anyone any tips how I can dive deeper in the problem based on this?

dmesg:
[http://pastebin.com/QWzenUFC](http://pastebin.com/QWzenUFC)

boot.log:
[http://pastebin.com/YqkYtmMk](http://pastebin.com/YqkYtmMk)

Xorg.0.log:
[http://pastebin.com/ANSMXTfP](http://pastebin.com/ANSMXTfP)

kern.log:
[http://pastebin.com/sf4dRLu0](http://pastebin.com/sf4dRLu0)

---

