---
title: "Lenovo IdeaPad S10e WiFi problems"
date: 2011-06-07
forum: Hardware
---

### Post by borepstein on 2011-06-07
Hello all,

I've got this netbook. Installed Ubuntu 11.04 32-bit on it, all is good except the WiFi it seems. I just can not turn it on. When it is enabled in the BIOS the network manager says that it is disabled by the hardware switch. Working the switch seems to make no difference.

lspci lists the WiFi adapter as:
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Lenovo Device 30a1
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

Has anybody encountered this sort of problem? Any idea how to fix it?

Failing other options: what USB WiFi dongle would you recommend for use under Ubuntu?

Thanks.

Boris.

---

### Post by Lanser on 2011-06-07
borepstein. I have an S10-3 which did the same thing. Luckily it was in the first few days of owning the netbook and I was still running in dual boot WIN7/ Ubuntu mode.
 It seems that there is a Lenovo driver that links to the firmware for toggle on/off mode. 
By booting into WIN, I could toggle the wireless card back on, then reboot back into Linux with the wireless card running. 
After some experimenting, I worked out that the best way to enable / disable wireless was using the Linux connection manager, not the switch.

Does this turn leave the transmitter on and using power ? No sure. But it does not seem to change battery life so I have not bothered to dig deeper. 
Only annoyance is that I have not been able to fully purge the S10 of MS ( just in case )  

hope this helps

Lanser

---

