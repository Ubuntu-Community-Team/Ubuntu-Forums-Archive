---
title: "wireless problem"
date: 2005-10-07
forum: Hardware &amp; Laptops
---

### Post by lost.sync on 2005-10-07
i've followed the how-to in the forums and everything seems to work to a certain extent.  in the networking utility i can see the SSID of my network and it says it's connected to it, though i don't see an IP anywhere (using DHCP).  when i set it as the active interface, it just doesn't work.  the card is working somewhat, it's just like ubuntu can't push traffic through it or something.  when i configure manually with an ip, it doesn't change anything.  

it's a broadcom chipset using ndiswrapper on an emachines m5312 notebook.  same results in hoary and breezy.

i'm completely clueless.  any ideas?

---

### Post by xristos on 2005-10-07
Try this ```
iwlist wlan0 scan
``` assuming your wireless interface is wlan0 . It should give you any AP  broadcasting in the area .

---

### Post by kuriharu on 2005-10-12
I've had a similar problem and I'm still looking for a resolution. At least in Ubuntu my wireless card got detected. I went through hell trying to get my laptop to see it using Fedora Core!

---

