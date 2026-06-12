---
title: "Ndiswrapper problem"
date: 2006-03-21
forum: Hardware &amp; Laptops
---

### Post by robtotheb on 2006-03-21
I have followed the wiki to get my belkin wireless notebook card running on breezy and I got stuck.
I found the chipset and installed the driver and when i  ndiswrapper -l i get
bcmwl5a driver present, hardware present

BUT there is no wlan0 in network set up.  Also the 2 lights on the card are off.

---

### Post by Titus A Duxass on 2006-03-21
Do a bit more searching and have a look at the wiki.

There are a few more steps to do:

sudo modprobe ndiswrapper
add ndiswrapper to /etc/modules
edit /etc/network/interfaces and add details of the wlan card (essid, dns-server, etc).
Then go into systems service and edit the networking entries.

As I said there are few more steps to do, but if you search these forums you will find all you need.

---

