---
title: "No networks Available: Ethernet nor Wireless recognized || Ubuntu-Budgie 17.04 ||"
date: 2017-08-17
forum: Hardware
---

### Post by shistar12345 on 2017-08-17
Okay so I issued this problem a few days ago involving my ethernet connection issues and audio [Dummy output (null)]. 
Seemed they were both related as they both happened at the same time. But I am going to try and get one of these done at a time. 

To start off; For the last 12 hours I've been trying to find solutions based on my actual hardware and have tried many commands to no avail.

So this is what happened. I did my bi-yearly cleaning on my computer. So I took off certain connectors: CPU radiator, CPU fan, GPU PCI 8-pin adapter, 
HD audio (chasis) connectors, CPU 4-pin adapter. I also took out my GPU/VGA from the PCI-e x16 slot. Then after I cleaned everything, I put it all back together
and then turned on the computer. Once I made it to the desktop (budgie desktop with budgie 10.3) it seemed I had no Network Connections. At all. Also the audio
with that Dummy-output (null) device. [Though that is for another post].

Anyways, I tried a few fixes such as; Resetting the CMOS by taking the batter from the connector (it's a mini-itx board), Tried to fix broken packages from kernel
recover (might of been something in between was wrong, idk), Tried reverting to a slightly older version of the kernel (so I went from 4.10.0-32 to 4.10.0-30),
tried network manager restart. 

So after that didn't work, I ran commands:
lshw / lshw -c
ifconfig / ifconfig -a

--------
When I checked the Network Manager .conf file under /etc/NetworkManager , It seemed I did not have the 
eth0 in // #auto eth0 
It was instead // auto lo
with no mention of eth0 in the .conf file

--------
So I went back to lshw to check one more time and checked something.
*network UNCLAIMED

which I got twice, one for the ethernet and another for the wireless.
I am not quite network smart on linux (or in general, most of this was done by researching commands), so I may not quite understand what any of it really means.
But I am throwing this on here to see if this is part of an issue.
--------

Okay so here I am, found an article on very similar hardware to my (ethernet at this time) onboard LAN hardware.
[https://ubuntuforums.org/showthread.php?t=1022411](https://ubuntuforums.org/showthread.php?t=1022411)

For one, I did not make it past step 1. But I did use the second command in step 1 to hopefully help with my problem
(it is kind of an out of date post, so I was not sure if I should try to go through it all since step 1 was still hard to go through)
Second command in step 1:
sudo lspci -v

Showed a bunch of stuff, but based on my ethernet and wireless here is what I got:

```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
	Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet
	
Flags: bus master, fast devsel, latency 0, IRQ 11
	
I/O ports at d000 [size=256]
	
Memory at fe900000 (64-bit, non-prefetchable) [size=4K]
	
Memory at d0300000 (64-bit, prefetchable) [size=16K]
	
Capabilities: [40] Power Management version 3
	
Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
	
Capabilities: [70] Express Endpoint, MSI 01
	
Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
	
Capabilities: [d0] Vital Product Data
	
Capabilities: [100] Advanced Error Reporting
	
Capabilities: [140] Virtual Channel
	
Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00



04:00.0 Network controller: Intel Corporation Wireless 7260 (rev bb)
	
Subsystem: Intel Corporation Dual Band Wireless-AC 7260
	
Flags: fast devsel, IRQ 11
	
Memory at fe800000 (64-bit, non-prefetchable) [disabled] [size=8K]
	
Capabilities: [c8] Power Management version 3
	
Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
	
Capabilities: [40] Express Endpoint, MSI 00
	
Capabilities: [100] Advanced Error Reporting
	
Capabilities: [140] Device Serial Number 7c-5c-f8-ff-ff-50-6e-96	
Capabilities: [14c] Latency Tolerance Reporting
	
Capabilities: [154] Vendor Specific Information: ID=cafe Rev=1 Len=014 <?>
```

(this is not based on the terminal, it is in text mainly because I have zero access to the internet on my ubuntu atm, but this is how it was correctly formatted).

Anyways, this is about what I have right now for this. I really do appreciate any advice that could help me with this fix!

Just kind of stuck an unsure what to do mostly. 

And please ask for anything else, will try my best to get it :-)

-Sir Jesse-David

---

### Post by vasa1 on 2017-08-17
There's also [ Ubuntu-Budgie 17.04 Cannot recognize Wires/wireless nor any Audio devices]("https://ubuntuforums.org/showthread.php?t=2368815").

---

### Post by shistar12345 on 2017-08-17
> **vasa1 said:**
> There's also [ Ubuntu-Budgie 17.04 Cannot recognize Wires/wireless nor any Audio devices]("https://ubuntuforums.org/showthread.php?t=2368815").

That would be my post as well!

The forum Moderator suggested I make a post for each of the issues, hence why this one is for the Network atm :-)

-Sir Jesse-David

---

### Post by vasa1 on 2017-08-17
> **shistar12345 said:**
> That would be my post as well!

The forum Moderator suggested I make a post for each of the issues, hence why this one is for the Network atm :-)

-Sir Jesse-David

Great!

---

