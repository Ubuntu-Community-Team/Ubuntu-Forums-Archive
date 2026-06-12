---
title: "wireless not enabled"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by slingre87 on 2007-03-25
on my network settings, where it allows you to activate eth 0 and eth1, eth1 doesn't show up. Does anyone know the command to activate it from the terminal?

Thanx much

---

### Post by handaxe on 2007-03-25
Is that wireless card properly configured, is the driver installed ??


```
sudo lshw -C network

sudo ifconfig

sudo iwconfig
```

for starters please, from a terminal command line and post outputs here. That way folk will have something to assess.

HA

---

### Post by slingre87 on 2007-03-25
*-network:0 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       resources: iomemory:c0200000-c0201fff irq:10
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:40:e0:b5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.117 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:c0202000-c02020ff irq:217


-----------------------------------

slingre87@slingre87-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D4:40:E0:B5
          inet addr:192.168.1.117  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe40:e0b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49506 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:66000156 (62.9 MiB)  TX bytes:4082476 (3.8 MiB)
          Interrupt:217 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1511 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1511 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:460201 (449.4 KiB)  TX bytes:460201 (449.4 KiB)

-----------------------------

slingre87@slingre87-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

I've got a broadcom 4318
I can't get it to work at all

---

### Post by handaxe on 2007-03-25
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

Seen that? Hope not, as there is hope if you haven't.

The outputs show quite clearly that the card is not configured. See if the above link can get you going.

HA

---

### Post by slingre87 on 2007-03-25
I know they're not configged. I'm not quite sure how to do it

---

### Post by slingre87 on 2007-03-25
Okay, now when Ubuntu is booting, when I pay attention, I noticed that 'Starting PCMCIA Services doesn't have an ok after it...does this have anything to do with my wireless not working?

---

### Post by handaxe on 2007-03-25
Hi,

Did you read that how-to that I linked in?  I don't have and never have had the broadcom card so only know as much as I read in that thread and thus as much as you will after reading it too.

If you go to the "wireless & networking" forum and  search for the make of your card you will get many hits.  A bit overwhelming, I know.  I chose the one I thought directly addressed what you needed to do but there is more info available.

There is another possible route to follow and that is to install ndiswrapper (from synaptic is one way) and use the Windoze drivers. Search the forum mentioned above for your card make & ndiswrapper - should give some help.

Below is a link for NetworkManager, that might help once the card works.

[http://www.ubuntuforums.org/showthread.php?t=341357](http://www.ubuntuforums.org/showthread.php?t=341357)

Other than this, I am not sure how much more I can do.

HA

---

### Post by handaxe on 2007-03-25
> **slingre87 said:**
> Okay, now when Ubuntu is booting, when I pay attention, I noticed that 'Starting PCMCIA Services doesn't have an ok after it...does this have anything to do with my wireless not working?

Is your card a pcmcia card?  The outputs you gave indicate pci (Doh!!! this is how a pcmcia wireless-card could appear - sorry)

HA

---

### Post by handaxe on 2007-03-25
As far as I can tell, this card is pci.  So no, a pcmcia problem will not affect it.

A few more links:

[http://www.ubuntuforums.org/showthread.php?t=190177](http://www.ubuntuforums.org/showthread.php?t=190177)

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

[http://ubuntuforums.org/showpost.php?p=1189681&postcount=105](http://ubuntuforums.org/showpost.php?p=1189681&postcount=105)

Good luck

HA

---

