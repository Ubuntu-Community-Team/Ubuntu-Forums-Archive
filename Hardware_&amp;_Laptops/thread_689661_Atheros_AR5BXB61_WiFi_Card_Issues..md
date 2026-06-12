---
title: "Atheros AR5BXB61 WiFi Card Issues."
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by Mire3212 on 2008-02-06
So, i've got a fresh install of Ubuntu 6.06 LTS, Dapper. I'm running it on a Toshiba Satellite laptop. Everything so far seems to be working, I've got sound (which was an issue from 7.10), I can play video (another 7.10 issue) but I can't for the life of me get WiFi working. I've got it hooked up to harline LAN right now, but can't seem to get the card to reckonize in the network util. it is an Atheros AR5BXB61 card.

lshw -C network

[INDENT]
*-network UNCLAIMED
[INDENT]
description: Ethernet controller
product: Atheros Communications, Inc.
vendor: Atheros Communications, Inc.
physical id: 0
bus info: pci@02:00.0
version: 01
width: 64 bits
clock: 33mhz
capabilities: cap_list
resources: iomemory:d0100000-d010ffff irq: 233
[/INDENT]
[/INDENT]

lspci

[INDENT]
...
0000:02:00.0 Ethernet Controller: Atheros Communicatsion, Inc.: Unknow device 001c (rev 01)
...
[/INDENT]

lspci -n

[INDENT]
...
0000:02:00.0 0200: 168c:001c (rev 01)
...
[/INDENT]

This is what i get when i run the above commands.... Anyone got any ideas why it can't recognize the card? I've followed the instructions here 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

to attempt to get it to work, i did use the ndisgtk utility to try to get it to work. It will load the driver in the window, but then if i configure network configurations, it doesn't show up with a wireless card, just my built in ethernet card and modem card. 

I'd appreciate some help if anyone can. Thank you!

Mire3212

---

### Post by Mire3212 on 2008-02-06
So i've been searching google as well for some info on the card i've got, so i found where someone used MadWiFi to get the card to work, which i did try but i couldn't figure out how to get madwifi to actually install or work... but they did mention that the other network devices may cause an issue if activated, so i tried:

sudo ifdown eth0

it deactivated....

sudo ifup ath0

...
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0

I figured this wouldn't work, because, well, if ath0 is recognized in the first place then it would show in the network config utility... anyway... anyone got some ideas??

Mire3212

---

