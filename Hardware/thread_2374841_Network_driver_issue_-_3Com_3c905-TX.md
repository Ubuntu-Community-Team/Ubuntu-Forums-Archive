---
title: "Network driver issue - 3Com 3c905-TX"
date: 2017-10-19
forum: Hardware
---

### Post by Frncio on 2017-10-19
Hello guys, can't figure out a way to make the (old) 3Com 3c905-TX network card to work. This computer was working just fine with its onboard netword card until last week when it got fried by a thunderstorm. This is the only network card I have available at the moment. I am using the linux mint distro but I think driver related issues should be agnostic to distros within debian/ubuntu derived distributions. Hopefully you might be able to help me out. 


Manually typed output from "inxi -Fxz":
```

System: Host: mic-francio Kernel 4.10.0-28 generic x86_64 (64bit gcc: 5.4.0)
             Desktop: KDE Plasma 5.8.7 (Qt 5.6.1) Distro: Linux Mint 18.2 Sonya    
Network: Card: 3Com 3c905 100BaseTX [Boomerang] driver: 3c59x port: ec00 bus-ID: 07:01.0
               IF: enp7s1 state: up speed: 100Mbps duplex: full mac: <filter>
```


It looks fine but it does not connects to the internet. After trying to connect for a while it gives two popup notification:


```
popup1: Wired Connection 1 - Connection deactivated
popup2: Wired Interface (enp7s1) - IP configuration was unavailable
```


I have looked around the internet but couldn't come up with any troubleshooting idea. The driver looks fine but there is no connection. The driver manager from linux mint thinks for a long time until it finally says that it cannot do anything without an internet connection or an installation disk (usb).


Any ideas how to solve this issue?

---

### Post by Frncio on 2017-10-20
[Solved the issue. The problem was not with the driver but with the ip configuration at my university network. This card works just fine on my linux system. I thought there was a driver problem because I could not get this card to work on windows 7 64bit due to driver issues. Sorry for the confusion.

---

