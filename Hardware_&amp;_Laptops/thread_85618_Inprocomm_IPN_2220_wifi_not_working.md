---
title: "Inprocomm IPN 2220 wifi not working"
date: 2005-11-03
forum: Hardware &amp; Laptops
---

### Post by fossean on 2005-11-03
I have installed Breezy on my laptop (Acer Aspire 1362WLMi), and am very pleased with the result. Successfully connected to router over wire, but cannot get the wi-fi to work (Inprocomm IPN 2220). It is mentioned in device manager, but that's all. 

I'm totally unfamiliar with Linux, but believe I successfully installed the correct windows driver from Acer; got the ndiswrapper working and did ndiswrapper -i at the extracted files. I activated the network-manager applet, and there is no network connection. On attempting to configure settings, I just have options on LO and eth0.
I think there should be wlan0 in addition.

Very new to all this, so I've quite likely missed something obvious. Working on it until three in the morning didn't help.

---

### Post by fossean on 2005-11-03
Well, I just got it working; posting this over the wi-fi. :)  Eventually sorted it out by following the instructions here [http://users.skynet.be/ostaquet/aceraspire1360/](http://users.skynet.be/ostaquet/aceraspire1360/)

Had to read up a bit on simple linux commands, and it took me twenty minutes just to figure out how to move the driver files to /opt - you'll gather it's been very steep learning curve. 

Think there might be a couple of typos on the page linked above, but it's all a bit of a guessing game atm.

---

