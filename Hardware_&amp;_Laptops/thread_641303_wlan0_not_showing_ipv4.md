---
title: "wlan0 not showing ipv4"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by inphektion on 2007-12-15
I got my wlan0 to show up by using ndiswrapper but at first I only saw ipv6 for it in ifconfig and in the gui in network tools.  I've blacklisted ipv6 as I don't want it for anything and now no protocols show up.  How do I get ipv4 to be in wlan0?  It's in my eth0 just fine....

---

### Post by inphektion on 2007-12-15
the ndiswrapper module is loaded.  I see wlan0 in iwconfig, etc.  There are a few .conf files in /etc/ndiswrapper/inet2220/
I don't see a RadioState entry anywhere.  should I add that?

---

