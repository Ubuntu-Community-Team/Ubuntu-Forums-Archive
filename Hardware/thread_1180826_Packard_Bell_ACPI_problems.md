---
title: "Packard Bell ACPI problems"
date: 2009-06-07
forum: Hardware
---

### Post by FPtje on 2009-06-07
Hi I'm having problems with my 
Packard Bell MH45-u-004NL laptop.

Whenever I go to suspend mode(in linux mint, based off Ubuntu) I get these problems:
1. Wifi stops working after I get back from suspend mode., and the only way to make it work again is to restart the laptop. When I try to connect to a local net work it just says "You are now disconnected".
When I turn networking off and on again it says the device is not available.
2. When I lower my brightness before going into suspend mode, the brightness will be 100% again when I come back from suspend mode. When I then change the brightness, it immediately jumps back to the lower value again.

I am running Linux Mint. 
on Mint IRC they said it was an ACPI problem.
This is the driver page for my laptop:
[http://support.packardbell.com/uk/item/?pn=PC31Q00786&g=2000](http://support.packardbell.com/uk/item/?pn=PC31Q00786&g=2000)
But there are no linux drivers on it at all.

Googling ACPI drivers ubuntu has no results either.
Looking in synaptics for packard bell/packard/bell/MH45 shows no results.

How do I fix these problems?

EDIT:
SOLUTION FOR WIFI STOPPING:
sudo modprobe -r rt73usb && sudo modprobe rt73usb

If you have a different laptop replace rt73usb with the module you're using for your wifi card.

---

### Post by FPtje on 2009-06-22
Please respond I'm waiting 2 weeks already...

---

### Post by Idefix82 on 2009-06-22
Not sure about the brightness. For the wireless, I would think that completely restarting the wireless driver should fix the problem instead of rebooting. Let's try. If your wireless is working now, can you open the terminal, type in
```
lshw -C network
```
and paste the output here? This will show which wireless driver is responsible for the card.

---

### Post by FPtje on 2009-06-23
```
falco@FPtje-laptop-mint ~ $ sudo lshw -C network
[sudo] password for falco: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:ba:d7:e4
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0d:f0:5c:de:68
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.103 multicast=yes wireless=IEEE 802.11bg

```

That's it! thanks for responding!

---

### Post by Idefix82 on 2009-06-23
Judging by your output, your wireless card is not recognised at this moment. Is it the wireless or the wired connection that stops working?

---

### Post by FPtje on 2009-06-24
The wireless stops working, the wired still works

Note: the wireless works before going into sleep

---

### Post by Idefix82 on 2009-06-24
> **FPtje said:**
> The wireless stops working, the wired still works

Note: the wireless works before going into sleep

Can you please execute the above command _while your wireless is working_ and paste the output here?

---

### Post by FPtje on 2009-06-24
```
falco@FPtje-laptop-mint ~ $ sudo lshw -C network
[sudo] password for falco: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:ba:d7:e4
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0d:f0:5c:de:68
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.103 multicast=yes wireless=IEEE 802.11bg
falco@FPtje-laptop-mint ~ $ ping www.google.nl
PING www.l.google.com (74.125.77.106) 56(84) bytes of data.
64 bytes from 74.125.77.106: icmp_seq=1 ttl=55 time=17.7 ms

```

There is not a single wire connected to my laptop except for the power...
Like last time I entered the command...

I tried installing the Ralink linux drivers but it either didn't help or I did it wrong..
It seemed to install correctly though...

---

### Post by FPtje on 2009-06-28
I tried installing the rt73usb drivers from Ralink, but without any effects. :(

Any idea? I've got a dual boot with vista, could I take the driver from vista and use it in mint somehow?

---

### Post by FPtje on 2009-06-30
Bump, any idea?

Problems in a nutshell:
After coming back from suspended mode:
- "You are now disconnected" and unable to connect to a network(it still finds networks though, but when I try to connect it says "You are now disconnected")
- Brightness goes up completely even though I turned it down before the suspend.
Changeing the brightness will make it jump back down again.

---

