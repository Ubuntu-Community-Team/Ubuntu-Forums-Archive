---
title: "Laptop WiFi Fails to Restart after Resuming from Sleep/Suspend"
date: 2015-11-01
forum: Hardware
---

### Post by kyrachris on 2015-11-01
The network card on a Lenovo Thinkpad X230 laptop was not responding after sleep/suspend. Here's the card info:

       description: Wireless interface
       product: Centrino Advanced-N 6205 [Taylor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: e0:9d:31:2f:ea:64
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.2.0-16-generic firmware=18.168.6.1 ip=192.168.1.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:f1c00000-f1c01fff

I followed some old solutions found on the forum here and added a "config" file in /etc/pm/config.d/ with the value SUSPEND_MODULES="iwlwifi". This appears to match the driver in use as seen above. However, the problem still occurs randomly. I have to reboot entirely to get wifi to work again, and this is extremely annoying, especially when I'm multitasking with several applications open, and they all have to be restarted.

This only happened after I upgraded to 15.10. (I also had severe problems on another computer after upgrading to 15.10. Seems like an unstable release.) Not sure if it would matter, but I'm using Gnome.

---

