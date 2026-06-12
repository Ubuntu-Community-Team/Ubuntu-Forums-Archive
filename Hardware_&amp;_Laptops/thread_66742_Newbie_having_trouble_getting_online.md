---
title: "Newbie having trouble getting online"
date: 2005-09-18
forum: Hardware &amp; Laptops
---

### Post by ubantunovice on 2005-09-18
Hi
I am a newbie at linux and have installed Ubuntu Hoary on a Toshiba laptop that has a built-in 802.11b (Toshiba mini-pci adapter - Agere windows driver) and a Hawking HWC54G (PC Card) adapter in my PCMCIA slot.

When I go to network settings, I find:
Modem Connection (grayed out, not configured)
Wireless connection - with PC Card icon (grayed out, not configured) 
Wireless connection - with PC Card icon: interface eth1 is active
Ethernet connection - with PCI card icon (grayed out, not configured)

At the top right panel is the icon for "Network connectoion:lo" and it shows both receiving and sending activity and the drop down box has no other options to monitor. (how do I scan for networks?)

using the root terminal I get:

iwconfig:
lo:       no wireless extensions
eth0:   no wireless extensions
wlan:   IEEE 802.11g/b+ (must be the PC Card?) ESSID: "STAF...." (not mine!!)
eth1:   IEEE 802.11 DS (must be the built-in wireless) ESSID: "a neighbor's"

I am assuming the eth0 is the HWC54G, but if so the card's LEDs are both dark. So, I deactivated eth1 and activated wlan0 and configured it with 
ESSID: any
Configuration: DHCP
.. and activated it.

The card's led remained dark. I still cannot connect to the web (which I do through a router at present configured with no encryption or security) on my wlan.

iwconfig now gives:

wlan0
IEEE 802.11g/b+ ESSID:off/any Nickname:"acx100 v0.2.0pre8"
...
Encryption key: off
Power Management:off
Link quality:0 Signal Level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0

eth1  
still shows the neighbor's wlan

Not sure where to go from here. Any help appreciated.

---

