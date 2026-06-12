---
title: "Wireless DHCP Fails"
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by Permafrost91 on 2006-04-07
Wifi-radar still hangs sometimes and takes a long time when getting an IP address via DHCP but it seems to be able to connect to wireless networks at least.

[COLOR="Silver"]I have a Linksys WPC11 v4 using the ndiswrapper driver on an IBM X30 Thinkpad. I have had several installs of breezy on this laptop and I have always did the same thing to get my wireless up and running:

(1) install breezy from the CD
(2) install ndiswrapper
(3) install wifi-radar
(4) boom! wifi-radar detects networks and automatically connects to my default ones

Just yesterday I installed breezy again (I went to kubuntu for a while and wanted to come back to Gnome and everything was messed up, but that's besides the point) and did the exact same steps outlined above which I have always done (through several installs of Breezy) and now I get wifi-radar detecting the networks in range, but not being able to receive IP addresses via DHCP. These are all open, public, non-encrypted connections. I can go into a terminal and do

$ sudo dhclient wlan0

and get an IP address without a glitch. Wifi-radar, for some reason unbenknownst to me, however, cannot do this even though it has always done it. So I thought "well maybe something happened in the breezy packages that I don't know about" and upgraded to Dapper (which rocks by the way!) and am still having the same issues.

I browsed through several forum entries here and tried

$ sudo rm /var/run/dh*

as someone suggested. Even tried gtkwifi, netapplet, and several others. They all seem to have the same problem (but I don't know these apps and I find them hard to use since I am used to wifi-radar).

Why can't wifi-radar all of a sudden get a DHCP request out?

Let me know what output you'd like to see, I'll be happy to post anything useful since this is driving me nuts. I hate having to manually search for networks everytime I go to school or a friend's house.[/COLOR]

---

