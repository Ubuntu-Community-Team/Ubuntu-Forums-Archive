---
title: "remember the load/unload cycle bug? well, here's an interesting twist..."
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by LMF5000 on 2008-02-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm sure that by now people are familiar with the ubuntu (and I think every other distro) bug that makes the hard disk load/unload the heads very frequently. It's described here: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

Anyways, 15 days ago I bought a Samsung HM121HC (it's a 2.5 inch 120GB HDD). It is in an external USB2.0 enclosure, and I've got ubuntu installed and running off it. My only computer (on which I run ubuntu from the external drive) is a laptop. 

When I place the drive (which, btw is very quiet) near my ear, I hear a metallic clink every five seconds, which suggests that the drive is unloading every 5 seconds. It also makes a scary loud pop unpredictably, about once a day (or less). My calculations reveal that at this load/unload rate, if I use it 8 hrs a day it will fail in 175 days.

Now, the problem is this: being a USB drive, hdparm -B 254 or 255 both do not work (to be specific, it tells me that the command executed successfully, but the clanging continues). Smartctl doesn't work either, so I'm in the dark as far as accumulated load/unload cycles are so far. The drive uses a 2.5 inch IDE connector, but my laptop internally uses an SATA connector.

Does anyone have any suggestions for stopping these constant load-unload cycles? I think the only way to get this done in such a situation is to create a program that accesses the disk every 2 seconds or so...

---

### Post by dmcn on 2008-05-21
I have the exact same problem with the same disk. I have it connected via a converter to my onboard IDE port as the disk is the system drive in my small file server. 

Have you come up with a solution? My disk unloads about 160 times pr. hour and since my file server is on 24/7 I see where this is going. ;)

---

### Post by LMF5000 on 2008-05-21
Sorry to disappoint you, but in a couple of days I finally got annoyed by the fact that my Canon Pixma iP1800 will not duplex under linux (I have to specify odd pages one by one, and then even pages one by one), and the fact that fonts and appearance are just too ugly under linux (compare openoffice under windows and under linux and you'll see what I mean - in windows, the colours are just brighter and the text more crisp), and ended up removing Ubuntu completely and going back to Windows XP.

Other limitations I encountered were: No support for my Panasonic RR-US450 voice recorder, no equivalent program to "DVD Decrypter" (unless you count AcidRip - but that has its limitations) and no support for my old scanner... In the end I decided it was easier for me to just go back to Windows, seeing that there's nothing in my case that linux can do better (except boot from an external drive)

---

