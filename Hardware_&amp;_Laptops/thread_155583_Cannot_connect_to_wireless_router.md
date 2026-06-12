---
title: "Cannot connect to wireless router"
date: 2006-04-05
forum: Hardware &amp; Laptops
---

### Post by ?@yk0&amp;^4 on 2006-04-05
My card was not recognised using Breezy, so I tried Dapper Flight CD 6...

I have been following the Wireless Troubleshooting Guide on the wiki, and although the wrong driver seems to be loaded for my Edimax EW-7128g wireless card (RT61 instead of RT2500), much of it works. I am able to scan for networks using **sudo iwlist ra0 scan**, and my network comes up with the correct channel, but I cannot connect to the router.

I have tried installing the Gnome Network Manager and the WiFi Radar program, and neither have allowed me to connect. When I tried using the pci=noacpi or acpi=off commands, various parts of the operating system froze.

My network consists of a wired router (static ip: 10.0.0.2) with NAT and DHCP on (dishing out addresses from 10.0.0.4 to 10.0.0.15) connected to an Airport Express base station (static ip: 10.0.0.3) with NAT and DHCP turned off. This works fine with my Windows PC's and Powerbook. I have turned WEP off to make configuration easier...

What should I try next?

Many thanks,
Greg.

---

### Post by karthik085 on 2006-04-05
Ndiswrapper is one of the best option to load windows wireless driver and connect it to the router. I usually do and it works well. 
First, check if ndiswrapper supports your card. There are many discussions related to this, on the ubuntuforums. Search, it will help you.
One such post:
[http://ubuntuforums.org/showpost.php?p=891217&postcount=3](http://ubuntuforums.org/showpost.php?p=891217&postcount=3)

---

### Post by ?@yk0&amp;^4 on 2006-04-05
It would seem that my version of the Edimax EW-7128g card does in fact use an RT61 chipset, and not the RT2500 chipset that many of these cards seem to use. When I run **lspci -n** I get **1814:0301** for the card, which is reported as RT61 in the Ndiswrapper list, and this seems correct. So my only problem now is how to connect to my router.

I don't think Ndiswrapper is really needed is it, as the native driver has been loaded...?

Many thanks,
Greg.

---

### Post by ?@yk0&amp;^4 on 2006-04-05
Right, by following *judgekaster*'s excellent instructions at [http://ubuntuforums.org/showthread.php?t=132980&highlight=ralink](http://ubuntuforums.org/showthread.php?t=132980&highlight=ralink), I've been able to get the card running on Breezy. I will try to find the exact problem in Dapper and submit a bug report, and I will try to perfect the instructions into a suitable HOWTO for the forum or wiki.

Many thanks!

---

