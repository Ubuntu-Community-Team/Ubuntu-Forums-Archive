---
title: "USB WiFi"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by markr on 2005-11-29
I'm looking for a new USB WiFI stick that will just work in Ubuntu/Linux.  I'm using NDISWrapper at the moment, but can't get it to work with 686smp and I think it is causing me some other problems as well.

What I want is a USB WiFI stick that will work natively in Ubuntu/Linux (without using NDISWrapper).

Any recommendations?

Thanks

Mark.

---

### Post by ukiechris on 2005-12-01
Check out D-Link AirPlus G Wireless Network Starter Kit
Model: DWL-922

Package includes: DI-524 & DWL-G122 The USB adapter is based on the Ralink chipset, who has been very helpful with the open-source community to release GPL drivers, so Linux users should be able to get drivers for the USB stick fairly easily, as apposed to most other USB wifi adapters.

There are current rebates for this bundle through Best Buy. Come up to $14.99 plus tax

[http://forums.slickdeals.net/showthread.php?t=160228&highlight=dlink](http://forums.slickdeals.net/showthread.php?t=160228&highlight=dlink)

---

### Post by unbc_kozijn on 2005-12-02
I bought the DWL-922 Kit about 6 months ago. while ukiechris was correct in saying the DWL-G122 is part of this kit, The hardware version I got was a model A2 (which is not a Ralink chipset). I think it is an Intersil Prism. Of course, Dlink is famous for different chipset versions under the same model number-- so beware.

---

### Post by shof2k on 2005-12-02
Safecom SLW5400 based on ZD1211 chipset is not bad.  The delivered driver works on an open network and with WEP encryption, but if you'll need to download a driver if you want WPA.

Hope that helps

---

### Post by unbc_kozijn on 2005-12-03
I just finished installing my D-Link DWL-G122.A2 USB adapter that was included in DWL-922C router-adapter kit. It did not take me very long. I downloaded the newest ndiswrapper1.6 package from sourceforge, which worked with the PRISMA02.inf and PRISMA.sys drivers included with the hardware. Note, I used the .sys driver that was contained in the XP directory. The other .sys file included in the same directory as the .inf folder hung my computer.

---

