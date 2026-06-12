---
title: "wifi very particular as to its working conditions"
date: 2012-06-02
forum: Hardware
---

### Post by sombreroDuck on 2012-06-02
I am having trouble getting wifi on my laptop, and I know the signal is allmost full here. First the internal card only seemed to work very intermittently (10% of the time), only after reboots, and irrespective if I did anything to the system or not. This suggested to me that it was a hardware problem (this is a ca 4 yr old laptop). The rest of the time the computer didn't even list it when I looked on the "lspci" or "rfkill" list. I've taken it out a couple of times and cleaned up the contacts and inside, but it made no difference. 

When I plugged in a borrowed PC-card wifi adapter it worked after a restart, but not after suspend, and not on battery power even if the battery is full. Following the suggestion in another thread I made the file in /etc/pm/config.d/ with "SUSPEND_MODULES="ath9k". Now it sometimes works after suspend, but only if plugged in during wakeup. I've also tried restarting the network manager but it didn't help. 

Currently the menu in the top-right is telling me I'm connected and that the "device is not ready" ?! I've tried looking around other threads, but have run out of ideas. Any suggestions at all would be welcome! Please!


Details: HP Pavillion tx2000, Ubuntu 12.04, the internal wifi is broadcom 4321, and the pc-card wifi is Atheros AR5418.

---

### Post by sombreroDuck on 2012-06-02
Update: My laptop has just detected BOTH the internal and pc-slot wifi adapters. For what it's worth, this is what lspci has to say about them:


01:00.0 Network controller: Atheros Communications Inc. AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express) (rev 01)
    Subsystem: D-Link System Inc Device 3a6f
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at c4000000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

03:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)
    Subsystem: Hewlett-Packard Company BCM4321 802.11a/b/g/n Wireless LAN Controller
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at c8000000 (64-bit, non-prefetchable) [size=16K]
    Memory at c9000000 (64-bit, prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

---

### Post by kai1 on 2012-07-24
How did you get 12.04 on your machine?
When I try running a live usb with 12.04(64bit) I get: a flashing cursor for a few seconds, the Ubuntu screen with the five dots changing between red and white, at some point a grey box in lower left corner(can't remember where this fits into the order) and finally a black screen.

---

