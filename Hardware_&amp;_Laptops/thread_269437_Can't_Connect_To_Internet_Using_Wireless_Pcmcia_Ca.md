---
title: "Can't Connect To Internet Using Wireless Pcmcia Card-Dell Inspiron 3700"
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by Todd0060 on 2006-10-01
New to and just installed Ubuntu 6.06 on laptop with linksys pcmcia card.  The card seems to be recognized, although as eth0, but even though I have DHCP and correct wep entered I cannot connect to Internet.

It seems the wireless connection is active and it sees my network id.

First, can anyone help.  I have read several support docs, but nothing seems to work.

Second, I installed network manager program and it seems to have installed ok, but I can't figure out how to launch the pgm.  It doesn't appear for me to select in any of the menus, such as Applications or System, etc.

Tks.

---

### Post by mzembe on 2006-10-04
I have had problems before where the wireless seemed to be functioning but stubbornly wouldn't connect. 
Once I was at a friends, using his DHCP style connection and it worked for a couple of minutes and just stopped while I was using the laptop(not some suspend issue) while the other computers were still connected fine. Rebooting several times didn't help, I exchanged hard drives with a spare clone drive and it started working again. 
Typically mine are configured static for my dialup gateway, and the drives are from identical laptops although one labels the network interfaces eth0 & eth1 while the other prefers eth1 & eth2.. 
Last time I was over there I reconfigured the network with wifi-radar and it worked, but hey, sometimes it would work anyways. After installing I couldn't find it in the menus so I had to open a terminal and run wifi-radar as root - later I changed the permissions of the /etc/wifi-radar.conf so I could run it as a user with a key combo or from alt-f2. Probably a bad idea to go around telling everybody my /ETC/WIFI-RADAR.CONF HAS ALTERED PERMISSIONS, lol.

---

