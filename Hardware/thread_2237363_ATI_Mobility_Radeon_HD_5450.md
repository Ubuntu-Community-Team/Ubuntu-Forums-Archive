---
title: "ATI Mobility Radeon HD 5450"
date: 2014-08-01
forum: Hardware
---

### Post by mftohfa on 2014-08-01
[SIZE=2][FONT=arial]Guys,

New to forms but a longtime Ubuntu user. I am looking to buy a used Dell Zino 410 HD with the below specs and am wondering if its worth it for $250 bucks. I am fine with most of the specs. My biggest concern is the Video card. Will it play well with Ubuntu and XBMC with 1080p @ and normal framerates?

[SIZE=1]Dell Zino HD 410. 
AMD Phenom II P960 Quad Core processor 
6GB of dedicated RAM
ATI Mobility Radeon HD 5450 dedicated video card.
Atheros AR8151 PCI-E Gigabit Ethernet controller.
DW1501 wireless-N WLAN wireless network card.
1TB hard drive.
[/SIZE][SIZE=1]DVD R/W +\- optical drive[/SIZE]

Please advice! 

thanks,
Ken[/FONT][/SIZE]

---

### Post by QIII on 2014-08-01
Hello!

The ATI HD series 5000 and greater are currently supported by a proprietary Linux driver, so fglrx will work if you decide to install it.

The default open source Radeon driver installed with Ubuntu will also work quite well.

The 5450 is an entry-level adapter, so don't expect high frame rates on the latest games.

---

### Post by mftohfa on 2014-08-01
Thanks for the quick reply. I am not expecting to play games on this machine but rather use it as a HTPC connected to a HD TV and also a Plex server. Would this do well or will it struggle?

---

### Post by coffeecat on 2014-08-01
*Thread moved to **Hardware**.*

---

### Post by Vladlenin5000 on 2014-08-01
> **mftohfa said:**
> Thanks for the quick reply. I am not expecting to play games on this machine but rather use it as a HTPC connected to a HD TV and also a Plex server. Would this do well or will it struggle?


It should be perfectly fine for your intended purpose.

---

### Post by Yellow Pasque on 2014-08-01
For HTPC, open-source driver is recommended (along with mesa-vdpau-drivers package).

---

