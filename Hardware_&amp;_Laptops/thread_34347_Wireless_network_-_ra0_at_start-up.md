---
title: "Wireless network - ra0 at start-up??"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by NetworkNed on 2005-05-14
Hi there,

I've installed a Ralink Rt2500 wireless network card following the [instructions on the wiki](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo), which were mostly pretty straight-forward, and I can get the card connected to the my WEP access-point & downloading from the net & stuff.

In order to do so, however, I have to wait until my laptop is booted up, open a terminal & run `sudo ifconfig ra0 up`. I can then run either the RaConfig2500 utility provided with the card or kWifiManager - both remember the WEP key & SSID I've entered into them & connect to the network. I then have to go back to a terminal & run `sudo dhclient ra0`.

I think it's possible to get kWifiManager to run a script to call `dhclient` after it connects to a network, and kWifiManager can be set to run in the system tray, so all I really need is for the `ifconfig ra0 up` to be done automatically. How can I achieve this, please?

I've tried tampering with /etc/network/interfaces, and adding the line "iface ra0 inet manual", but that doesn't seem to work. I'd rather not add the SSID & WEP key to /etc/network/interfaces - I can see that one can set up "home" and "work" profiles there, but I'd really rather do it through the GUI, so all I need is the `ifconfig ra0 up` running as part of the boot-process.

Suggestions?
Thanks in advance,

Ned.

---

