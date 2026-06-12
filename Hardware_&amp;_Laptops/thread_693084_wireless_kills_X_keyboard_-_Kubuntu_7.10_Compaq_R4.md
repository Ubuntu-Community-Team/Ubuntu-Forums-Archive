---
title: "wireless kills X keyboard - Kubuntu 7.10 Compaq R4000"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by locutus42 on 2008-02-10
I just built a fresh install of Kubuntu 7.10 on the Compaq/HP R4000/zv6000 laptop and I thought it was all working. It was after I setup my Broadcom wireless network by copying firmware to /lib/firmware that I found out rebooting results in a dead keyboard once KDE starts.

To get around this, I either have to add eth1 to /etc/network/interfaces to stop KNetworkManager from initiating wireless, or I must physically disable the wireless via its power button. I'll have to see if removing power allows me to get wireless working after getting to the desktop.

The keyboard works in kdm and even into the first part of the KDE desktop startup. The keyboard then goes away once the knetworkmanager applet loads in the kicker panel.

What is really strange is that once everything is up and running, if I comment out the "eth1" entry in /etc/network/interfaces I can use/connect to the wireless network without any keyboard issues. Unfortunately, even if I tell knetworkmanager to disable wireless, the next login will result in the loss of the keyboard. Also, this causes an incomplete shutdown and requires the 4-sec holding of the power button to eventually shut down the system.

Does anybody know what is going on here?

---

