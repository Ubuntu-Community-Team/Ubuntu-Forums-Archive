---
title: "network interface runs dhcp when plugged in"
date: 2005-12-01
forum: General Help
---

### Post by monkblah on 2005-12-01
Hi, I have kubuntu 5.10 on my laptop. The laptop has a built-in ethernet interface, called 'eth0.'

I think this interface is controlled by hotplug because it gets an IP address assigned & unassigned to it when I plug it into or unplug it from my network. This is good, but it insists on choosing its own IP address (192.145.0.52). I want it to use the address I specify, at least in certain situations.

I have set up the /etc/network/interfaces file to specify a fixed IP address, but the system does not obey me. It always sets itself for 192.145.0.52, which is wrong.

I have read the interfaces and hotplug man pages but honestly don't fully grasp how it works, particulary the 'mapping' part. Is a script named 'grep' being run? where is this script? 

Can someone explain this to me? It is getting really frustrating.

This is my /etc/network/interfaces file:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
#iface eth0 inet dhcp
#iface eth1 inet dhcp

iface eth0 inet static
        address 192.145.0.108
        netmask 255.255.255.0
        network 192.146.0.0
        broadcast 192.145.0.255
        gateway 192.145.0.1

iface eth1 inet static
        address 192.145.0.50
        netmask 255.255.255.0
        network 192.145.0.0
        broadcast 192.145.0.255
        gateway 192.145.0.1


```

Note: eth1 is my wireless interface, this works fine.

---

