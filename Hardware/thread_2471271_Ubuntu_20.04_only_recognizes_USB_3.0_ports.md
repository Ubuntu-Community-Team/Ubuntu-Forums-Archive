---
title: "Ubuntu 20.04 only recognizes USB 3.0 ports"
date: 2022-01-25
forum: Hardware
---

### Post by lukas34 on 2022-01-25
My USB devices are only found when plugged into one of my two USB 3.0 Ports. However when connected with one of my six USB 2.0 Ports they're not.
These ports get recognized with lsusb but don't chance status when something is connected to them:

{{{
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 003: ID 1532:0101 Razer USA, Ltd Copperhead Mouse
Bus 008 Device 004: ID 046d:081b Logitech, Inc. Webcam C310
Bus 008 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
}}}

When connecting a mass storage device to any of those faulty USB 2.0 ports, control lights on the device always flash for some seconds before going out.
The same problem existed with 18.04 already and didn't change its behavior.

I still got Windows as second boot system on my machine which recognizes any device on all USB ports. I also tested my test devices on another machine to rule them out as source of the error.

---

