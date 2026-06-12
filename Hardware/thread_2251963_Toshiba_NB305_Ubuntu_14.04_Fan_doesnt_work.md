---
title: "Toshiba NB305 Ubuntu 14.04 Fan doesnt work"
date: 2014-11-08
forum: Hardware
---

### Post by Kenneth_Grimm on 2014-11-08
Ive installed Ubuntu 14.04 on my Toshiba NB305 Notebook. seems to get hot at the bottom.. and the fan doesn't seem to work. it works good on windows 7 but not Ubuntu 14.04. 

I don't think the fan is installed, is there a way to go about installing it?

---

### Post by Kenneth_Grimm on 2015-01-31
i have a toshiba NB-305 N410BN with Ubunutu 14.04 updates on Feb 1 2015.. I had the same problem... 
I did... sudo apt-get install lm-sensors xsensors fancontrol 
Then... sudo sensors-detect 
Said yes to all and my fan works now... didnt test fan control...

---

