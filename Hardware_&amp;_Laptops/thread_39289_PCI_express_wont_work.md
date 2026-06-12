---
title: "PCI express wont work"
date: 2005-06-04
forum: Hardware &amp; Laptops
---

### Post by Abild on 2005-06-04
Hi

I just got a new computer put together consisting of:
AMD Athlon 64 3000+
DFI Lanparty NF4 Ultra-D
PowerColor Radeon X800XL with PCI-express

The problem is that Ubuntu won't detect the graphics card and i'm therefore not able to get the X server working,

I've tried to solve the problem by installing the ATI drivers. But they keep telling me that they cant find my X800

Right after the "Starting Ubuntu..." message is displayed during boot i see the two following errors:

PCI: Cannot allocate resource region of device 0000:05:00.0
PCI: Cannot allocate resource region of device 0000:05:00.1

The Xorg log states the folowing error:
(II) Primary Device is: PCI 05:00:0
(WW) fglrx: No matching Device section for instance (BusID PCI:5:0:1) found
(EE) No devices dected

Can anyone help me with this problem?

---

### Post by Abild on 2005-06-05
Nobody?

---

### Post by Abild on 2005-06-06
Come on guys. 37 views and no reply.

Is there really nobody who has expirience with ATI/nForce 4 PCI-express graphics in ubuntu?

---

### Post by codejunkie on 2005-06-06
are you using more than one video card in the system or just the one ati card?

---

### Post by Abild on 2005-06-06
I'm just using one card

---

### Post by GazaM on 2005-06-06
[QUOTE=Abild]I'm just using one card[/QUOTE]
 I have an nForce4 and radeon X700Pro PCI-express which I have been trying to get working with the ati drivers for months now with no luck. I have posted threads on these forums with no  decent reply's whatsoever. It seems that pci-e is too new at the moment for people to be able to give us help. By the way, that message at boot about pci resources etc. is one I had, but is gone now for some reason.

---

### Post by Chetic on 2005-06-06
I have the exact same processor and graphics card, man!
*Nobody* seems to be able to help with this.
I'm really starting to want hardware acceleration now.. vesa can be horrible.

**Somebody PLEASE help!**

---

### Post by voidlogic on 2005-06-06
I have built many linux boxes with PCI express. They were all nVidia based GPUs and worked like a charm. I got the one ATI X300 working with the 'vesa' driver set in the X config, try that. Use AMD and nVidia and you won't go wrong.

---

### Post by Abild on 2005-06-07
[QUOTE=voidlogic]I have built many linux boxes with PCI express. They were all nVidia based GPUs and worked like a charm. I got the one ATI X300 working with the 'vesa' driver set in the X config, try that. Use AMD and nVidia and you won't go wrong.[/QUOTE]
 Thanks alot man! My Xserver is working now :D

I seems like the current ATI driver don't support the X800XL. A new one will be out later this week so i'm hoping it will solve the problem. If not, i'm going to get a Geforce 6800GT

---

### Post by voidlogic on 2005-06-07
no problem, glad to help

---

### Post by mdruskin on 2005-06-28
So is it not possible to get X working with X800XL??

---

### Post by rezzakilla on 2005-06-28
:???:  euh..still the "vesa" mode

---

### Post by giardino on 2005-08-03
sup.... i have the same prob my system is. 
Motherboard: DFI lanparty nforce 4
ATI radeon X800XL (PCI XPRESS)
OCZ 2X512 MB PLATINIUM ED
ATHLON 939 WINCHESTER 3200+ @ 2.6 Ghz

THE PROB IS THE VIDEO CARD... i have cheked some forums. and we have to configure our LANS (ip address, subnetmask, and default gateway) to enter to the internet and download the driver for our video cards. We have to do all this by commands and i only know how to configure the LAN.

1. first is to configure the ip address and its subnetmask:
- ifconfig eth0 <ip address> netmask <subnetmask> 
Example: ifconfig eth0 10.0.0.2 netmask 255.255.255.0

-route add -net default gw <default-gateway> dev eth0 
Example: "route add -net default gw 192.168.2.1 dev eth0" will add the route required for this computer for its gateway.

now u have your LAN configured....

Then i dont know how to connect to the internet by a browser to download the video driver. Wich i expect some please contiunue helping here cuz im Linux newbie.

---

