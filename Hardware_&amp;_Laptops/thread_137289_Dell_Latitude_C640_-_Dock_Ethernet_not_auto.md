---
title: "Dell Latitude C640 - Dock Ethernet not auto"
date: 2006-02-27
forum: Hardware &amp; Laptops
---

### Post by jermz on 2006-02-27
Here's the story. I've got a Dell Latitude C640 laptop with a docking station. The Ethernet adapter in the dock works, but will not come up automagically at boot. If I do an "ifup eth3" in a terminal window, it comes up just fine. The output of *lspci* (below) indicates that there is a separate PCI bus assigned to the docking station:

*lspci* output:

0000:02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:03:08.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

The 0000:02:00.0 is the Ethernet adaptor on the laptop itself. The 0000:03:08.0 is the dock Ethernet.

I have tried the hotplug mapping facility in */etc/network/interfaces*, to no avail. Here is my *interfaces* file:

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
       script grep
       map eth3

# Onboard Ethernet
iface eth0 inet dhcp

# Dock Ethernet
iface eth3 inet static
address ***********
netmask 255.255.254.0
gateway *********

# Wireless Interface
iface eth1 inet dhcp
wireless-essid *******
wireless-key ***********************

auto eth3

Any ideas? It's a bit frustrating.

Jeremy

---

