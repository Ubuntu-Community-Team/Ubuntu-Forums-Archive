---
title: "NC8000/Intel 2200BG cannot connect to unencrypted wireless"
date: 2008-08-18
forum: Hardware
---

### Post by monikersupreme on 2008-08-18
I just installed Hardy last week and have been trying to get the wireless to an acceptable state. I am able to connect to my WPA network at home however, while my wireless card can "see" unencrypted networks (at a cafe when I'm out & about) I cannot seem to connect.

There is no "unencrypted" setting for creating the proper network profile... I'm not sure if this is the whole issue but it seems like a place to start.

Surfing around I found some commentary about the Intel "iwlwifi" driver but according to the wiki page it does not specifically support my wireless card. There is also the ipw2200 driver:

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

but I'm not sure if this is already installed by default. 

Any advice would be much appreciated!

---

### Post by lisati on 2008-08-18
Does setting the Wireless network control panel (system->administration->network) to "roaming" mode help?

---

### Post by monikersupreme on 2008-08-23
Apologies for the delay on this response... 

Configuring network control panel to "roaming" does not help. Furthermore, as I am attempting to connect to the free wireless at a cafe I frequent, I need to be able to specify the (open) network to which I will connect as there are other networks within range of my laptop that I would prefer to avoid...

While I can "see" the cafe's wireless router in the wireless control panel if I attempt to connect to the unencrypted wireless I am prompted for either a WEP or WPA security configuration (there is no "Unencrypted" option)...

How do I configure a connection to a specific unencrypted wireless networks?

---

