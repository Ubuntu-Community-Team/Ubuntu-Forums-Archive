---
title: "Configuring DWL-G650+ card (TI ACX111 Chip) at boot time"
date: 2006-04-02
forum: Hardware &amp; Laptops
---

### Post by dpm on 2006-04-02
Hi everyone,

I've got a D-Link DWL-G650+ pcmcia card on my laptop. After some trouble I managed to get it working under Breezy following this howtos:

[http://www.houseofcraig.net/acx100_howto.php]("http://www.houseofcraig.net/acx100_howto.php")
[https://wiki.ubuntu.com/WifiDocs/Device/DWL-G650+]("https://wiki.ubuntu.com/WifiDocs/Device/DWL-G650+")

and installing gtkwifi:

[http://gtkwifi.sourceforge.net/]("http://gtkwifi.sourceforge.net/")

Basically, I did not have to recompile the driver or anything, I just had to copy the right firmware that the card needs to download on every startup for initialisation purposes. Apparently, the firmware files included with Breezy were the wrong ones. There is a bug open for this ([https://launchpad.net/distros/ubuntu/+source/linux/+bug/26703)](https://launchpad.net/distros/ubuntu/+source/linux/+bug/26703)), which seems to have been solved for Dapper.

With this card I can connect to the internet by getting an IP address from my wireless router through DHCP.

However, even though the card is working (sometimes I get disconnected for a couple of seconds, though), I cannot get it to work before the desktop is loaded (i.e. at boot up). Even more, I cannot get it to work without gtkwifi running.

What I get is the "Configuring network interfaces" message at boot waiting until timeout or until I press CTRL+C to stop the script execution.

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
    map wlan0

auto wlan0
iface wlan0 inet dhcp
wireless-essid <here comes my ESSID>
wireless-mode managed
wireless-key <here comes my key>
``` 
Basically, there is no way to get the card to work until gtkwifi is executed. Using the standard 'network-admin' application only activates the card when gtkwifi is running, otherwise it stays forever in the "Activating interface wlan0" dialog. In fact, it seems to activate the card, but not to get an IP address.

Any ideas on how to activate and configure the card at boot time?

---

