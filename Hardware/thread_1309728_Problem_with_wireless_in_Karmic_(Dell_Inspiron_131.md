---
title: "Problem with wireless in Karmic (Dell Inspiron 1318)"
date: 2009-11-01
forum: Hardware
---

### Post by ger_macaco on 2009-11-01
I was running Ubuntu 9.04 on my Dell Inspiron 1318 and all the hardware was working fine.

I did a clean install of Ubuntu 9.10 Karmic (x86) and now my wireless card is not recognized. There is no eth1 when doing ifconfig or iwconfig.

When running this command: lshw -C network I get a list of both cards, one with logical name eth0 (not wireless) and the other one without any logical name:

*-network
description: Network controller
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0c:00.0
version: 01
width: 64 bits
clock: 33 MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:17 memory:f1ffc000-f1ffffff

How can I solve this?
Many thanks

---

### Post by Opie2010 on 2009-11-01
I'm having the exact problem after my install of 9.10. I also have a Broadcom device and it refuses to be recognized now where as it worked in 9.04. The only difference is mine has a logical name after running the last command in the OP's post.
*-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:86:b9:06
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v3.04 ip=192.168.1.20 latency=0 multicast=yes
       resources: irq:30 memory:fe5f0000-fe5fffff
 [B] *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:4c:8c:f0:27
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg[/B]

---

### Post by ger_macaco on 2009-11-01
Seems that now Broadcom BCM43xx drivers are disabled by default and have to be activated manually (like NVIDIA).

Edit: This solved the issue

---

### Post by Opie2010 on 2009-11-01
How exactly did you do that?

---

### Post by Noble Hacker on 2009-11-01
I also had no wireless after upgrading from 9.04 to 9.10. (Dell 1520, Broadcom driver).
The solution for me was simple.
I went to System -> Administration -> Hardware Drivers, to check the list of proprietary drivers. My Nvidia accelerated graphics driver driver was activated by default. As for Broadcom STA wireless driver, it said "The driver is activated but is not currently in use".
All I had to do was just highlight Broadcom STA wireless driver line, click the button Remove, located below, wait untill the driver was unloaded, and then just activated it once again. That did the job and my wireless was enabled.
Hope this will help someone :D

---

### Post by Opie2010 on 2009-11-01
> **Noble Hacker said:**
> I also had no wireless after upgrading from 9.04 to 9.10. (Dell 1520, Broadcom driver).
The solution for me was simple.
I went to System -> Administration -> Hardware Drivers, to check the list of proprietary drivers. My Nvidia accelerated graphics driver driver was activated by default. As for Broadcom STA wireless driver, it said "The driver is activated but is not currently in use".
All I had to do was just highlight Broadcom STA wireless driver line, click the button Remove, located below, wait untill the driver was unloaded, and then just activated it once again. That did the job and my wireless was enabled.
Hope this will help someone :D
This what I did for 9.04. In 9.10 I don't even see any proprietary drivers when I navigate to >hardware drivers :S

Edit: Through some miracle I fixed this problem. Thanks for helping nubs like me :)

---

### Post by seoci on 2009-11-04
I'm having the same issue. What did you end up doing to fix it?

---

### Post by sergio jose dias on 2009-11-05
Go to link:
 [http://pelenegra.blogspot.com/2009/11/ubuntu-karmic-koala-solucao-do-bug-da.html](http://pelenegra.blogspot.com/2009/11/ubuntu-karmic-koala-solucao-do-bug-da.html)
And try that solution.

---

### Post by mnoyes on 2009-11-05
Me too -- "through some miracle" -- can you be a bit more specific?;)

---

### Post by the_maplebar on 2009-11-05
I had the same problem, Broadcom STA driver did not show up in the Hardware Drivers utility.  I figured out I could install it manually by installing the package

```
sudo apt-get install bcmwl-kernel-source
```

if you have a wired network connection this should work with no problem, also the package is available on the installation CD if you use that a an APT source

---

### Post by seoci on 2009-11-06
I ended up hooking my laptop up to my router and running an update. I installed this package as well, rebooted and my wireless works. I don't know and honestly don't care which fixed it for me right now, but one of the two got it.

Thanks for the help!

> **the_maplebar said:**
> I had the same problem, Broadcom STA driver did not show up in the Hardware Drivers utility.  I figured out I could install it manually by installing the package

```
sudo apt-get install bcmwl-kernel-source
```

if you have a wired network connection this should work with no problem, also the package is available on the installation CD if you use that a an APT source

---

### Post by kecker on 2009-11-30
How to install this package without a wired connection?

---

### Post by Marat Galiev on 2009-11-30
You can use windows drivers for you card.
Install ndiswrapper package, this solve my problems.

---

### Post by kecker on 2009-12-05
Best way to do that?

---

### Post by paradigm2 on 2009-12-08
> **the_maplebar said:**
> I had the same problem, Broadcom STA driver did not show up in the Hardware Drivers utility.  I figured out I could install it manually by installing the package

```
sudo apt-get install bcmwl-kernel-source
```

if you have a wired network connection this should work with no problem, also the package is available on the installation CD if you use that a an APT source

Thank you.  Doing the above on my 9.10 karmic install on a HP mini 110 1030NR solved my wireless issue.  Although I do notice some oddities like it not reconnecting automatically after going into Standby.  But it is at least usable again.  Thanks again for the information.

I guess while here: Does anyone happen to know if I will have to reinstall the source and recompile the modules each kernel upgrade or no?

---

### Post by tlcstat on 2009-12-10
Greetings,
this worked for me. Dell Inspiron B120 Dell 1390 Express Card 14e4:4311 Broadcom BCM4311. 

sudo apt-get install bcmwl-kernel-source

---

