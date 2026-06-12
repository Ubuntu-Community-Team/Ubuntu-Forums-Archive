---
title: "Acer Extensa 4420"
date: 2008-08-03
forum: Hardware
---

### Post by vanden12 on 2008-08-03
Hey I did a search and found all the threads to be locked. But I just got this and trying to get ubuntu fully working...


I read tons of things that say wireles works out of the box but that must not be so in my case...
\

Here the threads I found..

[http://ubuntuforums.org/showthread.php?t=746335](http://ubuntuforums.org/showthread.php?t=746335)

---

### Post by phidia on 2008-08-03
As it says there in the link you provided you need to enable the driver.
 It would be helpful to know what wireless card you have in your computer.
[This link]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") will be a start in that direction.

---

### Post by vanden12 on 2008-08-04
The Hardware test said this



Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 15)
Broadcom Corporation BCM4310 USB Controller (rev 01)

---

### Post by Maverynthia on 2008-08-18
I too am having the same problem, same set of Hardware.
I've tried many of the threads listed, but the problem stems from the fact that it's no "on" since it wants the switch on the laptop to be pushed which Linux doesn't respect. :<

---

### Post by RedAE102 on 2008-10-08
I have an Extensa 4420-5963 successfully dual booting Windows XP and 8.04.1 AMD64. The Hardware test lies.  It is not a BCM4310 USB controller, as Windows Device Manager also identifies it as.  If you turn the laptop over, there's a sticker on the bottom identifying the wireless card as a BCM4312.  You have two options for getting it up and running:

You could go the route I did, as described in this thread:
[Having trouble w/ Broadcom on Hardy? Give this a shot](http://ubuntuforums.org/showthread.php?t=880218)

Or you can go the ndiswrapper route, and use the XP drivers here.  I can only verify that these do indeed work on XP.  Acer USA and Acer Europe do NOT have working XP drivers listed for the 4420, but Acer Taiwan does:
[http://twcsddl.acer.com.tw//acerdl/upload/Notebook/Extensa/EX4420/Driver/WLAN//PGM00828-DR-XPX86-WLANB4312-4_170_25_12.zip](http://twcsddl.acer.com.tw//acerdl/upload/Notebook/Extensa/EX4420/Driver/WLAN//PGM00828-DR-XPX86-WLANB4312-4_170_25_12.zip)

For a full listing of properly working XP drivers for the Extensa 4420, follow the directions below.
[http://www.acer.com.tw/driver.asp](http://www.acer.com.tw/driver.asp)
To get to the Extensa 4420 driver page:
In the top of the 3 big drop-down menus at the bottom, select the second option.  In the second menu, select Extensa.  4420 should be shown in the third menu.  If it isn't, select it, and then click the button immediately to the right of that. Now, select Windows XP in the drop-down menu on the drivers page.

---

