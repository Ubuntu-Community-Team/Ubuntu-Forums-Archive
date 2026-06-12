---
title: "Clean Upgrade 8.10 -&gt; 9.04 -- What to check there-after"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by bxcrx on 2009-04-30
I did a clean upgrade from 8.10 -> 9.04 which involved me formatting the drive with EXT3, installing 8.10, and then went straight to synaptic after it finished installing 8.10 and hit "Upgrade to 9.04".

Everything works as far as drivers and devices are concerned along with synaptic. 


I'm using EXT3 for my file system.

Is there anything else that I should check in regards to the integrity of the system?


Thanks

---

### Post by zvacet on 2009-04-30
If you don´t see anything unusual then your system is O.K.If anything start to make trouble feel free to ask here.It is little bit strange that you upgrade from 8.10>9.04 without updating Intrepid first,but if it works then O.K.

---

### Post by bxcrx on 2009-04-30
It's funny that you should say that because:

My first attempt to upgrade, with video drivers activated during the process from a fully patched 8.10 failed.

My system specs are:

AMD Athlon XP 1.5
2 GB DDR RAM
Nvidia 9600 GT AGP Card running 180.29 <- installed from a PPA deb 

What really failed the first upgrade was that xorg-server, and nvidia drivers failed to upgrade properly in the end.

---

### Post by zvacet on 2009-05-01
Usual way to upgrade is to have updated existing version of Ubuntu,then in system>admin>software sources uncheck all third party sources and after all that you can upgrade.I understand that is not a way you did it and it fails first time.Does it work now and if not what are the problems?

---

### Post by bxcrx on 2009-05-01
So far everything seems to be working out. :)

---

