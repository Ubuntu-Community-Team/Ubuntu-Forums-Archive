---
title: "Wireless Network, N00b needs help."
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by Thaxium on 2006-04-06
Ok, I've scoured many a forum to get this wireless card working. Heres what I have so far:


The Networking tool says that wlan0 is active and enabled.

0000:00:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) <--- Thats the device from lspci

wlan0     No scan results <--- Thats from iwlist wlan0 scan


wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: [COLOR="Red"]00:00:00:00:00:00[/COLOR]
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

                     ^----from  iwconfig wlan0

I do believe that the Access Point is what's causing my problems....

I used ndiswrapper to install the driver,  bcmwl5.sys .ini and bcm43xx.cat

The card is a linksys WMP54G ver. 3 (Almost positive its v3)

Any information would be greatly appreciated. Ubuntu beats the crap out of my old windows XP install, and I really dont want to go back... I also have a Linksys WUSB54GP that I can use, but I figured that since it is USB, It would be easier to configure the card.

---

### Post by karthik085 on 2006-04-06
Do you know any AP you can connect to? Sometimes you have to mention essid before scanning.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Configure_interface:](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Configure_interface:)

You may want to check FAQ:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ](http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ)

---

### Post by Thaxium on 2006-04-06
If this makes any difference, I'm going to eventually connect to this computer via another computer. The  network that i had set up was Ad-Hoc, and right now that computer is not on. Could that be why i dont have an access point?

---

### Post by karthik085 on 2006-04-06
Maybe. Why don't you test first, if your ubuntu system can connect directly to the router using wireless? Then, configure your other computers, ubuntu system, routers, etc and test.

---

