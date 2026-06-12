---
title: "Dell Vostro 3560 - no wireless"
date: 2012-07-05
forum: Hardware
---

### Post by keidaritay on 2012-07-05
Hi everybody!
I'm trying to connect to a WiFi but Ubuntu 12.04 does not detect my (or any other) Wifi network.
It looks like a hardware problem. My laptop has the Broadcom Corporation Device [14e4:4365] (rev 01)  .
Important notice - the Ubuntu was installed alongside WIN7, with which the laptop was purchased. wifi works perfectly on the WIN7.
If anyone has any idea - i'll appreciate it...

---

### Post by ahallubuntu on 2012-07-05
Looks like your Broadcom wireless card is not supported in Ubuntu yet - not surprising as Broadcom wireless card support usually takes a while in Linux.  You might want to follow this thread from people with the same wireless card:

[http://ubuntuforums.org/showthread.php?t=2014096](http://ubuntuforums.org/showthread.php?t=2014096)

Personally, I would just replace the wireless card with an Intel wireless card.  It appears the Intel WiFi 2230 card will work in this laptop and might even add functionality.  You can buy this card on eBay for about $30USD shipped from California.

---

### Post by thotz on 2012-07-10
I have got exactly the same problem with my Dell Vostro 3560 :(

---

### Post by thotz on 2012-08-20
Have a look at this. I tried it on 12.04 LTS with my Dell Vostro and it worked.

[http://ubuntuforums.org/showpost.php?p=12181965&postcount=5](http://ubuntuforums.org/showpost.php?p=12181965&postcount=5)

---

### Post by emgiezet on 2012-10-07
Same issue worked for me
[http://askubuntu.com/a/127660/77143](http://askubuntu.com/a/127660/77143)

---

### Post by gadh on 2012-10-23
i tried all the possible solutions including ndiswrapper (using win7 driver) but none worked.

--> finally - I succeeded activating the wireless using Ubuntu 12.10  on Dell Vostro 3560 using only this solution !! 
follow the instructions  on this link:
[http://forums.fedoraforum.org/archive/index.php/t-283824.html](http://forums.fedoraforum.org/archive/index.php/t-283824.html) 
(update to the instructions: use apt-get instead of yum)

---

