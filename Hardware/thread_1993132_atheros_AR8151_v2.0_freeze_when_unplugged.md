---
title: "atheros AR8151 v2.0 freeze when unplugged"
date: 2012-06-01
forum: Hardware
---

### Post by Cowloon on 2012-06-01
I am running 12.04 64-bit on a toshiba satellite c655d-s5511 laptop.

lspci -nn

shows:

Network controller RL8188CE [10ec:8176] (rev 01)
Ethernet controller Atheros AR8152 v2.0 [1969:2062] (rev c1)

With a fresh install, if I unplug the ethernet cable, the system freezes and nothing is written to syslog.

I had got this to stop by installing the driver from realtek version 0005.1230.2011. And the "bleeding edge" driver from linuxwireless compat-wireless-2012-03-12-p, for the "alx" atheros driver. But, I then encountered problems with the proprietary radeon driver and reinstalled.

Now, with or without a wireless connection, with or without compat-wireless-2012-03-12-p installed, with or without the newer bleeding edge drivers (reinstalling ubuntu each time) and with or without linux-backports-modules-cw-3.3-3.2.0-24-generic, and with or without X running, the system freezes if I unplug the ethernet cable or boot without it plugged in.

Do you have any idea how to fix this? I would at least like to be able to start the laptop with no network. For that, I tried adding "blacklist atl1c" to /etc/modprobe.d/blacklist-atl1c.conf, but the modules is still installed.

---

### Post by Cowloon on 2012-06-01
About the blacklisting idea, I need to run update-initramfs to get the ethernet module to not load. So, a suboptimal solution is to blacklist the ethernet driver before unplugging the ethernet cable...:

echo blacklist atl1c > /etc/modprobe.d/blacklist-atl1c.conf
update-initramfs -u
shutdown -r now

Then reverse that when I want to plug it in. Whee.

---

### Post by Cowloon on 2012-06-09
Running fedora 17 64-bit this is fixed with kernel 3.4.0.

---

### Post by pieterio on 2012-07-06
hiya,

quite new to the (wonderful) world of linux myself....

installed ubuntu 10.04 lucid lynx on my new acer aspire 7250 (which i bought with linux linpus, a linux without gui, so no fun for me :))
the Ethernet controller Atheros AR8152 v2.0 didn't work but got the wireless going from installing ath9k from compat-wireless 2012-5-10

never got the ethernet going (didn't really try because everyone told me to go and get ubuntu 12.04
so i did...did install on its own immediately ethernet as well as wireless drivers, *however*...the same thing does happen: it freezes when i take out the cable...in fact, i disabled networking for the time being and now reinstalled 10.04 on the side (dual boot) because it doesn't give me any trouble...that is, i get the wireless to work and use that.

anyhoo...i've done some searching for solutions, it's a bit hard to go through every forum there is...so i now ask you; would you know of a solution for ubuntu 12.04 or should i, like yourself, go for fedora? (*what the hell is fedora actually? i'll look into that immediately)*

thanks
Pieter

---

