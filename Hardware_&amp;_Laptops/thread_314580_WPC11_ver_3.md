---
title: "WPC11 ver 3"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by hebetude on 2006-12-07
I'm running an old Presario laptop.  From the original install, my wireless card worked perfectly.  It also worked on the LiveCD.  However, one day I went into the networking settings and noticed the card was not enabled.  After clicking the button my card has never worked since.

I've got a wireless connection tool installed (NetworkManager Applet 0.6.3) that used to find local networks, now it doesn't even say that I have a wireless card.  

Here is a printout of lshw:

  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:06:25:ab:dd:20
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

So... no driver is installed, I'm assuming.  I've tried going the ndiswrapper route with no success, it seems the linux kernel has native support for this card.  Here is my chipset information:

802.11b WPC11 v.3 PCMCIA 	 
chipset:Prism 1 	 
driver:orinoco

---

### Post by hebetude on 2006-12-07
sudo lshw -businfo:

Bus info     Device     Class          Description
==================================================
             eth1       network        Wireless interface

---

