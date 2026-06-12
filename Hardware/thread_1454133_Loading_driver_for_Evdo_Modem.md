---
title: "Loading driver for Evdo Modem"
date: 2010-04-14
forum: Hardware
---

### Post by dreamgazer on 2010-04-14
I've just recently bought a mobile with Ev.do Modem built in it.
after skimming though various website, i was able to install it using these commands:

sudo lsusb
sudo modprobe usbserial vendor=0xXXXX product=0xXXXX
sudo dmesg

the problem is: i have to do this every time i'd like to go online. is there anyway to automate it?
plus, there's this warning after typing the second comand (the "sudo modprobe bla.. bla.. bla.."):

Warning: All config files need .conf: /etc/modprobe.d/bad_list, it will be ignored in a future release.

Thanx before.

---

