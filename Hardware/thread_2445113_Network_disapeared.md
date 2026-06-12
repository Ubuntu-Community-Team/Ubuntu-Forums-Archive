---
title: "Network disapeared"
date: 2020-06-09
forum: Hardware
---

### Post by jdauphinais on 2020-06-09
[COLOR=#242729][FONT=Arial]I am using Ubuntu 20.04 64bit in a VM in VMWare Workstation 15 player.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]It was working fine but I had an improper shutdown and since then, I launched the VM and the network has disappeared from the top right. If I do a sudo lshw -c net, I get:
[/FONT][/COLOR]
*-network DISABLED        
   description: Ethernet interface
   product: 82545EM Gigabit Ethernet Controller (Copper)
   vendor: Intel Corporation
   physical id: 1
   bus info: pci@0000:02:01.0
   logical name: ens33
   version: 01
   serial: 00:0c:29:3b:ce:ce
   capacity: 1Gbit/s
   width: 64 bits
   clock: 66MHz
   capabilities: pm pcix bus_master cap_list rom ethernet physical logical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI latency=0 link=no mingnt=255 multicast=yes port=twisted pair
   resources: irq:19 memory:fd520000-fd53ffff memory:fd500000-fd50ffff ioport:2000(size=8) memory:fd540000-fd54ffff

[COLOR=#242729][FONT=Arial]In VMWare, I can see that the network is active.[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-06-09
Welcome.

Please check the virtualization software settings. Re-enable networking if necessary.

---

### Post by jdauphinais on 2020-06-09
But I have another ubuntu image and the other one is working fine...

---

### Post by CelticWarrior on 2020-06-09
> **jdauphinais said:**
> But I have another ubuntu image and the other one is working fine...

This doesn't mean much. Settings are per VM.

---

### Post by jdauphinais on 2020-06-09
but I didn't change any settings, it happened right after an improper shutdown of the pc :(

---

### Post by CelticWarrior on 2020-06-09
Yes, it was stated in your first post: *It was working fine but I had an improper shutdown* (...) and yes, even an improper shutdown shouldn't have changed the settings but it could. Also "shutdown" needs some explanation. Was it in the Ubuntu VM or the host?

This is what we know so far: *network DISABLED.* In bare metal this usually means the device is disabled ion BIOS/UEFI. In a VM this *usually* means disabled in that VM's settings, reason why I repeatedly asked you to check it. If still correctly enabled the troubleshooting proceeds from there but that MUST be checked before anything else.

---

