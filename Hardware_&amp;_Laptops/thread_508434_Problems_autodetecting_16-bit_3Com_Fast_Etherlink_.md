---
title: "Problems autodetecting 16-bit 3Com Fast Etherlink PCMCIA card in Xubuntu 7.0.4"
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by gimle on 2007-07-24
I have tried several different install cd's on a Toshiba Satellite Pro 4200 laptop with a pcmcia 3com Fast Ethernet (16-bit) card. (I would like to run the latest Xubuntu, 7.0.4, which I currently have installed) All the install packages behave similarly. If one boots from the live cd, the network card is not detected. However, if one uses the alternate install cd, the network card gets  detected during the install phase that "starts pccard services". The install then correctly finds the device, and offers me to use it as device "eth0: Fast Ethernet". During the install it also successfully retrieves language files and checks for patches.

After reboot, the pcmcia card stays dead quiet. It doesn't get detected at boot. In fact, not even the cardbus controller shows up in lspci. dmesg displays nothing when grepped for "pcmcia", "eth0" or "3c574".

I found a closely related discussion at thread :

[http://ubuntuforums.org/showthread.php?p=3071073#post3071073](http://ubuntuforums.org/showthread.php?p=3071073#post3071073)

So after some digging, i found out from a slackware thread, that supposedly the correct kernel module for this card would be "3c574_cs" (the chipset is 3c574-tx, so I assumed it was correct). 

So I did do "depmod -a" and after "modprobe 3c574_cs"  without any errors. However, when trying to restart networking, eth0: is still not there. I added the "alias eth0 3c574_cs" to /etc/modules and booted, but nothing. 

Prior to calling modprobe, pcmcia bus does not exist in /sys/bus/
And post-call, /sys/bus/pcmcia/devices/ ,is empty

Currently booting added with boot options "noapic nolapic"

Might this be an issue with the cardbus controller? And why the heck does it work during install, but not after boot??

---

