---
title: "feisty wireless ????"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by arijel on 2007-05-02
Im using ubuntu Feisty with my HP nx6325 which has Dell 1390 wlan card (broadcom 4311 chipset). I have extracted firmware via bcm43xx-fwcutter and everything went ok. The card is working, led is flashing blue when turned on, I can scan all the networks in range... The problem is that I can't connect to any of the networks via network manager, wifi-radar or wpa_supplicant. I found one unprotected network which I can connect to from win xp, but can't from feisty. When using wpa_supplicant I always receive message that it is trying to associate with AP and then request timed out.
Can someone instruct me how to use my wifi card, Im sure that Im doing something wrong but I can't figure what?

---

### Post by teh.element on 2007-05-02
If you can, try installing the driver through Feisty's Restricted Driver Manager or through Automatix2, assuming you can get a LAN connection.

---

### Post by manishk on 2007-05-23
I have the same laptop and I followed the instructions here [http://www.ubuntuforums.org/showthread.php?t=322761](http://www.ubuntuforums.org/showthread.php?t=322761) and my WiFi is working perfectly fine.

Good Luck.

---

### Post by frozinfire on 2007-05-29
I have a similar wireless card, so hopefully this could work for you. Please bear in mind that my wired connection shows up as eth0, my wireless is wlan0, and my unprotected network is "linksys," so the labels should be changed as appropriate.

Open a terminal
$ sudo ifdown eth0
$ sudo ifdown wlan0
$ sudo ifup wlan0
$ sudo iwconfig wlan0 essid linksys
$ sudo dhclient wlan0

---

