---
title: "Two weird things since Breezy - computer shutdown and wlan0 error"
date: 2005-11-24
forum: General Help
---

### Post by Minilek on 2005-11-24
I have been having a couple problems with my laptop (a Dell p4) since upgrading to Breezy.  My computer randomly shuts itself down.  I can usually tell when it's about to happen since my laptop's fan starts being much much louder than usual for about 3-5 seconds beforehand.

Also, when I first booted up Breezy I got my wireless card up and running using ndiswrapper.  I also changed my /etc/network/interfaces to configure things how I wanted.  When I rebooted however, my wlan0 disappeared.  I get errors like this:

minilek@minilek:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

If you want to see what my /etc/network/interfaces looks like:

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
iface eth0 inet static
address 18.250.0.130
netmask 255.255.0.0
gateway 18.250.0.1

auto eth0

iface wlan0 inet dhcp
wireless-essid poop
wireless-key DECA-FDEC-AF

auto wlan0

Also, I don't mind playing around with Breezy, but I'm at a point right now where I need a stable laptop for a few weeks.  So, I was thinking I might downgrade back to Hoary then try to get Breezy working over Christmas break.  Is there a clean way to downgrade back to Hoary, and if so, does anyone know of a guide that says how?

---

### Post by kaamos on 2005-11-24
[QUOTE=Minilek]minilek@minilek:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device[/QUOTE]

Hello. 

You most likely have done this, but just checking.. Have you added ndiswrapper to /etc/modules ?

---

### Post by Minilek on 2005-11-24
No...I had never done this before with Hoary either though.  I did do ndiswrapper -m though for modprobe.  Was there something else I should have done too?

EDIT:  If it helps, the system seems to actually detect the physical wireless card (look at network:1).  Also, the drivers seem to be installed:

minilek@minilek:~$ sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:15:63:1a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.95 duplex=half ip=18.250.0.130 link=yes multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:faffe000-faffffff irq:17
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       resources: iomemory:faffc000-faffdfff irq:11

minilek@minilek:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present

I think the driver is the right one.  I used it successfully with Hoary at least.

---

### Post by Minilek on 2005-11-25
Ok, things are working now.  It turns out I was using the wrong driver (though why that wrong driver worked when I used Hoary is beyond me. :)).  Getting the correct driver fixed everything.

By the way, does anyone have the problem that sudo ifup wlan0 doesn't work?  I have to manually do:

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid blah mode Managed etc.
sudo dhclient wlan0

I thought this is exactly what ifup did (I modified my /etc/network/interfaces to have the right mode and essid), so I'm not sure why only doing this manually works!

---

