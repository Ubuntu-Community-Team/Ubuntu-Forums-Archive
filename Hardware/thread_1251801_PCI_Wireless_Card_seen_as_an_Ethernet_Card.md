---
title: "PCI Wireless Card seen as an Ethernet Card"
date: 2009-08-28
forum: Hardware
---

### Post by meastwood98 on 2009-08-28
Hi,
 
I’ve got an Ashton Digital Airdash PCI wireless card which im using in a Dell Inspiron 2600. I’ve used it with ubuntu 6.06, 8.10 and 9.04 and it works perfectly by just plugging it in (no need to install drivers or anything).
 
I’m using ubuntu 8.04 (for reasons I wont go into), and it does seem to work the same. The device manager recognizes it as an Ethernet card. It is definetly the wireless card it is referring to as an Ethernet card because when i remove it, it dissapears from the device manager and also the description in the device manager is one for a wireless card. How do I change it so it see's it as a wireless card? Any help much appreciated.
 
Thanks,
 
Mark

---

### Post by H.R.H on 2009-08-29
I need to find a wireless PCI card that works with v9.04, so if you could tell me the model of the card, I'd much appreciate it.

---

### Post by DJKnut on 2009-08-29
Still working on a solution... but I can list two to pass on.. First is a Sabrent PCI-G802, which like the one above... was miss-recognized as a NIC and showed up a 'Cable Disconnected'..!!  The second was a Netgear WG311 v.3 which worked (using ndiswrapper and an XP driver..) but wouldn't support WPA-personal security... I'm now waiting for a Netgear WPN311 which is stated (elsewhere in the forums..) to work out of the box without any extra drivers...  we'll see!!  Good luck, Dave

---

### Post by DJKnut on 2009-09-06
Got the Netgear WPN311NA PCI wireless card, and it worked with the native kernel support, no need for any additional drivers... and it supports WPA-Personal security as well.... Life is good... I might add that I reloaded a fresh install of Ubuntu 9.04 to remove any chance that something I'd done before would still be lurking in the shadows and cause trouble... I think it was worth the effort!!  Cheers, Dave

---

