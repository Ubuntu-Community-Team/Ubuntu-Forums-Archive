---
title: "Can't have wireless at boot"
date: 2004-11-17
forum: Hardware &amp; Laptops
---

### Post by thibaud on 2004-11-17
Hi, 

- I installed my wireless PCMCIA card following the ndiswrapper HOWTO
- I added ndiswrapper in /etc/modules (or something like that ) so that it is loaded automatically
- Running "ifup wlan0" from a root terminal under Gnome works perfectly :)

But, if I ask for wlan0 to be activated at boot, network doesn't work and 
I have to "ifdown wlan0","ifup wlan0" to make it work. (ifup alone is not enough).

Thank you very much for this distro, it is by far the best I've ever tried. :)

---

### Post by orkolorko on 2004-11-23
The reason IMHO is that ubuntu is doing the script for configuring network devices before he enables the PCMCIA.
But I donàt know how to change its behaviour.

---

### Post by thibaud on 2004-11-24
Thank you for your answer. It is not a solution, but it helps me to find one.

How do you know that PCMCIA is started after Network ?

I assumed it was'nt the case, since the lights of my wireless card turned on when Ubuntu brought network up during the boot process.

---

### Post by bmichel on 2004-11-24
In file /etc/network/interface your must have something like:

# The primary network interface
auto wlan0
iface wlan0 inet static
address 192.168.0.92
netmask 255.255.255.0
broadcast 192.168.0.255
network 192.168.0.0
gateway 192.168.0.100


where auto wlan0 says to auto start your wireless card. I experienced some conflicts with the integrated ethernet card (eth0) so I deactivated it.

You must be able to handle that through the gnome-network app.

---

### Post by thibaud on 2004-11-25
Here is the part of my /etc/network/interface concerning wlan0:

iface wlan0 inet dhcp
name Liaison par onde radio
wireless_essid ma maison

I also had conflict with eth0 and I also disactivated it through the gnome-network app.

I tried to manage the 'on boot' problem with wireless both with the gnome-network app and by adding "auto wlan0" before 
"iface wlan0 inet dhcp" in /etc/network/interface, but both ways give me the same problem. wlan0 seems to be up (ifup wlan0 complains), but the network doesn't work .

---

### Post by bmichel on 2004-11-27
iface wlan0 inet dhcp

Your wireless card is configured to use a dhcp server. are you sure that you have one ? else use static address instead.

could you see your wlan0 with : ifconfig

---

### Post by bmichel on 2004-11-27
Another point that I manage to be sure to boot on wireless:  Activate your wlan0 on the default profile (unknown/inconnu) and remove the ethernet card from it.

---

### Post by thibaud on 2004-11-27
Thank you for your interest bmichel,

I'm sure I have a DHCP server. Otherwise, "ifup wlan0" would not work once in GNOME.
 
I saved my network profile under "original". 
I removed eth0 from "Unknown", which is still the default profile.
I checked "on boot" for wlan0, which was still activated and rebooted.

I still have the same problem, once in GNOME: 
* Network doesn't work
* "ifconfig" reports only "lo"
* "ifup wlan0" reports "ifup: interface wlan0 already configured".

By the way, with "on boot" checked, network need a long time, but finally reports [OK] during the boot process. And a few lines after, it complains about "unable to resolve name" trying to find the time server. Once in GNOME, Network works after "ifdown wlan0; ifup wlan0".
Witout "on boot", Network works after "ifup wlan0", which takes around 1 second.  

When I'm in windows, wireless need time before to be available. So I wonder if Ubuntu doesn't try to early or doesn't wait long enough, who knows...

---

### Post by Hendry on 2004-12-02
What kind of wireless card are you using? My wireless SMC PCMCIA card didnt work unless I added the firmware to my machine. See [www.prism54.org](www.prism54.org) for information about obtaining the latest firmware. I just copied the file to my Ubuntu system and I had no problem activating my card after this  :D

---

### Post by thibaud on 2004-12-02
I have a WN825G PCMCIA card from Mororola. The ndiswrapper wiki reports that it has a BroadCom chip and that it works with ndiswrapper 0.9+ (I have 0.10-1).
So, it seems that I'm not in your case, but thank you for your interest.

---

### Post by orkolorko on 2004-12-16
I'm sorry it took me a so long time to reply.
I think pcmcia services start after the network configuration because the pcmcia subsystem if you look at the start messages you get:

configuring network                         ok
.
.
.
other stuff

.
.
.
configuring Pcmcia
or something like this.

---

### Post by djgenesis on 2005-09-01
Hey guys... i have the same problem with my PCMCIA .. This is what happens when you try to get a cheap one ...you don't get the proper drivers.. Anyway
I would suggest to run these two lines of code somewhere along the startup while the kernel is loading but after it has set the PCMCIA devices up...

From all the ubuntu users out there... does anyone know how to do that ?
 :smile:

---

### Post by djgenesis on 2005-09-01
uummmmm......
"2 lines of code" = ifdown wlan0 ; ifup wlan0

---

### Post by gnerdman on 2005-09-11
I managed to kludge a solution together for this.  The problem is that networking starts in /etc/rc0.d/S35networking (which is a symbolic link to /etc/init.d/networking) while pcmcia services start in /etc/rc3.d/S??pcmcia which is a symbolic link to /etc/init.d/pcmcia).

At first I tried creating a symbolic link from /etc/rc0.d/S32pcmcia to /etc/init.d/pcmcia, but for some reason, it still came up *after* networking, even though it was in the start order *before* networking (never did figure out why).  So I kludged it by starting pcmcia services from within the networking startup script like so:

#!/bin/sh
#
# manage network interfaces and configure some networking options

**/etc/init.d/pcmcia start**

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

if ! [ -x /sbin/ifup ]; then
    exit 0
fi

[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

spoofprotect_rp_filter () {
    # This is the best method: turn on Source Address Verification and get
    # spoof protection on all current and future interfaces.

....<and so on>

That fixed the start order problem, even if it is kinda sleazy.  The next step was setting up the wireless interface (which installed as eth0) in /etc/network/interfaces:

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

auto eth0
iface eth0 inet dhcp
wireless_essid <my_essid>
wireless_mode Managed
wireless_rate auto
wireless_ap <lan_mac_address_of_my_router>
wireless_channel 9
wireless_key <my_wep_key> restricted

Works like a charm, even if it is cheating.  The trick to the whole thing was forcing pcmcia to start before networking.  Hope this helps someone out.

---

