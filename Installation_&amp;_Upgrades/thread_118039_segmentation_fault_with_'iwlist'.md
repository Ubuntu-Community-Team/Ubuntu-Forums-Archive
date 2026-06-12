---
title: "segmentation fault with 'iwlist'"
date: 2006-01-16
forum: Installation &amp; Upgrades
---

### Post by nemik on 2006-01-16
i'm going insane with this small pentium II laptop. 
so a little background info: 
wifi via its PCMCIA worked great after i did base install. i did ```
iwlist ath0 scanning
``` and found the MAC address, did ```
sudo iwconfig ath0 ap <MAC address> 
then sudo iwconfig ath0 key <correct key>
``` and i could ping google and all! so i apt-getted xubuntu desktop, it worked great, then got open-office using synaptic. everything perfect, love it.

THEN the problems began:
i tried to reboot, it looked like it ended everything normally, but got stuck at 'now rebooting...' so i turned it off. now all hell broke loose. no wifi, ok fine. so i did ```
iwlist ath0 scanning
``` well now when i do it, i get a "segmentation fault" and the system just crashes. sudo gets stuck, can't ctrl+c, nothing. only shut off and try again with more disappointment.

so why did iwlist generate that segmentation fault? getting stuck at reboot and me turning it off?

and how do i fix it? start ALL over? or would apt-get install ubuntu-base get the base stuff back on and i could try then?

any help would be greatly appreciated! thank you all!

---

### Post by nemik on 2006-01-16
how would i got about at least trying to reinstall the base system? would that work to do it off the CD?

---

