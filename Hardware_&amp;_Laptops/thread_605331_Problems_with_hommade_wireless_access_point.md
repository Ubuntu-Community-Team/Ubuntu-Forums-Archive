---
title: "Problems with hommade wireless access point"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by YogiPaolo on 2007-11-06
Hello Ubuntu Community.

I have built my own wireless access point using various "howtos" found on the internet. Once I understood the process, it was rather easy. However, I'm having strange issues with connecting to this access point and I wonder if this has to do with: the way I have set up and configured the card and/or the drivers for this card.

I have the interface and bridge configured to come up and down with ifup and ifdown. 

When I scan for the AP, sometimes it shows up, sometimes it doesn't. I've scanned for the AP with several different computers running windows, ubuntu and gentoo. The results are spotty. Sometimes the machines can see the AP, sometimes they can't. An apple laptop can't see the thing at all. 

Below are the output of interfaces and iwconfig as well as the lspci showing my card type

Also, I don't understand what the wifi0 thing is. Is this a dummy device? It seems I can only configure the wlan0 and it works. Strange.


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface - do not touch this one.
auto eth0
iface eth0 inet dhcp

# Declare br0
iface br0 inet dhcp
#iface eth1 inet dhcp

# Begin pullup
# build bridge and bridge ports
bridge_ports eth1 wlan0
pre-up brctl addbr br0
pre-up brctl addif br0 wlan0
pre-up brctl addif br0 eth1

# Setup eth1. Make sure eth1 is down then bring up with 0000
#pre-up ifconfig eth1 down
pre-up ifconfig eth1 0.0.0.0 up

# Setup wlan0. Make sure wlan0 is down then bring up with 0000
#pre-up ifconfig wlan0 down
pre-up iwconfig wlan0 essid oxfordmil
pre-up ifconfig wlan0 0.0.0.0 up
pre-up ifconfig wifi0 0.0.0.0
pre-up iwconfig wlan0 mode master


# Begin bringdown

# Take down interfaces
post-down ifconfig eth1 0.0.0.0 down
post-down ifconfig wlan0 0.0.0.0 down

# Take down bridge
post-down brctl delif br0 eth1
post-down brctl delif br0 wlan0
post-down brctl delbr br0
 
```

```
 00:0f.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

```

```
 wifi0     IEEE 802.11b  ESSID:"oxfordmil"  Nickname:""
          Mode:Master  Frequency:2.412 GHz  Access Point: 00:06:25:09:0F:F9
          Bit Rate:11 Mb/s   Sensitivity=1/3
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off

wlan0     IEEE 802.11b  ESSID:"oxfordmil"  Nickname:""
          Mode:Master  Frequency:2.412 GHz  Access Point: 00:06:25:09:0F:F9
          Bit Rate:11 Mb/s   Sensitivity=1/3
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:62  Invalid misc:1410   Missed beacon:0

```

What the heck, here is what my bridge looks like too:

```

bridge name     bridge id               STP enabled     interfaces
br0             8000.000475bd5154       no              wlan0
                                                        eth1

```

I hope that's enough info.

---

