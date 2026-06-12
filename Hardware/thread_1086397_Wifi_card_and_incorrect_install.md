---
title: "Wifi card and incorrect install"
date: 2009-03-04
forum: Hardware
---

### Post by supertails on 2009-03-04
[http://s83.photobucket.com/albums/j300/superutails/?action=view&current=Problem.jpg](http://s83.photobucket.com/albums/j300/superutails/?action=view&current=Problem.jpg) How do I fix my wifi card cause it goes on and off at times and how do I fix the problem in the picture?

---

### Post by Fir3chi3f on 2009-03-04
photobucket is down for maintenance 

are you using ndiswrapper?

---

### Post by supertails on 2009-03-04
No but I looked it up but is it really that easy? [http://upload.wikimedia.org/wikipedia/commons/5/51/Ndiswrapper.png](http://upload.wikimedia.org/wikipedia/commons/5/51/Ndiswrapper.png) It doesn't even ask for a password and it asks when ever you install a simple update.

---

### Post by moonport on 2009-03-04
About the wifi problem, you first hate to find what kind of card your laptop has.
In the command line type: lspci | grep Wireless
(In my case: Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01))
Ubuntu has problems with some wifi drivers and you have to replace them.

---

### Post by supertails on 2009-03-05
Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

---

### Post by moonport on 2009-03-05
This could help you:
[http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)

It's a step by step tutorial to install your driver.

---

### Post by supertails on 2009-03-05
Got to go into root first. How you go into root?

---

