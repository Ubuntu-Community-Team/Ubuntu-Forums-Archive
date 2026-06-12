---
title: "UPS shows as &quot;empty&quot;"
date: 2012-11-20
forum: Hardware
---

### Post by Hans83VT on 2012-11-20
Hi there,

I have a CyberPower CP1350PFCLCD UPS plugged into my computer via USB.  I am running Ubuntu 12.04.1, fully updated.

The battery panel at the top of the screen shows the UPS is always empty, and when I go into the Power Settings panel, it says exactly that:  Uninterruptable Power Supply - Empty.

The Power Statistics app does recognize I have a UPS, and even gives a time to empty of 49 minutes.

I tried downloading the CyberPower software for Linux, which allows the PC to shut off correctly during a power outage, but it doesn't fix the fact that the icon doesn't tell me if the battery is charged.

Any ideas? Thanks!

---

### Post by ahallubuntu on 2012-11-20
When you unplug the UPS from the wall and let it run the computer on battery, does Ubuntu show it as a battery (like a laptop)?  If so, you can set it to shut off when the battery is critically low in power preferences.

---

### Post by Hans83VT on 2012-11-20
Yes, Ubuntu understands it is a UPS and identifies it as such.  I can set it to turn off when power is critical.  The problem is that it doesn't show me any sort of battery charge info and instead says the UPS is "empty"

---

### Post by ahallubuntu on 2012-11-21
The UPS interface I've seen in other versions of Ubuntu is similar to a laptop.  When I am running my laptop on battery power, it shows me that the battery has X hours remaining.  Are you saying when you are running your UPS on the battery, the Ubuntu server doesn't have this same information?  (If not, it won't know to shut  down when the battery becomes "criticial.")

Otherwise, you may not be able to get this information directly from the UPS, but you may not need it if you can see the info I mention above.

---

### Post by Hans83VT on 2012-11-21
Yes, it is the same interface as when you have a laptop battery but it recognizes that it is a UPS.  However, instead of giving a charge level for the battery, it says the UPS is Empty.

---

