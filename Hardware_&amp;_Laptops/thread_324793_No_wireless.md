---
title: "No wireless"
date: 2006-12-24
forum: Hardware &amp; Laptops
---

### Post by urthshu on 2006-12-24
Good afternoon - 

This is probably not a big deal, but I can't seem to work it out from the documentation. 

I'm using a Toshiba Satellite m115-s1061 w/Edgy Eft installed. Everything works great except for the onboard Atheros 802.11 [b/g]. This is the first time I've used laptops with Linux of any flavor. 

When going into Networking, I've got Ethernet and Modem listed, but not Wireless. As far as I can tell, the madwifi module is installed properly - and just to be certain, I've reinstalled that. 

lshw shows eth controller at bus: pci@2.00.0 and - maybe its not helpful, but - 

# lsmod | grep ath
ath_pci               100000  0 
ath_rate_sample        16512  1 ath_pci
wlan                  207580  3 wlan_scan_sta,ath_pci,ath_rate_sample
ath_hal               192976  2 ath_pci,ath_rate_sample

So I *think* the card is being recognised on the hardware level, the driver is installed, but they don't seem to be matching up. 

lspci reads:

lspci -v | grep subordinate
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
        Bus: primary=00, secondary=08, subordinate=0a, sec-latency=0
        Bus: primary=00, secondary=0b, subordinate=0d, sec-latency=64
        Bus: primary=0b, secondary=0c, subordinate=0c, sec-latency=176

Any ideas would be most welcome. TIA

- Mark

---

### Post by disabled_20220313 on 2006-12-24
```
iwconfig
``` will bring up if your machine has recognised any networking devices with wireless extensions.

Other than that, I'm out of ideas.

---

### Post by urthshu on 2006-12-24
Ah, knew I forgot something...

I've tried iwconfig, didn't locate it. Thanks just the same. 

Also, before anybody asks, this is being done with the antenna switch to 'ON' :) 

And... wlanconfig returns 'unknown command' or some such. Could that be part of what's going on???

---

### Post by urthshu on 2006-12-24
ttt

---

### Post by disabled_20220313 on 2006-12-25
I don't think wlanconfig exists as a command on Ubuntu. 

If ```
iwconfig
``` didn't pick up any wireless extensions on the hardware you have a more complicated problem.

Though I've just remembered that iwconfig only shows wireless cards that have been "up'pped".

Try running ```
iwconfig wlan0 up
``` that may start the wireless card. And then you can start with the joys of networking.

Fingers crossed.

---

### Post by urthshu on 2006-12-25
erm... 

wlan unknown command "up"

:-| 

Can't for the life of me figure out what's wrong.

---

### Post by urthshu on 2006-12-25
OK, with it now - running DD & EE live disks

iwconfig shows:
lo, eth0 sit0 "no wireless extensions"

wlan0 up shows: "unrecognised wireless request "up" "

there is no wireless connection option on networking

FWLIW, SimplyMepis 6.0 livecd shows much the same, but without sound - so score one for Ubuntu. ](*,) 

I realise much of that is repetitive, but you never know what's important to whom.

---

### Post by urthshu on 2006-12-25
-More-

from lshw:

*-network UNCLAIMED
description Ethernet controller
product: Atheros Communications, Inc.
...
physical id: 0
bus info: pci@200.0
...

---

### Post by urthshu on 2006-12-25
[http://ubuntuforums.org/showthread.php?p=1929848]("http://ubuntuforums.org/showthread.php?p=1929848")

Someone else has the same issues, same manufacturer too. Thank you, ciaran, for your help - in the interest of simplicity, I'll follow some of that thread and see how it goes.

---

