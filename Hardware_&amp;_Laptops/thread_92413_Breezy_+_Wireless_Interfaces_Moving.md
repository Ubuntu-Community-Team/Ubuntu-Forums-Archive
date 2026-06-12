---
title: "Breezy + Wireless Interfaces Moving"
date: 2005-11-19
forum: Hardware &amp; Laptops
---

### Post by ksaling on 2005-11-19
Just finished the upgrade from **Hoary to Breezy** with no incidents on my **IBM Thinkpad T40 laptop**.  However, I just noticed the **built-in Cisco Aironet wireless** interface (uses the airo module) is behaving strangely.

*Of course, the airo module creates two virtual interfaces.  One for normal wireless use and one for wireless "monitor" mode (sniffing). *

On Hoary the module always mapped liked this:
[FONT="Courier New"][B] - eth0 (e1000 module) wired ethernet
 - eth1 (airo module) NORMAL WIRELESS interface
 - wlan0 (airo module) wireless monitor interface[/B][/FONT]

On Breezy it's behaving differently.  At boot up the module maps like this:
[FONT="Courier New"][B] - eth0 (e1000 module) wired ethernet
 - eth1 (airo module) NORMAL WIRELESS interface
 - eth3 (airo module) wireless monitor interface[/B][/FONT]

Even worse, if I [FONT="Courier New"]**`rmmod airo`**[/FONT] and later [FONT="Courier New"]**`modprobe airo`**[/FONT] the mappings change to this:
[FONT="Courier New"] [B]- eth0 (e1000 module) wired ethernet
 - eth1 (airo module) wireless monitor interface
 - eth2 (airo module) NORMAL WIRELESS interface[/B][/FONT]

Argh!  This is causing problems with my handy location scripts when the interface names keep changing!  **How can I pin this down?**

---

### Post by ksaling on 2005-11-19
Changing /etc/iftab to this fixed it:
 eth0 mac 00:0d:60:##:##:##
 eth1 mac 00:02:8a:##:##:## arp 1

So, it all ends up like this:
 - eth0 (e1000 module) wired ethernet
 - eth1 (airo module) NORMAL WIRELESS interface
 - wifi0 (airo module) wireless monitor interface

Best of all, my location scripts are happy again!

---

