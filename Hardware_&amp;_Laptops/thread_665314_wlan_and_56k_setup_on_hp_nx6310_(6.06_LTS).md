---
title: "wlan and 56k setup on hp nx6310 (6.06 LTS)"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by archman on 2008-01-12
Hi there. I need your help on setting up ubuntu 6.06. I run it on laptop hp nx6310. I wanna setup wireless card (bcm4311) and 56k modem. I tried many tutorials about setting wlan, but none went well. For the start, how do I install ndiswrapper-1.51?
Whenever I want to install some prog I go to folder location, type ‘make’ in terminal and get:

make -C driver
make[1]: Entering directory `/home/archman/Desktop/ndiswrapper-1.51/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.15-26-386/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/archman/Desktop/ndiswrapper-1.51/driver'
make: *** [all] Error 2

What am I to do?

Tnx.

---

### Post by archman on 2008-01-12
i installed ndiswrapper and supplied him with driver this way:

tar -xyz ndiswrapper-1.51.tar.gz
             cd ndiswrapper-1.51
             sudo -s -H
             make uninstall --ignore-errors
             make --ignore-errors
             make install --ignore-errors
             ndiswrapper -i bcmwl5.inf
            #installing bcmwl5...
             ndiswrapper -l
            #bcmwl5 : driver installed
            #device (14E4:4311) present

but now when i try to do modprobe ndiswrapper it says: FATAL: Module ndiswrapper not found.

what now?

---

### Post by archman on 2008-01-13
anyone???

---

### Post by archman on 2008-01-15
tnx for the support lol

i installed ndis properly now, but wireless card does not appear in system-admin-networking
what am i to do? try another ndis?

---

