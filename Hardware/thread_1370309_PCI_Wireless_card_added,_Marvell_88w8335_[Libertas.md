---
title: "PCI Wireless card added, Marvell 88w8335 [Libertas]"
date: 2010-01-02
forum: Hardware
---

### Post by robblue2x on 2010-01-02
I added a PCI network card to my PC recently but cannot get it to work

I have installed the drivers with ndiswrapper but no joy

I have a USB wireless card that worked out of the box aswell (wlan0).

Here is the info

$ lspci | grep Marvell
01:06.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wg311v3 : driver installed
        device (11AB:1FAA) present

$ lsmod
Module                  Size  Used by
ndiswrapper           245248  0 

$ sudo lshw -C network 
 *-network UNCLAIMED 
 description: Ethernet controller 
 product: 88w8335 [Libertas] 802.11b/g Wireless 
 vendor: Marvell Technology Group Ltd. 
 physical id: 6 
 bus info: pci@0000:01:06.0 
 version: 03 
 width: 32 bits 
 clock: 66MHz 
 capabilities: pm bus_master cap_list 
 configuration: latency=64 
 resources: memory:e6000000-e600ffff memory:e6010000-e601ffff

---

### Post by adam814 on 2010-01-02
For starters it seems to be complaining that /etc/modprobe.d/ndiswrapper needs to be renamed to ndiswrapper.conf.

Honestly ndiswrapper has always been hit or miss for me.  Are you using the right Windows driver in ndiswrapper?  It should be for XP and if you run 64-bit you need the one for XP 64-bit.  I don't think Vista/7 drivers work at all.

What problem specifically are you having?  Does ifconfig give you an interface for it?  Are you having trouble connecting unencrypted and encrypted networks?

---

### Post by robblue2x on 2010-01-02
It doesn't show up at all in ifconfig/iwconfig

I renamed ndiswrapper to ndiswrapper.conf, that got rid of that warning, thanks

Im not sure if i used x64 drivers! I'll re-install them to be sure and let you know

---

### Post by robblue2x on 2010-01-02
I got the x64 drivers from here:
[http://ubuntuforums.org/showthread.php?t=320111](http://ubuntuforums.org/showthread.php?t=320111)

Installed but got error -22 when i modprobe ndiswrapper

all i neeedd was a reboot!

got wlan0 and wlan1 now in iwconfig

Thankyou for all your help!

---

