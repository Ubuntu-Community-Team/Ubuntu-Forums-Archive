---
title: "WiFi from Minimal Install?"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by peterscj on 2006-02-04
I am trying to install Ubuntu Lite on an old laptop and can't seem to get the wifi card to connect to my network.  I wanted to do a minimal install and then try to get it onto the network so that it could apt-get the rest of the updated files.  I run regular Ubuntu on my main laptop and on one of my desktops with no problems but for some reason this old laptop is giving me loads of troubles.  The laptop is a Micron GoBook2 266MHz PII w/ 96 MB RAM and the card I'm trying to use is a Netgear MA521.  I also tried hooking up my DSL modem directly into my laptop through the usb with no luck either.

I did a minimum install then did an apt-get install ndiswrapper-utils from the CD.  I then downloaded the drivers for both the DSL modem and the WiFi card.  I installed the driver using:
sudo ndiswrapper -i NET8180.INF  When I check it shows the driver present and hardware present.

To my /etc/network/interfaces file I added:
iface wlan0 inet dhcp
wireless-mode managed
wireless-essid MyLAN

I disabled all security on the WiFi router so that I could narrow my problem area.  Does anyone have any further sugestions on how to get this working?  I've been working on it for hours and have had absolutely no luck as of yet.

Oh, I read [http://www.ubuntuforums.org/showthread.php?t=92119&highlight=Netgear+MA521](http://www.ubuntuforums.org/showthread.php?t=92119&highlight=Netgear+MA521) but it does not seem to fix whatever problem I'm having.  Any help would be greatly appreciated.

Cam

---

