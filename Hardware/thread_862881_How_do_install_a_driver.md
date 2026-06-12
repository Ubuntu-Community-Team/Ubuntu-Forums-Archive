---
title: "How do install a driver?"
date: 2008-07-17
forum: Hardware
---

### Post by Moonhead on 2008-07-17
I recently installed Ubuntu 8.04 on my HP 6710b laptop and everything seems to work fine except my wireless connection. Roaming mode does not detect any wireless networks. The laptop has a wireless kill switch that will that I cannot activate, and I suspect this is the problem. The wireless card is an Intel Pro/Wireless 3945 ABG, PCI ID 8086:4222. When I look in Device Manager the kill switch is listed under the main heading of the wireless card but it has a question mark for an icon. I found and downloaded a linux driver from the intel site but I have no idea how to make use of it. I extracted the file and read the included installation instructions which looked horribly complicated. I even attempted to enter some of the commands at a terminal (after entering sudo) but all I got was "no such job". I can't even figure out how to find out what my current driver is. All attempts to find a straightforward explanation of how to load a driver in Linux or Ubuntu on the web were utterly fruitless.

---

### Post by miguelbuenca on 2008-08-25
got a similar problem.anybody (experts) out there who can answer this please

---

### Post by Crafty Kisses on 2008-08-25
That's weird, sounds like a Ndiswrapper might do the job.

---

