---
title: "optimising the boot process for notebooks (and getting WPA-PSK support)"
date: 2005-06-05
forum: Hardware &amp; Laptops
---

### Post by dpod on 2005-06-05
I have what I think may be a partial solution to two Ubuntu problems, but I need help working out the details.

The problems are a) the slow start time loading Ubuntu (mostly while it does the network configuration and time check) and b) issues that ndiswrapper has with WPA support.

I have an Acer Aspire 1410 that (more importantly) runs the fairly common Linksys/Airconn IPN 2200 (rev 1) wan card. I'm using ndiswrapper to run the driver (?though this may be unnecessary in the current build?) and am using wpa_supplicant to handle my wpa protocols. I've also installed wifi-radar, but I don't think that's doing anything.

With ndiswrapper I can log on to an open system, but no encryption works. With wpa_supplicant, I am able to get WPA-PSK support by doing the following in a terminal after boot:

sudo ifconfig wlan0 up

sudo wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -Bw

sudo ifup wlan0


Because I need to do this after boot, the entire network config and clock business in boot is a waste of time: I need to reactivate wlan0 after boot no matter what happens, and there is no point checking the clock, since my AP won't give access.

So what I decided to do was build a "notebook boot" (perhaps this should be an option for future releases?): I dropped the network configuration and clock business from start up (allowing me to boot in about a third the time), and run the relevant script after boot.

Now what I'd like to do is try replacing the original network configuration with a shell script that does what I usually need to do after boot. I thought the best way of doing this was to 'remove' the original network configurations file (/etc/rcS.d/S40networking) and replace it with a new shell script with the three commands above. When I do this, though, I get a permissions error, probably because I need to be the sudo.

Any suggestions a) on a better way of doing this, or b) a better way of accomplishing the same goal. or c) objections to the idea that network configuration (certainly for laptops) is not quite an essential boot step given that the network login happens after boot is finished, meaning that nothing can depend on the configuration.

---

### Post by megajay on 2005-06-22
Hey, when you made you edited version of the boot file, did you just turn the things you didn't want the computer to do on boot to "NO"?  I tried this myself but haven't replaced the original boot config file with mine yet.

I have that same problem with it hanging up for like 2 minutes while it configures the network interface.  I don't even have a network to use right now.



Thanks.



Jay

---

### Post by MetalMusicAddict on 2005-06-22
I had a similar problem. I routed around the fourms and checked "/etc/network/interfaces" and saw my config wasnt being changed.

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
	map eth0 **<-**change to **wlan0**

 # The primary network interface**<- Move this down**
iface eth0 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1


**TO HERE!!**
iface wlan0 inet static
address 192.168.1.105
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid wireless
wireless-key 8A2371746E85105B85050E80C4

auto wlan0
```
Hope it helps. ;)

---

