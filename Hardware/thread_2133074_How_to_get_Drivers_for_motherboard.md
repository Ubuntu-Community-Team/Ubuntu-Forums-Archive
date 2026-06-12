---
title: "How to get Drivers for motherboard"
date: 2013-04-06
forum: Hardware
---

### Post by SMO787 on 2013-04-06
So i plan on building a linux gaming machine and ive been wondering how to get drivers for the motherboard that i'm going to be purchasing. I've read most times the standard drivers that are already on the board work fine but i was wondering if this is true or not plus i also heard they're not called drivers they're actually called kernals. I would love a nice big explanation since i am fairly new to linux and would much appreciate an in depth response. The mothernoard i plan on buying is an ASRock 970 Extreme3 AM3+ AMD 970 SATA 6Gb/s USB 3.0 ATX

---

### Post by sanderj on 2013-04-07
The only additional drivers you *might* need:
- LAN
- WLAN
- GPU

Only LAN is on that mobo: a Realtek RTL8111E. Realtek is normally supported by the kernel, and no need for additional drivers

HTH

---

### Post by SMO787 on 2013-04-08
Ok thanks so i only need drivers for the LAN. I should be able to get those right from Realteks site right becuase i know ASrock doesn't give out linux drivers right now. And i have a graphics card right now that's Nvidia do you know any common problems that i might want to look out for with Nvidia cards?

---

### Post by sanderj on 2013-04-08
My guess is that you do NOT need separate drivers for your LAN; I expect it to work with a standard Ubuntu Linux kernel.

Easy way: live-boot a Ubuntu CD/USB-key on the system, and see if it all works.

---

### Post by Mark Phelps on 2013-04-08
Go to the following link to look for RealTek LAN Linux drivers:

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2")

---

