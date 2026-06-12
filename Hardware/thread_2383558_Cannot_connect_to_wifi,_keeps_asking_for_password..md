---
title: "Cannot connect to wifi, keeps asking for password."
date: 2018-01-26
forum: Hardware
---

### Post by Subcomfreak on 2018-01-26
Doing an install of XUbuntu 16.04 and for some reason the wifi does not work and it keeps asking me to supply  a password (it does not seem to get passed the authentication stage).  It can see all of the networks around me perfectly fine, but it cannot  connect to my router. I checked and the Ethernet works perfectly fine,  but I'd like to get the wifi running. 

here are the specs of the wireless chip, which is an on motherboard sort of ordeal:
```
Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
    Subsystem: ASUSTeK Computer Inc. BCM4360 802.11ac Wireless Network Adapter [1043:8659]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fb400000 (64-bit, non-prefetchable) [size=32K]
    Memory at fb200000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: bcma, wl
```

Things I have tried. Re installed the driver, tried the other older versions of the driver. I've most recently tried ndiswrapper, but for some reason it does not seem to be working correctly. Additionally, I have tried messing with the security settings on the router to no avail.

---

### Post by Autodave on 2018-01-26
I have a machine here that is temperamental about that.  Try this:  Make a LibreOffice file with your password in it. Copy ande paste the password from LOffice into the wifi when requested.

That is the only way I get my Dell to work. :-)

---

