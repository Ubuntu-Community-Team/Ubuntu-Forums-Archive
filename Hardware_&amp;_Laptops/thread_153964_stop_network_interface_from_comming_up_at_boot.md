---
title: "stop network interface from comming up at boot"
date: 2006-04-02
forum: Hardware &amp; Laptops
---

### Post by mojognome on 2006-04-02
Much to my frustration I have been unable to prevent my wireless NIC from comming up at boot.  I have both a wired (eth0) and wireless (eth1).

I have removed hotplug-net and ifupdown  entries from boot scripts via sysv-rc-conf.

My /etc/network/interfaces file is as follows:
[INDENT]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# -----------------Default Ubuntu Settings------------------\/
## This is a list of hotpluggable network interfaces.
## They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#       script grep
#       map eth0

## The primary network interface (ubuntu "default")
#iface eth1 inet dhcp
#wireless-essid Smith-Waybrant
#wireless-key **********
# -----------------Default Ubuntu Settings------------------/\
# ----------------Mojobuntu Laptop Settings-----------------\/
## Designed to be used with ifscheme

mapping eth1
   script ifscheme-mapping

## Wireless LAN eth1
# 504 Shelden
iface eth1-504 inet dhcp
wireless-essid Smith-Waybrant
wireless-key *********

# Forestry Atrium
iface eth1-forestry1 inet dhcp
wireless-essid forestry1

# Rovernet
iface eth1-mtu inet dhcp
wireless-essid MTU



## 10/100 LAN

mapping eth0
   script ifscheme-mapping

# Standard, DHCP for HonSnarf-MojosGnome Network
#  an incremented MAC to make WinXP/Ubuntu dhcp IPs come up diff(easily)
iface eth0-504 inet dhcp
hwaddress ether **:**:**:**:**:**

# ----------------Mojobuntu Laptop Settings-----------------/\
[/INDENT]

I also tried taking down eth1 with ifdown, then logging of "sav[ing] current setup."

After trying all of the above, eth1 (eth1-504) still comes up at boot.

Any suggestions would be helpful.

---

### Post by CiberAmigo on 2006-08-13
try comment out eth1, like this:

#mapping eth1
#script ifscheme-mapping

## Wireless LAN eth1
# 504 Shelden
#iface eth1-504 inet dhcp
#wireless-essid Smith-Waybrant
#wireless-key *********

# Forestry Atrium
#iface eth1-forestry1 inet dhcp
wireless-essid forestry1

# Rovernet
#iface eth1-mtu inet dhcp
#wireless-essid MTU


that should do the trick, hopefully :D 

Cencerly

CiberAmigo
http.//troejgaaard.dk  

troejgaard   |   trojgaard

---

