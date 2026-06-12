---
title: "getting wireless to connect on startup"
date: 2005-11-28
forum: General Help
---

### Post by nandasunu on 2005-11-28
I have wireless working fine on my laptop, but it seems that I need to reconnect it every time I boot up. This is a little annoying. It shows that it is (supposedly) connected at startup, but the internet doesn't work until I go into network-admin and deactivate the wireless, then activate it again. Is there some way to get it to automatically do this on startup?

---

### Post by soulestream on 2005-11-28
put your network information in /etc/network/interfaces

SSID, WEP key, etc


soule

---

### Post by ecobuntu on 2005-11-28
here is my /etc/network/interfaces that works automatically....copy it and/or adjust it at will...

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth1 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid any

---

### Post by nandasunu on 2005-11-30
Thanks for you help. I tried modifying my /etc/network/interfaces but it only made it worse :( I even tried copying and pasting the one posted above.

Any other ideas? The wireless shows as connected when I start up, but the internet doesn't work until I disable then enable it. Maybe theres a command line  action I can auto-run at startup so I don't have to manually do this every time.

FYO here is my /etc/network/interfaces:

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
iface eth0 inet dhcp
# wireless-* options are implemented by the wireless-tools package
wireless-mode managed

iface wlan0 inet dhcp
wireless-essid belkin54g

auto eth0

auto wlan0

```

---

### Post by Lambert on 2005-11-30
Try this change in the file.

mapping hotplug
script grep
map eth0

change this so it reads like this instead

mapping hotplug
script echo
map eth0

then add below it another one  that says this

mapping hotplug
script echo
map wlan0

at the bottom reverse the order so it reads like this.

auto wlan0

auto eth0

Do you ever use eth0? it may be worth commenting out all the lines pertaining to eth0 if you don't.

Post back if this works.

---

### Post by carlosqueso on 2005-11-30
Do you have the network-manager package installed? That gave me the same problem until I removed it.

---

### Post by nandasunu on 2005-11-30
> Do you ever use eth0? it may be worth commenting out all the lines pertaining to eth0 if you don't.

most of the time I don't, but sometimes I do (at university etc.)
 
> Post back if this works.

it didn't work ](*,) 

but...

> Do you have the network-manager package installed? That gave me the same problem until I removed it.

that worked!! \\:D/  thanks so much, thats one less annoyance to deal with...

---

### Post by carlosqueso on 2005-11-30
no problem...glad it's not just my messed-up computer :-)

---

### Post by Mr. Electric Wizard on 2005-11-30
When ya'll say Network-Manager are you talking about
System-->Administration-->Networking?
Is that the default network configuration tool in Breezy?

---

### Post by nandasunu on 2005-11-30
> When ya'll say Network-Manager are you talking about
System-->Administration-->Networking?
Is that the default network configuration tool in Breezy?

no, its a seperate package that you can install via synaptic to manage your wireless connections.

---

