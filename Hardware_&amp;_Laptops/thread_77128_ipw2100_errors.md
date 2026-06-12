---
title: "ipw2100 errors"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by alweston on 2005-10-16
After upgrading to Breezy, my wireless card is giving me problems. It starts just fine but downs itself after a few minutes with the following error in the logs:

ipw2100: : Fatal interrupt. Scheduling firmware restart. 

I can restart the card, but it will go down on its own after a few minutes. 
This card worked perfectly prior to the upgrade. Anyone know of a fix or workaround for this one?

---

### Post by chunk on 2005-10-16
I have the same wireless card on my laptop and I'm not having any problems.

Whatever that's worth.

---

### Post by nbc on 2005-10-29
Hum, weird, I've got the same problem : sometime it works, sometime I've got those 
[4297105.255000] ipw2100: : Fatal interrupt. Scheduling firmware restart.
message
Can't figure why for the moment

---

### Post by dangerjunkie2002 on 2005-10-30
Hi,

Have you tried going to the Intel website and seeing if there is a newer version of the firmware available for the  card? Failing that I'd try reseating it to check it's not a loose connection causing a spurrious interrupt.

Cheers,
Paul.

---

### Post by bb002 on 2005-10-31
Well there is a howto on how to manually update the ipw drivers. The howto was designed to get WPA support in Hoary but it involved updating the firmware version. 

it is located here [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

the ipw2100 and ipw2200 drivers are one and the same because while following the howto I had to manually delete those two module directories before i could compile the drivers.

I don't know what version of the ipw drivers breezy contains but I would download the newest versions of the three components you have to install from the howto. No idea how much the newer versions will affect the reliability of the howto so be prepared to hose your system.

you can get the latest versions of the components here.

firmware  [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)
ieee80211  [http://prdownloads.sourceforge.net/ieee80211/](http://prdownloads.sourceforge.net/ieee80211/)
ipw2200  [http://prdownloads.sourceforge.net/ipw2200/](http://prdownloads.sourceforge.net/ipw2200/)

---

