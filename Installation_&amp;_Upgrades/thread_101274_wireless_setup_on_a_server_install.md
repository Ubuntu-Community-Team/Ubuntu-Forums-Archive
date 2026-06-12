---
title: "wireless setup on a server install"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by lerio on 2005-12-09
Hi,

i just performed a server-install and now I want to make my wireless pcmcia card (DWL-G650 D-Link Air Plus) work because I want to install the XFCE Desktop Environment.

*** Important: when i fully install Breezy Badger the wireless connection is already setup and working fine ***

Unfortunately, I'm a newbie and not so well trained to setup a wireless conneciton by myself. What I know is that when Breezy is fully installed, the wireless connection is called "ath0". ifconfig now is only listing "eth0" (which is the internal network card, which I don't use) and "lo" (which I don't know exactly what is).

Please somebody help me out with this. How do I manually setup a wireless connection?

Thanks!

_v

---

### Post by matthewv on 2005-12-09
I think you will need to load the kernel module for your wireless card. Try running ```
sudo modprobe madwifi
```No idea if that will work.. but give it a try. If it does work, add the line "madwifi" without quotes to /etc/modules. If that doesn't work, try using ndiswrapper

---

### Post by lerio on 2005-12-09
Hi Matthew,

thanks for your reply. The solution to my problem is probably easier for someone who's familiar with linux shell commands.
Basically the wireless card is working fine, but I don't know how to configure it.

how do i activate the ath0 connection? how do i set the IP address, ESSID. subnet, gateway etc. for my wireless connection?

Thanks,

_v

---

### Post by Lambert on 2005-12-09
sudo iwconfig ath0 essid ____  channel ___ commit

do man iwconfig if you need more info such as setting wep key or you maybe need to add the ap option

then

sudo ifup ath0

then

sudo dhclient ath0

if using dhcp or

sudo ifconfig ath0 xxx.xxx.x.x

if using static ip

using static you will also need to set up a name server in /etc/resolv.conf



search domnainnameserver.net
namerver xxx.xxx.xxx.xxx (where xxx = ip address of the name server)


and if you're connected with an ip but can't get to internet try this

sudo route default gw xxx.xxx.x.x (where xxx = ip or your router)

---

