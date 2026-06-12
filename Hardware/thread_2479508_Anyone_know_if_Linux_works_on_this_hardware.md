---
title: "Anyone know if Linux works on this hardware?"
date: 2022-09-27
forum: Hardware
---

### Post by maglin2 on 2022-09-27
I'm buying an All-in-One PC with the following key components:

CPU Intel i5 Six Core Processor i5-11400 (2.6GHz)
Motherboard ASUS® H510T2 (Intel Chipset)
Network Card GIGABIT LAN & WIRELESS INTEL® Wi-Fi 6 AX200 (2.4 Gbps) + BT 5.0

Any advice on any of them known to work OK with Ubuntu would be much appreciated.
I hope to install Ubuntu (or at least Linux), but if it won't work I'll have to fall back on installing Windows.
Thanks
Dave

---

### Post by QIII on 2022-09-27
It is nigh impossible to say with 100% confidence that Brand X's Model Y will work without any hitch.

However, it is generally the case that Intel products are well supported by Linux.  The only misgiving I might possibly have is that the 11xxx products are pretty new.  It sometimes take a bit of time for the developers to catch up to new hardware.  But Intel's generations are usually evolutionary and not revolutionary.  

As an aside, it would be best to ask if "Linux supports (or works on) this hardware."  Hardware is not typically designed to "work with Linux".

---

### Post by #&amp;thj^% on 2022-09-27
> **maglin2 said:**
> I'm buying an All-in-One PC with the following key components:

CPU Intel i5 Six Core Processor i5-11400 (2.6GHz)
Motherboard ASUS® H510T2 (Intel Chipset)
Network Card GIGABIT LAN & WIRELESS INTEL® Wi-Fi 6 AX200 (2.4 Gbps) + BT 5.0

Any advice on any of them known to work OK with Ubuntu would be much appreciated.
I hope to install Ubuntu (or at least Linux), but if it won't work I'll have to fall back on installing Windows.
Thanks
Dave
This will be the only problem, and really not much of problem with kernels 5.15 and up. >>> "**GIGABIT LAN & WIRELESS INTEL® Wi-Fi 6 AX200 (2.4 Gbps) + BT 5.0"**
```
inxi -Nz
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169
  Device-2: Intel Wi-Fi 6 AX200 driver: iwlwifi

```
Bluetooth:
```
inxi -Ez
Bluetooth:
  Device-1: Intel AX200 Bluetooth type: USB driver: btusb
  Report: rfkill ID: hci0 state: up address: see --recommends

```

> **QIII said:**
> It is nigh impossible to say with 100% confidence that Brand X's Model Y will work without any hitch.

However, it is generally the case that Intel products are well supported by Linux.  The only misgiving I might possibly have is that the 11xxx products are pretty new.  It sometimes take a bit of time for the developers to catch up to new hardware.  **_But Intel's generations are usually evolutionary and not revolutionary.  _**

As an aside, it would be best to ask if "Linux supports (or works on) this hardware."  Hardware is not typically designed to "work with Linux".

+1

---

### Post by maglin2 on 2022-09-27
Thanks very much both.
I turn Bluetooth off anyway.
If the good Lord spares me to order another desktop PC (12 years since last one) I'll try to remember the advice on phrasing the question!
Dave

---

### Post by maglin2 on 2022-10-06
Preferred processor was out of stock. Spec is now:
CPU Intel® Core&#8482; i3-10100    3.60GHz
Motherboard ASUS® H510T2 Intel® H510 Chipset Intel 
Integrated Graphics Processor
Network Card GIGABIT LAN & WIRELESS INTEL® Wi-Fi 6 AX200 (2.4 Gbps) + BT 5.0

Attempting to boot Ubuntu 22.04 from liveusb gives a black screen after initial choice screen for Ubuntu/Safe Graphics etc
I can hear the Try Ubuntu/ Install Ubuntu screen jingle though, so there seems to be a graphics/display driver issue I suspect.
Booting liveusb to safe graphics mode works (with the usual odd safe graphics display).
Is it worth trying to install alongside Windows to see if it then installs correctly with suitable graphics driver? Anything else I can try to get display working properly with liveusb first?
I'm very much a novice with this stuff. Ubuntu has just worked on every other machine I've tried it with!
As a consequence I know nothing about Windows either, and would hate to have to try to learn now!
Any help much appreciated.
Thanks
Dave

---

