---
title: "Sound Card and Wifi issues"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by lordsonny on 2008-02-28
I'm a total newbie at this sort of thing (linux) and I'm no computer geek.:guitar:

I installed Wubi Ubuntu 7.04 recently on my Toshiba Satellite A135-s4437, according to the sticker on it.  It works fine, except that it won't detect my sound card or my wireless card.  Please help!

If you need more info, please ask.

---

### Post by Yellow Pasque on 2008-02-28
Try installing linux backports to update ALSA, i.e. go to the terminal and enter:
```
sudo aptitude install linux-backports-modules-generic
```

Then configure your alsa-base file according to this:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by Yellow Pasque on 2008-02-28
For your wireless, can you run these commands so we know what wireless chip you have and whether there's a module loaded for it?:
```
sudo update-pciids
sudo lshw -C network
sudo iwconfig
```

If you can't post the entire output of those commands because of no internet, what I'm really interseted in is the following lines in bold(i'm using my PC as example)

(sudo update-pciids won't work without internet)

```
sudo lshw -C network
     *-network
       description: Wireless interface
       [B]product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.[/B]
       physical id: 2
       bus info: pci@0000:03:02.0
       **logical name: wlan0**
       version: 20
       serial: 00:05:5d:98:2f:bf
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=ndiswrapper+netrtw** driverversion=1.52+, ip=192.168.0.3 latency=64 link=yes maxlatency=64 mingnt=32 **module=ndiswrapper** multicast=yes wireless=IEEE 802.11b
```

For iwconfig, just let me know if it finds wireless extensions on any of your network interfaces, or if all of them just say "no wireless extensions found"

---

### Post by superprash2003 on 2008-02-29
for your sound.. try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by lordsonny on 2008-03-07
product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth1


For iwconfig, it all say no wireless extensions found.

---

