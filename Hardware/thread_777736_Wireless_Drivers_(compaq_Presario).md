---
title: "Wireless Drivers (compaq Presario)"
date: 2008-05-01
forum: Hardware
---

### Post by pilgprog on 2008-05-01
I have a compaq presario f750us with built in Broadcom wireless.  I have had success using ndiswrapper on other systems in the past but I can't seem to find the XP driver (with .INF and .SYS) files so I can try using ndiswrapper to get this system working.

anybody know where I can get the XP drivers for the Broadcom wireless device?

Thanks much :-)

BTW, got the NVidia drivers working and it's really great  :-)

---

### Post by teaker1s on 2008-05-02
first 
```
lspci
``` then you wil need to use cabextract or unzip

plus look here
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=(fluff)|(no)#head-c8cbba1734885284e4f79c2054461c863169f1bf]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=(fluff)|(no)#head-c8cbba1734885284e4f79c2054461c863169f1bf")

---

