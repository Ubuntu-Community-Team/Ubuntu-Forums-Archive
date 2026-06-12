---
title: "wireless card"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by nae5 on 2007-02-23
dell inspiron 600m Dell TrueMobile 1400 Dual Band WLAN Mini-PCI Card

card is not working atm.

i clean installed winxp and left 20gigs for ubuntu 6.06. i had been trying it on another computer as an experiment, and just repartitioned my main pc. i left 20 gigs open for ubuntu after xp.  

everything seems perfect except the wireless card doesn't work (in ubuntu), i have read on other posts that there are problems with this type, but that fixes exist. the only ones i was able to find are something called ndiswrapper which i read had to be compiled from source.  

i assume this is a driver or what linux calls drivers, anyway i have no experience compiling source code so i was hoping there was a way around that or a link w/ step by step to fix this problem(i cant use hardline have to copy files to cd in win then move to linux)(dont know bout swap drives (thought they were created in installation tho) or moving files from win partition to lin partition.)

 i want to use linux for everything that isn't win necessary but am lacking in some knowledge, im pretty good w/ drivers and firmware in win, but until this machine ubuntu worked perfect.

i guess what im trying to say is this seems a lil complicated for me to just wing it from a previous post.
...help , yea?

---

### Post by nachotronics on 2007-02-24
You get your wireless card working following **[these steps]("http://www.ubuntuforums.org/showthread.php?t=297092&highlight=edgy+dell+1390")**
The driver in that post is the one for any of these cards:

Dell Wireless 1350 WLAN MiniPCI Card, 
Wireless 1350 WLAN PC Card, 
Wireless 1370 WLAN MiniPCI Card, 
Wireless 1390 WLAN ExpressCard, 
Wireless 1390 WLAN MiniCard, 
Wireless 1450 WLAN miniPCI Card, 
Wireless 1470 Dual-Band WLAN miniPCI Card, 
Wireless 1490 Dual-Band WLAN MiniCard, 
Wireless 1500 Draft 802.11n WLAN mini Card

The procedure is exactly the same for your card using ndiswrapper, but you will need to get the windows drivers for your wlan card from [http://support.dell.com](http://support.dell.com)

After getting your wlan working you might want to install network-manager-gnome following **[this howto]("https://help.ubuntu.com/community/WifiDocs/NetworkManager?highlight=%28network%29%7C%28manager%29")**. This utility helps you set up WEP or WPA secured networks

---

