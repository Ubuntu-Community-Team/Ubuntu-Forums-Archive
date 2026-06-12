---
title: "Wireless won't connect on boot"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by Jonne on 2006-04-13
Hi,
I'm running Dapper Drake Flight 5, but I had the same problem in Breezy too:
When I start my computer, the built-in wireless card won't get an ip from my access point. I need to manually run a script as sudo with this (this was suggested to me on IRC):
```
#! /bin/sh
ifdown eth1 ; ifup eth1
```
After I run this, my wireless is connected fine.

Is there a way I can either:
-fix the problem in the first place (maybe it's a timeout that's too short in the init script?)
-run this script as sudo at startup automatically (putting it in init.d didn't work)

I don't really know what wireless card it is, as i get conflicting reports if I try to check it with the commands from the wiki. On windows, the drivers I needed to install were broadcom, though.

---

### Post by joplass on 2006-04-14
I will think that you tried "modprobe ndiswrapper" at the command line.

---

