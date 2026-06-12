---
title: "Wireless but no wired and no eth0 interface on eee pc 1000 with rt2860 adapter"
date: 2009-04-30
forum: Hardware
---

### Post by Dave_Connor on 2009-04-30
I am currently using a combo of Ubuntu's 2.6.24-23-generic and Adam's custom kernel off array.org. I now have wireless internet access thanks to Ubuntu Forums and RaLink being nice with there cards. But I have issues with using wired connections. With Adam's custom kernel eth0 interface shows up and I can used Wired connection for school but with the generic kernel it shows ra0 and lo interface but no eth0. Is there a need module I need to compile or some config file to edit for wired connections since I need wired for school with my programming class due to no wireless access points in the building.

---

### Post by Dave_Connor on 2009-05-03
Never Mind. Array.org posted what modules they added and only needed the atlie module and after compiling it is working great. Thanks for the community for great documentation on changes. :)

---

### Post by mikedep333 on 2009-05-03
Just FYI, I believe Ubuntu 9.04 completely supports the Eee PC 1000 series. It supports my 901. You will not need to install a custom kernel.

[http://www.ubuntu.com/news/ubuntu-9.04-unr](http://www.ubuntu.com/news/ubuntu-9.04-unr)

---

