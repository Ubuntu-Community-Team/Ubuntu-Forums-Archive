---
title: "Slow boot and big periods of nothing in my Bootchart - please help"
date: 2008-07-29
forum: General Help
---

### Post by flogger on 2008-07-29
Hi,

My boot time is significantly slower than the Win XP that was previously installed. I used boot chart to profile the boot process. Could someone more knowledgeable than me take a look and suggest the next steps to take? There seems to be two periods of complete inactivity.

Cheers
Nick

---

### Post by jtniehof on 2008-07-29
Both periods seem to be where the network is trying to come up. Do you have any network cables unplugged? What is in /etc/network/interfaces ?

---

### Post by flogger on 2008-07-30
The following is in the file... I only use my wireless but sometimes plug in the wired... Cheers Nick

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid Nick

---

### Post by jtniehof on 2008-07-31
> **flogger said:**
> The following is in the file... I only use my wireless but sometimes plug in the wired... Cheers Nick
Yeah...you've got four wired interfaces in there that are looking for an IP address on every boot. (Do you actually have four network cards plus the wireless?) Unless you have fairly special needs (running a server?), just delete everything except the lo lines, and use the Gnome NetworkManager applet to handle your networks.

---

