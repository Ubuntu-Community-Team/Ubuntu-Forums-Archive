---
title: "Configuring the net"
date: 2005-01-15
forum: Installation &amp; Upgrades
---

### Post by Pink Floyd on 2005-01-15
the first time I installed ubuntu I had my pc connected, so dhcp did all itself.
but now I have installed ubuntu without the net, and connected my pc only after the installation.
what have I got to do to configure the net? 


I have also another question: what is a good tool to see reiserfs partitions from WinXP?
I tried rfstool and it finds the partition, but it doesn't see the files contained in it.

Thank you,
Pink Floyd

---

### Post by Pink Floyd on 2005-01-15
first problem (net) solvet running dhclient

---

### Post by socrazy143 on 2005-01-15
You could also bring up a console and use

sudo ifup eth0

replacing eth0 with whatever you are using to connect.  I use ath0 for wireless and some use wlan0.

---

### Post by Pink Floyd on 2005-01-16
ok, but does anybody know a good tool for looking into the reiserfs partition?

---

