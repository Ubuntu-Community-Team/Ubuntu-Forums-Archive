---
title: "Wifi in HP laptop"
date: 2008-08-26
forum: Hardware
---

### Post by nuke_fluke on 2008-08-26
There is this button in my HP laptop which glows blue when you switch it on (The Wifi detecting device)...

It works alright in Vista..
But it does not glow in ubuntu although I can still manage to connect to the net just by pressing the button...

Why is the button not glowing?

Thanks in advance

---

### Post by Crafty Kisses on 2008-08-26
Post the results of
```
lshw -C network
```

---

### Post by nuke_fluke on 2008-08-26
WARNING: you should run this program as super-user.
PCI (sysfs)  
soumyashant@soumyashant-laptop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:b1:a3:36
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.78 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:7b:e9:98
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

---

### Post by nuke_fluke on 2008-09-16
Please help somebody...

---

### Post by sergiom99 on 2008-09-16
I have no idea, since your wireless card is working and its all about the button.
Check the forum's search results for your card to see if it already happened:
[http://ubuntuforums.org/search.php?searchid=48113986](http://ubuntuforums.org/search.php?searchid=48113986)

---

### Post by drpaul on 2008-09-16
I have an hp dv6000 [Intel chipset] and my wireless light used to turn blue under Gutsy, but no longer does so under Hardy. Wireless works but light doesn't change color.

---

