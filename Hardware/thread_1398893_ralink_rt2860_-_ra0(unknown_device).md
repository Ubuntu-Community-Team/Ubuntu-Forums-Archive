---
title: "ralink rt2860 - ra0(unknown device)"
date: 2010-02-05
forum: Hardware
---

### Post by debili on 2010-02-05
is the rt2860 module fully working under ubuntu? 
I can't get ICS to work/not able to create a network, also , under firestarter my wifi card is showing as 'ra0 (unknown device).
I've got a Sitecom wl181 N-wireless card

anyone can confirm same issue?
thanks!

---

### Post by IcarusR on 2010-02-05
To get rt2860 working try installing drivers from here..

[http://www.ralinktech.com/support.php?s=2]("http://www.ralinktech.com/support.php?s=2")

This page explains how to setup ICS...

[https://help.ubuntu.com/community/Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

All this was found with the help of google & quite a bit of reading !!

---

### Post by debili on 2010-02-05
hi icarusR,
Thanks for your reaction!
I'm googling for a month now, with no success :/ 

the InternetConnectionSharing link you've provided describes Ethernet sharing only, I went thru that process a couple of times already; at the bottom of that page is a link to [WifiDocs/ShareEthernetConnectionThroughWireless]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") which I've tried as well, thare it say's you need Firesterter; as I indicated in my first post I get an ra0 (unknow device) listing + device ra0 not ready error message when trying to setup Firestarter.

well, and I've tried to compile the driver from the Ralinktech website as well; on some forums I've found that the driver won't compile on the >=2.6.30 kernel (karmic 9.10 uses 2.6.31), but I've got like equal results if trying it under 9.04/2.6.28 kernel. 
Anyways, the driver looks to me as included under ubuntu, as when checking the Connection Information while connected to a wireless network it says the rt2860 is in use...
i'm lost

---

### Post by IcarusR on 2010-02-05
May be simpler to get a router & setup a network that way.
How do you connect to internet ?? 

ie my setup is

laptop > router/modem > internet
PC > router/modem > internet

Am I correct in asuming that WiFi works OK ??

[https://help.ubuntu.com/community/In...nectionSharing]("https://help.ubuntu.com/community/In...nectionSharing")

Does apply to wifi & ethernet...

> or a Wireless card for the incoming internet and an Ethernet port for the connection to the other computer

Have you actually tried it ??

---

### Post by debili on 2010-02-05
thanks,

well I guess a router would be easier; I just don't have one..I've bought the pci card in order to get N-speed access to the machine without the need of an extra router. Prior to that I've only read how straight forward it is to set this up(ics) with ubuntu; and that this card is supported. 

Regarding your quoted text - I'm looking for the opposit solution > internet >modem>ethernetcable>mymachine>wireless sharing to other computers
(at the moment i'm sharing my ethernet(internet) connection wirelesly from an iMac, so wifi/connecting to a wifi network/ works fine on my ubuntu machine, there's only a problem with sharing it...
the ubuntu InternetConnectionSharing documentation ( [https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless) ) requests firestarter to be used, yes I've tried it, that's the point where I get the ra0(unknown device) error message....
 

The wired thing is, that when I got the card, I've plugged it into an older PentiumIII pc, created a network with WEP enabled as described in the UbuntuDocumentation - the created wifi network was wisible on other computers, I also was able to connect to it, it just never asked for a password/wep - but this happened only once; after that, the created network never showed up on other computers when scanning for wifi networks, and not even once since the card is plugged into my current ubuntu machine. 

would you have any other suggestions please?

---

### Post by IcarusR on 2010-02-07
Sorry no ideas, short of trying it out myself, but don't have time at present.

---

