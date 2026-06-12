---
title: "WPA works but ARP doesn't?"
date: 2006-04-10
forum: Hardware &amp; Laptops
---

### Post by GarBhaD on 2006-04-10
My WLAN consists of:
-Desktop with D-Link DWL-G520 (atheros, uses madwifi), static IP, Ubuntu Breezy
-Laptop with D-Link DWL-G650 (atheros, uses madwifi), static IP, Ubuntu Breezy
-PDA, DHCP, Windows Mobile 2003

I installed wpasupplicant following the [WPAHOWTO]("https://wiki.ubuntu.com/WPAHowto") in both ubuntu systems. Apparently, everything worked fine: I had internet access on all 3 devices with WPA encryption enabled. Until I tried to ping the laptop from the desktop: host unreachable. (note that this did not happen before installing wpasupplicant and enabling WPA)

The laptop can't reach the desktop and viceversa, but the weird thing is that both CAN reach the PDA. If I run arp in my desktop, the HWaddress for the laptop says 'incomplete' (and the opposite when running arp in the laptop).
I tried to fill the arp table manually using 'arp -s' and then they can reach each other again!
Why is that?

---

### Post by GarBhaD on 2006-07-08
In the end, I had to disable wpasupplicant and now I use WEP :(

---

