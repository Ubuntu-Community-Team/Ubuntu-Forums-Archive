---
title: "Problems with Broadcom wireless card"
date: 2008-07-31
forum: General Help
---

### Post by marvlowe on 2008-07-31
I have an HP Pavilion dv6000 laptop with a broadcom BCM94311MCG mini-PCI card. I am running ubuntu 8.04. I am using Broadcom's B43 proprietary driver. It worked fine for several days but while online I suddenly lost my connection. Rebooting did not help. There have been no changes to my system. Ubuntu still recognizes the card and the monitor light indicates it is on. It also identifies the wireless network but it can not connect. Any suggestions on what I can do to try to correct the problem?

Marv Lowe

---

### Post by fragos on 2008-07-31
Click the Network Management icon in the applet bar. You can make sure you Wifi is selected as the network. This will also provide a path to manual configuration. You want the "Enable roaming mode" box checked in the properties of each connection option. Can you "ping google.com"? How about "ping 72.14.207.99" a valid Google IP?

---

### Post by marvlowe on 2008-08-01
Roaming is enabled on wireless. It worked fine for several days before I became disconnected when online and have not been able to reconnect since. From what I've read on this forum the Broadcom proprietary driver is flaky and I should get an Intel wireless card which has ubuntu support. I decided to do just that.

Marv

---

### Post by fragos on 2008-08-01
My Intel WiFi has worked flawlessly and automatically through the last three releases of Ubuntu.

---

