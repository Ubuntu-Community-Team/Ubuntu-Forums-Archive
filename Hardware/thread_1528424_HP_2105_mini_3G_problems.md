---
title: "HP 2105 mini 3G problems"
date: 2010-07-10
forum: Hardware
---

### Post by bawig1 on 2010-07-10
Hi Everyone,

I have just gone out and bought myself a HP mini 2105. I installed  Ubuntu Netbook remix and was loving it until i realized that the 3G  modem wasn't working properly. I do not think that the device is  supported. There are no entries under network manager and the sim card  is inserted correctly. Any help would be much appreciated as I am stuck  in hospital and need 3G to ward off cabin fever..

I read on another website that the netbook works with kubuntu 10.04 but  for ubuntu 10.04 you need to get firmware from HP, but i'm not sure if  this is true.

thanks,

Brett.

---

### Post by pdc on 2010-07-10
tell us more:

a separate modem? which provider?

tell us what

> lsusb

and copy and paste 

> dmesg | grep tty into a terminal and copy and paste the results back here; see if we can help

you can subscribe to a thread; (via clicking in thread tools); your email then tells you a reply is there ..

___________

> HP **2105** mini 3G problems

this wouldn't be the **2150** would it?

[http://www.liliputing.com/2009/01/hp-2150-mini-note-with-3g-on-its-way.html](http://www.liliputing.com/2009/01/hp-2150-mini-note-with-3g-on-its-way.html)

---

### Post by bawig1 on 2010-07-10
Hi pdc,

the model is definitely a HP Mini 5102. The 3G modem is built in (optus). The sim card inserts in a slot behind the battery. The output of lsusb is;

```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 5986:03b0 Acer, Inc
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```dmesg | grep tty;

```

[    0.000000] console [tty0] enabled

```hope this helps.

Brett.

---

### Post by pdc on 2010-07-10
thanks;

so a built-in modem ..

I wonder if lspci shows the device: can  you give us that printout

> lspciin a terminal 

the tty command shows not recognised yet; ttyUSB0 is good!

---

### Post by pdc on 2010-07-10
and I see this

> Ubuntu 10.04 

* 3G modem requires firmware files from HP, gobi_loader and some patched kernel modules due to bug in 10.04 default kernel*.

from here

[http://www.linlap.com/wiki/hp+mini+5102](http://www.linlap.com/wiki/hp+mini+5102)

We can get to that when we come to it ..

---

### Post by bawig1 on 2010-07-10
I have noticed the link before in google searches, but have no idea how to do it.

lspci;

```

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
01:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
43:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4381 (rev 11)


```the 3G modem does not seem to be listed :(

---

### Post by pdc on 2010-07-10
I suspect this will be the gobi loader issue;

if you are with optus, I would suggest instead an external usb modem from Optus and that will work; 

so would suggest transferring sim from internal to external ..

you can get them second-hand too

[http://computers.shop.ebay.com.au/items/Wireless__W0QQBrandZHuaweiQQ_catrefZ1QQ_dmptZAUQ5fModemsQQ_flnZ1QQ_sacatZ162340QQ_ssovZ1QQ_trksidZp3286Q2ec0Q2em282](http://computers.shop.ebay.com.au/items/Wireless__W0QQBrandZHuaweiQQ_catrefZ1QQ_dmptZAUQ5fModemsQQ_flnZ1QQ_sacatZ162340QQ_ssovZ1QQ_trksidZp3286Q2ec0Q2em282)

the gobi loader; firmware; HP issue has an on-going thread and some day it will get sorted

[http://newyork.ubuntuforums.org/showthread.php?t=1008200](http://newyork.ubuntuforums.org/showthread.php?t=1008200)

there are 18 pages;

Optus (and Virgin Oz) who use Optus; need CHAP disabled I believe

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

Need to disable CHAP (via Network Manager, edit settings, PPP settings tab)

---

### Post by bawig1 on 2010-07-10
hey pdc, thanks for all your help. I have an external usb stick that I am using. Hopefully one day the internal 3G modem will work.

brett.

---

### Post by pdc on 2010-07-10
that's good you have the external already; great! enjoy

If you are stuck in hospital, you can read the sagas of gobi-loader; qualcomm firmware; !!

some of able guys: Dan Williams from Fedora who works on network manager is involved in some posts on it; it will get sorted eventually, particularly as HP now sell laptops with linux preinstalled:

some Melbourne suppliers sell HP netbooks with linux preloaded (but I guess not with 3G installed ..)

funny thing is: your HP should give some printout with HP (from the USB I think) to acknowledge this internal 3G

---

