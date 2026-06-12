---
title: "NIC not working after fresh install"
date: 2011-08-07
forum: Hardware
---

### Post by ubox on 2011-08-07
I installed Ubuntu 11.04 and it didn't find a driver for my NIC.

Ran at the terminal: sudo lshw -C network

Showed:

[HTML][sudo] password for ted: 
  *-network               
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth0
       version: 10
       serial: 00:08:54:3f:f1:b1
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:21 ioport:a000(size=256) memory:e1000000-e10000ff memory:20000000-2001ffff[/HTML]When I try System > Admin > Additional Drivers, it errors saying "downloading package indexes failed..."

EDIT:
I found this page:
[http://manpages.ubuntu.com/manpages/hardy/man4/re.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/re.4.html)

Which recommends that I compile a driver into my kernel file.  That sounds kinda sharky for a noob like me.  Is that what I should do?  I did a search on "kernel configuration file" and found several different files that are called that.  So now I am really confused.  

Also, I tried plugging in a USB wi-fi NIC and Ubuntu didn't respond to it.  Is there something I have to do to tell it to look at the newly attached device? 

Any help would be fantastic, thanks!

---

### Post by ubox on 2011-08-16
Update:

The NIC does show up when I do an LSMOD.  Still cant get it work  :(

---

### Post by ubox on 2011-08-16
Network works with a USB wi-fi NIC.  Ran update.  Unplugged the usb nic.  PIC NIC still doesn't work  :(

---

