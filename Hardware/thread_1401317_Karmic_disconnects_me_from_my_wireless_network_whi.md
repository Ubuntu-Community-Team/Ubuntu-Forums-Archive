---
title: "Karmic disconnects me from my wireless network while Jaunty does not."
date: 2010-02-07
forum: Hardware
---

### Post by Kodiak Bear on 2010-02-07
Here is my wireless info, via lshw...

```
description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wmaster0
                version: 01
                serial: 00:24:2b:d7:7e:b0
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.1.101 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
```I got Karmic and the connection would drop unexpectedly (even when updating!) The only way to get back online would be restarting my laptop.

Is there any way to fix this problem? I just find it odd because Jaunty works perfectly and doesn't drop my connection. I really want to upgrade.

---

### Post by Kodiak Bear on 2010-02-08
Bump.

---

### Post by Enigmapond on 2010-02-08
I had the same problem so I installed wicd as my network manager and it has worked flawlessly.

---

### Post by dmalizia on 2010-03-09
I had the same problem on a Toshiba A300. No problem with 8.10, virtually no wireless with 9.10 
looking at /var/log/daemon.log I realized that NetworkManager was logging the disconnection immediately after an error by wpa_supplicant. 
In the same log on 8.10 there was no sign of wpa_supplicant (which I don't even think I had installed). Apparently they do not behave well together and they both get installed by default. The problem must also be related to the network card because on a second toshiba laptop I had no trouble at all. 
I first thought about removing wpa_supplicant but this will remove also NetworkManager so I did the opposite and removed only NetworkManager. I configured the wpa_supplicant (there are various guides on how-to around the net) and the wirelss started working fine. I lost the nm-applet but I found a nice application which will do something similar called wpa_gui. It does only configure wireless connections but this is fine for me.

---

### Post by newmark42 on 2010-04-21
So I've been having this problem for a while and it's been getting worse, as I always install the latest patches available in the main patch line.  Here's what I've found: 
 
1. If you have the problem connecting to a linksys router running linksys firmware, and you install DD-WRT on the router instead, it usually fixes the problem (have done this with 3 linksys routers)
 
2. The problem on my laptop has become worse over time. I installed karmic almost immediately upon release.  It had misc drops in the past but it's gotten FAR worse.  Today, after some update yesterday, I can't keep a connection on one of my networks for more than 5 minutes, despite reboots, hard boots, etc.  (After that same update, my audio is foobar - unmutes itself everytime the system wants to make sound... and those  noises are WHY I HAD IT MUTED) 
 
3. when I was running network-manager, I could ifconfig eth1 down (eth1 is my wireless) and then ifconfig eth1 up and avoid the "cant connect loop of death until you reboot the machine" issue that others have noted.
 
4. I switched the WPA to use AES instead of TKIP, as was recommended some places, to no avail.
 
5. I switched over to wicd upon recommendation from others in other places, same exact problem.
 
6. I rebooted and booted to an ancient kernel that was still available.  Gnome is VERY angry (no mouse in Gnome is annoying!), but guess what -- Wireless is PERFECT.  No issues, no drops, no nothing.
 
So, with no real differences other than the kernel between reboots, after fighting this issue for about 4 hours today, I am satisfied with the answer I've seen elsewhere.  
 
The kernel is broken.  
 
And unless someone hacked the package repositories, I'd say it's all on Linux's side.  
 
After some additional research, it appears that this problem is not unique to Ubuntu, or to any particular network card.  I've seen Broadcom (mine uses BC43 driver), Intel, Atheros, etc. all having the same problems.  
 
Meanwhile, my linux laptop is useless - unless I'm somewhere with a router with dd-wrt.  And after the beating I gave it today, I'm not even sure that will work anymore.

---

### Post by newmark42 on 2010-04-21
PS. Version of kernel with no problem was 2.6.28-17. My kernel is 2.6.31-20.  I notice that Linux kernel is up to 2.6.33.2.  I have to wonder if the problem is resolved in later kernels.

---

