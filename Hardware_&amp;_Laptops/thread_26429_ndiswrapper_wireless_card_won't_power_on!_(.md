---
title: "ndiswrapper wireless card won't power on! :("
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by shayan on 2005-04-12
Okay, so I had Warty, and now I have Hoary, which is sa-weet, except for the fact that now I can't get it up (my wireless card).

I have an mn-720 (microsoft, yes, gasp) pcmcia wireless card. Obviously, due to its microsoftness, I'm using ndiswrapper. I have the module working, and doing an 'ndiswrapper -l' shows that the driver is installed, and that the hardware is present. However, when I do a modprobe ndiswrapper, it loads the module without turning the card on.. ..lsmod shows ndiswrapper, so the module is loaded and it thinks it's doing what it's supposed to, but it's not.

my /etc/ndiswrapper/mn720-ankh/14E4:4325.conf says this:

NdisVersion|0x50001
Environment|1
BusType|5
mac_address|XX:XX:XX:XX:XX:XX
ndis_version|Microsoft,06/13/2003, 3.20.23.0

antdiv|3
BTCoexist|1
Channel|11
EnableLEAP|1
frag|2346
IBSSGMode|2
Interference_Mode|-1
LegacyMode|0
NetworkAddress|
PLCPHeader|0
PowerSaveMode|0
RadioState|1
Rate|0
rts|2347

I don't know what this means, or if it's helpful at all, but I am totally l am totally lost on this one.. ..any gurus out there? or even other newbies who actually 
know what's going on? (unlike me)

---

### Post by François Battail on 2005-04-13
Shayan,

I don't know if it will helps you but in my case (Amd Ferrari 3000) the Wifi card was down too. Changing the line:

```
RadioState|1
```

to

```
RadioState|0
```

works fine for me.

---

