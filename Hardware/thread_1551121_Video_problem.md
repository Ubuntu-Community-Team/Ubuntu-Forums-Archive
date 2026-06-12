---
title: "Video problem"
date: 2010-08-11
forum: Hardware
---

### Post by K8JWT on 2010-08-11
When I run Ubuntu on my desktop computer (fresh install as of 8/10/2010) Every 3 hours or so the video just quits working and I have to do a hard reboot to get the video back for a few more hours then it happens again.

I have ran the same computer on Windows XP PRO and Windows Server 2008 and never had this problem.

Any idea why this is doing this???:(

---

### Post by wojox on 2010-08-11
Do you mean like your video driver locks up and the mouse and keyboard become unresponsive?

---

### Post by K8JWT on 2010-08-11
After some further checking I found this information about my video system.


VGA compatible controller	Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

---

### Post by K8JWT on 2010-08-11
Some more information:

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

$ sudo lshw -C video
[sudo] password for jacob: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f7ffffff(prefetchable) memory:fc400000-fc47ffff

---

### Post by K8JWT on 2010-08-11
Not like that but the video stops putting out a video signal.

Everything else keeps working fine.

The monitor even displays that there is no video signal coming from the computer.

Tried some fixes from the Ubuntu Video help site but did not work. Dealing mostly with the drivers. 

This is a old refurbished desktop computer from Tigerdirect.com so the video system is not that new that U10.04 should not have a good driver for it.

Jake

---

### Post by wojox on 2010-08-12
Try installing [Caffeine]("https://launchpad.net/~caffeine-developers/+archive/ppa") and see if that makes a difference.

---

### Post by K8JWT on 2010-08-12
Will try that tonight after I get home from work.

Thank you

Jake

---

