---
title: "occasional freezing during &quot;Detecting Hardware&quot; on bootup"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by Beanalby on 2007-01-02
I have Ubuntu 6.10 installed on a Dell Latitude LS, works fine overall.  Sometimes when booting it will freeze at the "Detecting Hardware..." stage (I've left it for hours), and will require a reboot to get past, sometimes multiple times.

My hardware debugging is limited; I only know how to collect diagnostic info with dmesg & such after a successful boot, so it doesn't have any errors in it.

Are there any boot flags I can give that could shed more light on what exactly it's hanging on, or a way to disable the graphical boot screen so I can see more verbose output?

Thanks
Bean

---

### Post by dmartinsca on 2007-01-03
Do you have an Intel 3945abg wireless adapter in your latitude? I have read a couple of times that the wireless switch being off during boot can cause lockups. Personally I have one of these wireless adapters and have experienced lockups during boot when the switch is off (but it is a switch which slides to the side then springs back, there is a led indicating whether it is on or off). I don't know at what point it locks up, the ubuntu splash screen with the orange progress bar simply freezes forever.

---

### Post by Beanalby on 2007-01-03
> **dmartinsca said:**
> Do you have an Intel 3945abg wireless adapter in your latitude?

Nope.  There's no built-in wireless, and I use a Belkin PCMCIA b/g card (can't remember model off the top of my head), have the problem whether that's plugged in or not.

Thanks though.

---

