---
title: "Laptop crashes randonly - but only when undocked"
date: 2008-10-18
forum: Hardware
---

### Post by lnajt on 2008-10-18
When I have my Dell Latitude Laptop docked it is fine, but after I unlock it the computer sometimes crashes randomly.

When it crashes these things happen:

1. Everything locks up (The screen image remains the same though)
2. The Caps Lock and Scroll Lock buttons flash on and off at regular intervals
3. I am forced to hard reboot my computer.

I looked around on the forums here for a while, and I discovered that in many cases (that is, all of the ones I saw) this had to do with a wireless card from RaLink. My Wireless card is not from RaLink. It is from Broadcom, and here is the output of lspci | grep Network:

0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

I have installed the drivers for this device using Ndiswrapper.

Does anyone know how to overcome this particular problem?

Thanks

P.S. My computer also crashes if I undock and then redock it. Is it possible that these problems are related?

---

### Post by Benchrest on 2008-11-13
I may have the same problem. locks up with caps lock light blinking and must power off by holding down the power button. I have 8.04 . This did not occur on 7.04 . It happens at differnt times and differnt applications, but one that happens most is if the microwave get turned on. Now the microwave being turned on might cause a wireless connection failure but shouldn't cause a system freeze. I have a broadcom wireless. This occurs about once every two or three hours of operation. I am going to search launchpad bugs page as I can't seem to find a resolution here. The failure is a little difficult to describe exactly.

---

### Post by sharon.gmc on 2008-11-13
from my experience, i just unplug the microwave . . .

---

