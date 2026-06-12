---
title: "Ubuntu 11.04 wireless help!"
date: 2011-09-14
forum: Hardware
---

### Post by pitty04 on 2011-09-14
Hello everyone! i have a labtop. Toshiba Satellite L650-07U. I just currently installed 
Ubuntu 11.04 (32bit) along side my windows 7(64bit) and i can not connect to wireless 
internet with Ubuntu.... im wondering if it is because my windows 7 is 64 bit witch has 
the wireless drivers and such and Ubuntu is 32bit. but i would life to know if this might 

solve the issue before i try it :$
Thanks in advance!

Computer specs..
- Toshiba Satellite L650-07U
- Intel core 13 M730 @ 2.40GHz
- 4gb ram(3.80 useable)??
- 64 bit on windows(32bit ubuntu?)
- Itel HD Graphics Driver
- Realtek WLAN driver
- Atheros LAN driver

NOTE!!: i just downloaded these driver as i re installed windows 7.. im pretty sure there 
the right ones as both WLAN & LAN work on windows 7!!!:p
please help i love ubuntu! :):popcorn:
):P

---

### Post by mue.de on 2011-09-14
Hello, 

on my Toshiba Satellite L350-16 the KNetworkManager works fine under Lucid Lynx, of course also WLAN.
But i don't realize your situation: do you have a dual-boot-system or are you using ubuntu inside of windows 7 ?
You don't need any specific driver, if your wlan-chipset is the same as mine 
try in a terminal:
> sudo lshw 

I get the following chipset 
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation

Meanwhile for me ubuntu is sometimes a hate / love relation ;-)

---

### Post by pitty04 on 2011-09-14
i get this
Product: RTL8188CE 802.11b/g/n wifi adapter
vender: Realtek

but i just downloaded a linux realteak WLAN driver and now it work! i have wireless :) but yes my linux is installed along side windows 7... is that bad? and its 32 bit bit windows 7 is 64 bit..

but when i install CCS and use wobblely windows its kinda laggy?... but i have good prosscer so i dont think it should be laggy... do i need drivers or hardware update for my intel HD graphcs?

---

### Post by mue.de on 2011-09-14
Sorry, 
i can't answer that; my hardware is older ;-(

---

### Post by pitty04 on 2011-09-14
its okay, thanks tho! :)

---

