---
title: "thinkpad r61 wireless config"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by newbie61 on 2007-11-28
Hi everyone,

I'm a newbie with linux and slowly learning. I have a thinkpad r61 running ubuntu 7.1.
I'm having an issue with my wireless connection and need help to disable the built-in NIC that comes with the laptop. I have a buffalo g54 NIC card in the pcmcia port and would like to have it startup as the default when I boot up. The problem is, when booting up the built-in NIC loads using the atheros driver and I want it to load only the bcm4318 drivers for the buffalo NIC. I would have to manually untick the atheros driver connection and select the  bcm4318 connection every time. I checked the iwconfig and shows both ath0 and eth1. The ath0 configuration does not have a nickname for me to add it to the blacklist. I've tried using "blacklist ath0" but that does not work. Can someone tell how I can have the buffalo (eth1) load as default. thanks very much.

---

### Post by crouton on 2007-11-29
If you don't want the ath0 to load at all (which is what it sounds like) you could modify the /etc/network/interfaces file and comment out the 'ath0' lines.  Or just cut'n'paste it here so we can take a look at it.

---

### Post by newbie61 on 2007-11-29
thanks crouton,

that worked the way I wanted.

---

