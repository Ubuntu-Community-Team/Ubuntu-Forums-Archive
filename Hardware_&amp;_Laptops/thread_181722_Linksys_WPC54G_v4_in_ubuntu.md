---
title: "Linksys WPC54G v4 in ubuntu"
date: 2006-05-24
forum: Hardware &amp; Laptops
---

### Post by scapermoya on 2006-05-24
I posted this over in another thread, but then realized it was for 4.1

I finally got ndiswrapper to recognize my wlan card, but heres my problem:

when i "iwlist scan", it shows the proper ssid, which is good
but then, "sudo iwconfig wlan0 channel 6 essid scotland mode Managed" kicks back with "Error for wireless request "Set Frequency" : SET failed on device wlan0 ; Invalid argument."

so i got rid of the "channel 6" part of the command, just to try, and it goes through without error. except that this makes the "link" light on the card solid indefinitely. "sudo ifup wlan0" kicks back a "Ignoring unknown interface wlan0=wlan0."

if i replace scotland with a non-existant ssid (like moocow for instance), the link light blinks a few times and then goes dark, blinking every once in a while as if its looking for the moocow.

any thoughts?

by the way, ifconfig doesnt show wlan0, if that means anything.

---

### Post by qb4ever on 2006-08-22
This maybe an old thread but have you set up your /etc/network/interfaces file?

Here's mine:
> 
"
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
**auto wlan0**
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0
**        map wlan0**
# The primary network interface
iface eth0 inet dhcp
**iface wlan0 inet dhcp**

"

The bold are the wireless commands

---

