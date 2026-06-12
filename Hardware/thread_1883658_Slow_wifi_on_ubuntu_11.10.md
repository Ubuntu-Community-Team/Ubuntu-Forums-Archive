---
title: "Slow wifi on ubuntu 11.10"
date: 2011-11-19
forum: Hardware
---

### Post by MA6ASRB on 2011-11-19
Hi,

New to the forum, so I hope this all makes sense.

I can see lots of people with this problem.

I have run the following;

```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```

This works a treat.  However now I need to make this permanent, and most threads say to add a line to the file /etc/modprobe.d/ath9k.conf.  They say to add the line
```
options ath9k nohwcrypt=1
```

However, I don't have this file.  In this directory I only have the following files;

```
alsa-base.conf              blacklist-modem.conf
blacklist-ath_pci.conf      blacklist-oss.conf
blacklist.conf              blacklist-rare-network.conf
blacklist-cups-usblp.conf   blacklist-watchdog.conf
blacklist-firewire.conf     libpisock9.conf
blacklist-framebuffer.conf

```

Any ideas how to make this a permanent change?

Thanks,
ma6asrb

---

