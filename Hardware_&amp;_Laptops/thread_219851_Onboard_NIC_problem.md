---
title: "Onboard NIC problem"
date: 2006-07-20
forum: Hardware &amp; Laptops
---

### Post by ShadowRage on 2006-07-20
ALrighty folks, here's the scenario:

I bought myself an ASRock Dual 939-SATA2 mobo with an AMD64 3200+ cpu, and 512 mb of ram, etc.

Now then, after some tweaking with alsa, I got most of the onboard sound to mix. Just, now I need to manage to get all the OSS apps to play nice. (and after getting qsynth, midi support!)

Now, the other hurdle is, the onboard lan, which I know what the chipset is, it's a Realtek 8201 PHY (something along those lines, but is reported as a ULi M5261/M5263 (in dmesg anyway) It's the latter number according to LSPCI (M5263)

update: I updated the pci ids:

0000:00:11.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)

However the tulip driver still shows it as the other.


The official driver site, since being acquired by nvidia, only now supports windows, but I know that isnt much of an issue as the tulip driver loads the NIC up. The problem is, I get this error on initialization of the card in dmesg:
"[4296126.617000] eth0:  Invalid media table selection 128."

and I can even set up the interface with an ip address and it doesnt send or recieve packets, it doesnt fetch dhcp, and when I ping using that interface, I get "network unreachable"

any ideas?

I'm on ubuntu 5.10 (obviously)

however, I'm not using the latest kernel update, dunno if that is a problem. Also, is this fixed in Dapper?

Any module loading options that may fix this?

---

