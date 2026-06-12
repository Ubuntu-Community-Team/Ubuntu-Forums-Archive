---
title: "Thinkpad T21, Which wireless card?"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by uksigma on 2006-03-02
Have a thinkpad T21 laptop, just installed Ubuntu Breezy Badger.

Have a Mac Mini on OSX with an airport express network set up

1) 
a)Is it possible to connect laptop to mac network
b) OR possible to connect laptop to internet via airport (sharing with mac mini)

2) Which wireless card do I need to buy?

Really appreciate your help with this - Yes am a (brand)newbie

---

### Post by ssalman on 2006-03-02
for Q2, I have a x20 thinkpad and I was able to use:
- Cisco aironet 350 PCMICA (802.11b) card with unsecured networds.
- Netgear WG511T PCMCIA (802.11g) card with both unsecured and secured networks.

I hope this will help.

---

### Post by mjgumbley on 2006-03-28
Hi, I have a Belkin Wireless G Notebook Network Card, model number F5D7010, and it's working with a T21 - with a little manual help to activate it upon insertion - on a WPA network, using ndiswrapper (rt2500 driver, if I recall) and wpasupplicant.

---

### Post by Titus A Duxass on 2006-03-29
I have a linksys WPC11 v4 which uses the RTL8180 chipset.  
It needs ndiswrapper to function, but is really stable.

---

### Post by mips on 2006-03-29
Card with a Ralink chipset. Cisco is one of them if I'm not mistaken, can be had for cheap from E-Bay and they are very good cards.

---

### Post by jml on 2006-03-29
I agree with ssalmin  Both the Cisco Aironet 350 and the NetGear 511T work well with Ubuntu,(I've used them both).  Of the two, I prefer the NetGear card because of support for both WEP and WPA encryption in the card's firmware.  Both cards work with the native Linux drivers Ubuntu installs, so setup is pretty straightforward.  Go into Network Manager, select the wireless card, configure the card and then activate the card.  One tip.  Set up an unencrypted connection first.  Once you know that that much works, then you can play with encryption.

Joe

---

### Post by JEBB on 2006-03-30
Zonet ZEW 1501 worked right out of the box for me.  It connects to the Internet via my Airport Extreme Base Station.  I am using WEP security.  What I haven't been able to do is print to the USB printer attached to the AEBS.

---

