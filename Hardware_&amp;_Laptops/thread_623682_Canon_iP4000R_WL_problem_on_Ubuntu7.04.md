---
title: "Canon iP4000R WL problem on Ubuntu7.04"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by Squirrel61 on 2007-11-26
Hello,

As a pretty experienced computer user, but new to Linux, I'm trying to setup Ubuntu 7.04 on my Toshiba Satellite Pro 6100 laptop. As far as the installation is concerned, there where *NO* problems, which surprises me pleasantly because even Windows XP SP2, which is pretty filled with drivers, can't install everything and especially is having severe problems with the VGA card (dedicated Toshiba drivers needed). Ubuntu installs everything fine from scratch, without needing additional downloads! Sound, VGA, Wireless card, thumbstick, everything that the laptop comes equipped with is working!

But my first deception came when installing my Canon Pixma (Pixus) iP4000R printer. Although it is included in the Ubuntu driver collection (cheers again!), I can't get it to fully work. My intention is to use it as a wireless network printer, as I did (and still do) on my Windows machines.

The situation: Wireless all-in-one ADSL-modem/router/Wireless AP Thompson/Alcatel Speedtouch 780i WL, Canon iP4000R connected dynamically through a wireless connection, several Windows computers connected wired and wireless to the Thompson and using the printer's full features.

The problem: Canon doesn't provide Linux drivers (bad, very bad!). The Ubuntu drivers include a iP4000 driver. I can setup the driver and when on the "Connection" tab of the printer's properties page, I select "Network Printer", "TCP/Socket" protocol. For "Host", I'm using "http://192.168.1.65" which is the IP-address my printer gets from the router. Could as well use the full network name for the printer, once it is working. For "Port", I'm using the proposed 9100. When sending a test page to the printer, the driver starts up, connects to the printer (I know this because the printer wakes up from sleep mode and starts preparing for the print job, making noises in the process) and starts sending data (power light on the printer starts flashing). But then the driver pauses. I can resume the printing, but within a second, it pauses again and keeps doing that.

It seems like the driver is expecting some feedback (status?) from the printer which it doesn't get.

I've been searching this and other forums and googling all around but couldn't find a working solution, so I hope someone has solved this problem for this or any other printer (the constant pausing).

BTW. The same problem applies to Turboprint, in case anyone think that could help...

---

### Post by Squirrel61 on 2007-11-28
The problem has been fully solved by just using the update manager to update to 7.10

---

