---
title: "Please Help 128 Bit WEP"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by routerstu on 2005-05-19
I am attempting to use a cisco aironet 350 with 128bit wep.  I am nto able to get it to work.  I have tried the gui, iwconfig, and editing /etc/network/interfaces, and entering wep key with xxx-xxxx-, and without dashes.


Can someone please help.  I also have an orinoco card, but the cisco was in during install so I am not sure of any issues caused by swapping cards.


Thanks for your help in advance

---

### Post by routerstu on 2005-05-19
got it working.  AP must be configured for OPEN, not SHARED wep.  posted below is /etc/network/interfaces for others



# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
auto eth1
iface eth1 inet dhcp
wireless_essid home
wireless_key ABC7-4395-1111-1111-1111-8585-73
wireless_mode managed
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map wifi0

---

