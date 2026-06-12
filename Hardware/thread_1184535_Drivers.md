---
title: "Drivers"
date: 2009-06-11
forum: Hardware
---

### Post by Joshua Mayer on 2009-06-11
Hey Everyone.

I am installing Ubuntu on my laptop which was originally designed for Windows XP. The laptop came with some drivers for the wireless card, but the driver is designed for Windows. I checked on the IRC channel if I could get the wireless card to work, and they said it might. So I want to check on the forums. The card is a \Dell Wireless 1350 WLAN Mini-PCI card. Does Ubuntu have a driver for that?


Thanks!

---

### Post by Idefix82 on 2009-06-11
Welcome to the free world :)

Can you open the terminal, type in
```
lshw -C network
```
and paste the output here?

---

### Post by Joshua Mayer on 2009-06-11
I haven't installed Ubuntu yet. I am downloading it now, but I was just wondering if my card was compatible.

---

### Post by Idefix82 on 2009-06-11
From what I read, it seems to be. Come back here once you have installed Ubuntu if you are having trouble with your WiFi.

---

### Post by Joshua Mayer on 2009-06-11
Should Ubuntu automatically install the a driver for the card during the install?

---

### Post by Idefix82 on 2009-06-11
> **Joshua Mayer said:**
> Should Ubuntu automatically install the a driver for the card during the install?

I don't know about the newest version. It seems that in the previous version you needed a tweak. Anyway, you will find out in a few minutes' time.

---

### Post by pmlxuser on 2009-06-11
Form experience most of the drivers for cards that were designed for machines running win Xp are supported. You shouldn't have alot of problems.. but after installing you can do as suggested by Idefix 82

---

### Post by Idefix82 on 2009-06-11
> **pmlxuser said:**
> Form experience most of the drivers for cards that were designed for machines running win Xp are supported. You shouldn't have alot of problems.. but after installing you can do as suggested by Idefix 82

There will very likely be no need to use a Windows driver.

---

### Post by Joshua Mayer on 2009-06-11
Thanks for the answers. Automatic Updates restarted my computer with 200mb to go, so I have to download again :(

---

### Post by Joshua Mayer on 2009-06-19
Finally I got ubuntu to install. 

I am having 1 problem. When I try connect to a wireless network, it doesn't connect. It just says disconnected, even though all the wireless network details are correct.

This is the output from lshw -C network
```
 *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 81
       serial: 00:0f:1f:a9:80:3e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A ip=192.168.0.23 latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:bb:28:1c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 32:4e:57:47:07:39
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by Joshua Mayer on 2009-06-19
Also, I can't find Networking (                                  System &#8594; Administration &#8594; Networking.). There isn't a shortcut. There is only network tools, so I can't search for the wireless :(

---

### Post by Idefix82 on 2009-06-20
Try installing the firmware for your card: type in the terminal
```
sudo apt-get install b43-fwcutter
```
and then provide your password. You might need to restart Ubuntu after that.

If it worked then you should be able to click the network icon in the top right corner and see a list of available networks.

---

### Post by Joshua Mayer on 2009-06-20
I run that and it says Couldn't find package b43-fwcutter

---

### Post by Idefix82 on 2009-06-20
> **Joshua Mayer said:**
> I run that and it says Couldn't find package b43-fwcutter

Can you do
```
sudo apt-get update
```
and then the same command as before? By the way, I am assuming that your wired connection works?

---

### Post by Joshua Mayer on 2009-06-20
I'll run that code when I get back onto Linux.

Wired connection works.

---

