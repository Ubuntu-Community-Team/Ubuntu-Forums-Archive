---
title: "Installing Belkin F5D6020 PCMCIA Wifi Dell laptop"
date: 2006-01-03
forum: Installation &amp; Upgrades
---

### Post by dlall on 2006-01-03
Hi,

I have just installed ubuntu on my dell lpatop and i would like to use the belkin F5D6020 wifi card. I can see the wifi card in the system settings but it doesn't detect the wifi network.

Can someone help me in setting this up.

All help will be appreciated.

Devdutt

---

### Post by Danny Rafferty on 2006-05-08
Man in same position. Need Help.
Tried the rtl/belkin driver mix but no success.
I did the ndiswrapper thing and can see and activate the card, but there's no light on the card.

---

### Post by Danny Rafferty on 2006-05-08
LED looks like its trying hard but doesn't light properly.
I have experienced some strange keyboard symptoms while this is going and  and I also get this which doesn't right:
rafferty@feynman:~$ sudo dhclient ra0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
ra0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device

---

### Post by Danny Rafferty on 2006-05-14
This is a F5D6020 / WEP issue.
The card works without privacy turned on. No amount of fiddling will make it work. Do not bother with hex/ascii or open/shared or dhcp/static. Don't bother formatting the hex like this xxxx-xxxx-xx. Don't bother specifically entering the key into the command line, don't bother editing your interfaces file, don't bother trying to manually enter the key into the driver file.

Do not install a scanner or network manager. In fact the network manager install simply didn't work for me and the mail list looked like yet another nightmare.

Maybe just try WPA immediately. I haven't tried that yet, and am not sure I will. I'm very frustrated and irritated with the amount of time this taken from me.

Oh, if you can get any of your totem decoders working in three easy steps let me know. I'm sure someone has an easy solution for that one, but I don't think I'm going to spend 30 minutes searching around here and an other hour fiddling with it.

](*,)

---

