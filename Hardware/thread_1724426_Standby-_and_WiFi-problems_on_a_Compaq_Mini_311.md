---
title: "Standby- and WiFi-problems on a Compaq Mini 311"
date: 2011-04-08
forum: Hardware
---

### Post by Hinder on 2011-04-08
Hi,

I have been using Ubuntu 10.10 for a few months on my laptop, but I have one problem that's a little bit annoying: my standby-mode doesn't work. In this situation, my WiFi just works well. Sometimes my laptop won't even boot by the way, or it just freezes while working on it. This doesn't happen really often, but I think it's 5% of the total time.

My WiFi-specifications (WiFi working and connected):
> 
lshw
*-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: [...]
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.35-28-generic firmware=N/A ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:93000000-9300ffff My WiFi-specifications (WiFi not working):
> lshw
*-network UNCLAIMED
                description: Network controller
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:93000000-9300ffff
By the way, I run Ubuntu as a dualboot with pre-installed Windows 7. Everything, including standby and WiFi, works well on Windows 7.

Like I typed before, my WiFi works well with the default settings. It always did; just after the installation of Ubuntu it worked straight away. The standby-mode never worked really good. Sometimes it turns itself off if I close my laptop, and if I re-open it, it won't come back; all I see is a black screen with a white cursor. This is the same thing I see when my laptop won't even boot.

After some research, for example on this forum, I figured out that my standby-problem has something to do with my WiFi-drivers or -settings. I figured out that when I put '**hpet=force nolapic**' behind the default boot-lines in GRUB, the standby-mode works completely again. However, after this modification, my WiFi won't work anymore. I realize I change some really important settings with my modification, so can it be done in an other way, so my WiFi could still work?

I also get some errors, after the modification in GRUB, on my screen when I boot:

> 
[3.797531] Disabling IRQ #11
[26.110311] ath9k 0000:03:00.0: request_irq failed
Does anybody has a solution to this? Thanks a lot!

PS: If there are more logs required to solve this problem, I am willing to provide those.

---

