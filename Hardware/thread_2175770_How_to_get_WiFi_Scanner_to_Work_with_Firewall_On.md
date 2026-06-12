---
title: "How to get WiFi Scanner to Work with Firewall On"
date: 2013-09-20
forum: Hardware
---

### Post by RavenLX on 2013-09-20
I use Linux Mint (which is built upon Ubuntu). They had the firewall turned off by default. I wanted to turn it on but when I did, the scanner part of my All-In-One Printer/Scanner would not work. XSane would say it can't find it. Yet the printer was detected in programs just fine and printed. I knew it had to be due to the firewall so for the longest time I kept the firewall off even though I would feel better with it turned on. 

Tonight I did some playing around with it and I came across the solution. And it's so simple I could have bopped myself over the head! :D

One just needs to make a rule to allow the scanner to come in through the port it's using. Thing is, while the port the scanner uses is the same, each time you use XSane or anything that accesses it to scan an image (say GIMP for example), the port on the *computer* end of it changes! Well, then you just got to use *any port* for that part of it. Also you need the IP addresses for the computer and the printer/scanner.

I put together a tutorial to show how to do this a quick and easy way or manually:

<snip>

I hope this helps others get their WiFi scanning devices working with their computer.

---

