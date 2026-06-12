---
title: "Problem: ubuntu does not detect my wifi"
date: 2011-04-12
forum: Hardware
---

### Post by necrocode on 2011-04-12
Hello everybody. This is my first post. I am new in the ubuntu world. Yesterday i installed ubuntu 10.10 in my new netbok (toshiba NB505). The problem is that ubuntu does not detect no wifi networks and i dont know what i have to do. It seems that the operating system has not installed any driver for the wifi. Due to im new in the free software world i dont have to much experience. I hope that anybody can help because 
I feel frustrated by not being able to surf the net with my new Ubuntu. 
If anything can serve here as I leave the output for some commands:

ifconfig

Eth0        Link encap: ethernet direccion hw 1c:75:08:82:057b
                .......
                .........

lo.            Link encap: Bucle local
                Direc. Inet 127.0.0.1 masc 255.0.0.0
                ......
                .......



Iwconfig

lo              No wirless extensions

Eth0.        No wirless extensions


In the case that i  do not have installed the drivers of the card wifi, how I can know wihich Wifi hardware i have and where I can download the appropriate drivers?

Thanks a lot for take the time to read this post. I hope that anybody can help me

---

### Post by ajgreeny on 2011-04-12
To find out what network card(s) you have run ```
lspci
``` in terminal.  It may also be worth updating with the machine cable connected, then looking in **System ->Administration ->Additional Drivers** for any drivers that may be available for the wireless card.

---

