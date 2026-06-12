---
title: "Dell Latitude D810 Occasional HANG during Boot"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by cassiuss on 2006-01-08
Hello all,
I'm using a Dell Latitude D810, 1.2Gb RAM, Built in wireless card and ndiswrapper to load the bcmwl5a driver for the wireless.

Occasionally, the boot sequence hangs completely when I boot at home without the docking station. When I try "recovery mode" I find the following messages:

ndiswrapper version 1.1 loaded (preempt-no,smp=no)
ndiswrapper: driver bcmwl5a (Broadcom,06/05/2004, 3.40.73.0) loaded
ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ5
ndiswrapper: using irq 5

And then it just stops. I rebooted tonight two times, and the second time the system came up.

lspci gives the following information on my wireless:

0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

and lshw -C network provides:
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: wlan0
       version: 03
       serial: 00:0b:7d:08:95:c8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper ip=192.168.2.101 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:fafec000-fafedfff irq:5

Any ideas what might be causing the frequent hangs at boot time? Could it be my WAP not responding somehow?

THANKS

Cassius

---

### Post by cassiuss on 2006-01-11
This is getting more annoying; I have not been able to boot the system on Ubuntu at home since I posted thie previous message. I am now travelling on a business trip, and can't boot Ubuntu in my hotel room either. 

NB - I can boot without problem at work, where 1) I use a docking station and 2) there is no wireless.

If anyone out there has seen this, please let me know. Booting and wireless under Window$ XP works fine.

Cassius

---

### Post by toorima on 2006-01-12
Don't know if it's the same problem but my inspiron 8600 would hang while booting before when on battery, change bios boot check to complete or thorough or something like that, bios takes 5 sec extra at boot but I can live with that
Hope it's any help

---

