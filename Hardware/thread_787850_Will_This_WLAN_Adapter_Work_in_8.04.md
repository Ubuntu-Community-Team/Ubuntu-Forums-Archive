---
title: "Will This WLAN Adapter Work in 8.04?"
date: 2008-05-09
forum: Hardware
---

### Post by CarlosinFL on 2008-05-09
I am ordering a new laptop from work and all of us in the office use 8.04 Ubuntu however I would like to know if the wireless adapter I am ordering with my system is natively supported or recommended by the Ubuntu community.

The WLAN adapter is an Intel 4965AGN (802.11 a/g/n) PCI-E card.

[COLOR="Blue"][Intel Product Page](http://www.intel.com/network/connectivity/products/wireless/wireless_n/overview.htm)[/COLOR]

---

### Post by industrytool on 2008-05-18
I just got a hp dv6000 laptop with the same wifi card. Found lots of resources on how to install the drivers for it however i'm still having trubble doing so. You'll need to install the 80211 modules then the 4965AGN drivers, but'ca need the kernel souces for it. Still can't figure out how to add the sources to the auto update thingy, havin problems doing it manually 8(

---

### Post by ASULutzy on 2008-05-18
My hpdv6000 was pretty easy to get to work... I just got the broadcom 43xx drivers, installed ndiswrapper and ndisgtk and it worked.

---

