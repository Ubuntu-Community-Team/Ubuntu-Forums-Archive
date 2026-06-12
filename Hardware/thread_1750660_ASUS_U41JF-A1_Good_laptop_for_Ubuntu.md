---
title: "ASUS U41JF-A1: Good laptop for Ubuntu?"
date: 2011-05-05
forum: Hardware
---

### Post by anthony62490 on 2011-05-05
I couldn't find this model in either of the Laptop Compatibility Lists. I imagine that the NVidia graphics card shouldn't cause much trouble, but I am unsure about the rest of the hardware.

Here are the specs:
```
•  14-inch 720p (1366x768) glossy panel with LED backlighting 
•  Intel Core i3-380M dual-core processor (2.53GHz, 3MB L3, 4.8GT/s QPI, 35W TDP) 
•  Intel HM55 chipset 
•  Switchable graphics via Nvidia Optimus technology: 
•  Nvidia GeForce GT 425M w/ 1GB DDR3 memory 
•  Integrated Intel HD graphics 
•  4GB DDR3-1066 dual-channel RAM (2x 2GB) 
•  500GB 5400RPM Western Digital hard drive (WD5000BEVT) 
•  Atheros AR9285 802.11n wireless LAN 
•  DVD burner (MATSHITA DVD-RAM UJ892AS) 
•  8-cell battery (14.4V, 5800mAh, 85Wh)
```

Is there a place where I can check to see the compatibility of these components? I don't necessarily need a definitive answer, just a good place to search for one.

---

### Post by beew on 2011-05-05
It has Optinus (see switchable graphic) It  doesn't work with Linux unless there is a BIOS switch to turn off Optimus, otherwise you wouldn't be able to the Nvidia graphic card** at all,--**never mind switching. You will be stuck with the low performance Intel card. Even though you can't use the Nvidia card it will still be sucking power and generating heat.

So forget about it, unless you know for sure it has the BIOS switch to turn off Optimus and use the discrete graphic card.

---

### Post by anthony62490 on 2011-05-08
> **beew said:**
> So forget about it, unless you know for sure it has the BIOS switch to turn off Optimus and use the discrete graphic card.

Of course, it occurs to me that I could just keep a Windows partition for gaming. Windows would still use the NVidia card for games. besides, the small "Intel GMA HD" card should still be better than my crappy little "GeForce4 MX 420"

---

### Post by beew on 2011-05-08
> **anthony62490 said:**
> Of course, it occurs to me that I could just keep a Windows partition for gaming. Windows would still use the NVidia card for games. besides, the small "Intel GMA HD" card should still be better than my crappy little "GeForce4 MX 420"

Well if you are primarily using Windows for performance that is another story, just saying I won't buy it because I don't dual boot. 

Now as for the Intel card you should also do more research, I am not sure but it seems that under Optimus even the Intel card doesn't have 3d effects.

---

