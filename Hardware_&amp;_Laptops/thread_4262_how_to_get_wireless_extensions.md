---
title: "how to get wireless extensions"
date: 2004-11-13
forum: Hardware &amp; Laptops
---

### Post by Razvan on 2004-11-13
Hi all,

im trying to get my atheros-based wlan card running...

madwifi is installed and loaded

bad thing is that pcmcia-cs couldnt find my card, so i added some stanzas to /etc/pcmcia/config

the thing is, that still nobody seems to seee my card...can I edit /etc/network/interfaces manually? what do i have to add?

oh...and sudo cardctl ident gives "no information avialable" so is the problem maybe the pcmcia-driver? 

any ideas? thanks

---

### Post by randy on 2004-11-14
After you load the module ath_pci you should have a network device ath0.  This is your network device.  You can then use gnome-system-tools to setup the network connection.

---

### Post by Razvan on 2004-11-19
thats what i thought...but i dont get a device...

does anybody know, if the Texas Instruments - PCMCIA-chip is supported? i believe its the pcmcia bridge and not the wlan card....

---

