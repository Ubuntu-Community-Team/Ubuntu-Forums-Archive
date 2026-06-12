---
title: "No Wireless"
date: 2009-05-30
forum: Hardware
---

### Post by _PEM on 2009-05-30
I have an used Dell latitude D510 I put Ubuntu 9.04 on. Love it except a couple of things.
One;
Wireless.
When I ran it from the optical drive before I installed it it detected the wireless card and I was able to get a drive for it. I had it working. When I installed Ubuntu and ran it from the drive it will no longer detect the wireless card. 
Back when it did ( running Ubuntu from the cd ) the name of the driver was "Broadcom B43 wireless driver". 
Can you help me?

Thanks

---

### Post by _PEM on 2009-06-02
Bump

---

### Post by _PEM on 2009-06-26
Think I'm gonna have to replace the card.

---

### Post by tommcd on 2009-06-26
Don't replace that wireless card just yet.
You need to install the **b43-fwcutter** package. See this page from the Ubuntu wiki:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
Disable encryption on your wireless router, and see if you can connect to the internet. Then when you get online without encryption, work on getting online with encryption.

Write back if you need more help.

---

### Post by _PEM on 2009-06-30
I installed the b43 package but the laptop still refuses to recognise theres a wireless card.
That wiki was the most helpful thing yet though.

---

### Post by Ayuthia on 2009-06-30
Can you post the results of:
```
lshw -C network
lsmod|grep -e b4 -e ssb -e wl -e ndis
dmesg|grep b4
```
It will help us see what is happening with your wireless

---

### Post by _PEM on 2009-07-06
Sorry for the delay, I was out of town.
Maybe its the network, think I'll try a coffee shop.

paul@paul-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:be:40:89
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=99.141.137.163 latency=64 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:0b:9f:0a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5e:9a:df:bf:e7:e4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
paul@paul-laptop:~$ lsmod|grep -e b4 -e ssb -e wl -e ndis
b43                   131484  0 
mac80211              217208  1 b43
led_class              12036  1 b43
input_polldev          11912  1 b43
b44                    35984  0 
ssb                    41220  2 b43,b44
mii                    13312  1 b44
paul@paul-laptop:~$ dmesg|grep b4

---

### Post by tommcd on 2009-07-06
Try enabling the driver by using: system > administration > hardware_drivers, and see if Ubuntu recognizes your wireless and can enable it.
Also, assuming that you can enable the wireless card, disable all encryption on your wireless router and see if you can get online. Then work on getting online with encryption enabled.

---

### Post by _PEM on 2009-07-07
Nope. Thats kinda what this thread is about. See my first post again.

I went to a local coffee shop tonight. They claimed to have wireless and other poeple were working on laptops there. I got no bars and could not find a network. 

Idea; I had the wireless working from the CD, I should run the laptop from the CD again in the coffee shop. I'll post results.

---

### Post by _PEM on 2009-07-13
I should have time to run that test tomorrow. I'll post the results when I do.

---

### Post by Ayuthia on 2009-07-13
You might try to use the Broadcom STA option.  It can be activated through System->Administration->Hardware Drivers.  However, you also have a Broadcom 44xx series wired ethernet card.  This means that you will have to do a few extra steps in the Terminal:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo modprobe b44

```You will need to wait a few seconds for NetworkManager to catch up.  From there, hopefully you will be able to find a wireless site and connect to it.

---

### Post by _PEM on 2009-07-13
Im not sure what the the Broadcom STA option is, or how to use it. When I open hardware drivers no items are displayed. 
I ran the code but nothing happened.

---

### Post by _PEM on 2009-07-15
No bars. 

Same old story.

---

