---
title: "Need a wireless card for kismet"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by qb4ever on 2007-02-21
I need to find a wireless card that has native linux drivers for kismet/airsnort etc. 

So far at walmart I have found:


Belkin F5D8010 <-- appears to have native linux drivers [here ]("http://gpl.airgonetworks.com/")but costs almost $90 :(

and

Belkin F5D7011 <-- the other choice for $34 but unknown chipset or native linux support

---

### Post by Skidpad on 2007-02-21
A link from last week: [http://www.ubuntuforums.org/showthread.php?t=362713](http://www.ubuntuforums.org/showthread.php?t=362713) and here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported).

No need to spend $90, mine was $30.

---

### Post by qb4ever on 2007-02-22
I ended up getting the  Belkin F5D7011 that has the broadcom 4318 chipset. I followed the instructions in the wiki and got it to work other than the "invalid AP" bug. then I installed kismet but noticed no support for the broadcom.. instead I picked ipw2200 as the "source device" and it works :guitar: :popcorn:

---

### Post by towy71 on 2007-05-16
I have tthe same card and usng bcm38xx-fwcutter to extract and place the firmware from the wiindows install  cd, it works just fine on my ancent laptop running feisty

---

