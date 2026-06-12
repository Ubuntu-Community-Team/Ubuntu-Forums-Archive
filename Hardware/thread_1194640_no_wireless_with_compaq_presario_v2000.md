---
title: "no wireless with compaq presario v2000"
date: 2009-06-22
forum: Hardware
---

### Post by skeetlez on 2009-06-22
i installed ubuntu and everything is well except my wireless isnt working. I have a compaq presario v2000 and im using ubuntu 9.04 jaunty

thanks in advance for the help:)

---

### Post by terdon on 2009-06-23
Hi, I'll need a bit more information. What happens if you simply click on the NetworkManager icon on the panel? Do you see wireless networks?

Also, please open a terminal, run the following commands and post the output here:

```
iwconfig
```
and
```
ifconfig
```

---

### Post by benditoelqueviene on 2009-10-15
You've to check your drivers.  There should be no restricted modules.  Your network should be Broadcom 4318.  Open Terminal and write:
```
lspci | grep Broadcom
```

The answer will be:

```
0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```****Or something like that.****If so,****install [I]Windows Wireless Network
drivers[/I] from your *Aplications *menu, with *Add and remove aplications*.
You'll found that aplication in *System tools*.  Then you go to your
*Hardware drivers* and activate B43.
It worked for me.  Now the V2000 detect the wireless networks and
conect to the internet. I found this solution in
[http://ubuntuforums.org/showthread.php?p=8106508#post8106508](http://ubuntuforums.org/showthread.php?p=8106508#post8106508)****Unfortunately in Spanish.

---

