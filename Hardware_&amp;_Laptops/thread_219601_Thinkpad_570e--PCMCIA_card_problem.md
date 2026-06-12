---
title: "Thinkpad 570e--PCMCIA card problem"
date: 2006-07-20
forum: Hardware &amp; Laptops
---

### Post by Brunellus on 2006-07-20
My IBM Thinkpad 570E’s dock arrived, allowing me to boot a live session of Xubuntu.

Weird things:

   1. Why does the Xubuntu LIVE cd correctly detect my wlan adaptors...but then refuse to pull an IP via DHCP?
   2. Why does the installed version of Xubuntu (yes, I used the graphical installer) spit out a “could not write to card memory” error for the same adaptors--when it’s running off the exact same kernel?! Why are they detected on a live cd session and not on a full installation? 

When cards are inserted, they light up, they have power.  In the Live cd session, I can bring them up and down with ifup and ifdown, and they show up with an ifconfig -a.

Unfortunately, in the installed session, they light up, but are otherwise not there.

Anybody have any insights?

---

