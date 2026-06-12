---
title: "Geforce 4 Ti 4600 + SBA = no go"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by stevend1038 on 2007-05-27
This problem has been annoying the crap out of me and I've looked all over for a solution but I must be blind cause I can not find it. Anyway when I try to enable FastWrite and SBA on my AGP card it, it works, but not really, only fast write gets enabled and SBA just hard locks X.

> steven@steven-desktop:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Enabled
SBA:             Disabled


> steven@steven-desktop:~$ cat /proc/driver/nvidia/agp/card
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x 
Registers:       0x1f000217:0x1f000114


> steven@steven-desktop:~$ cat /proc/driver/nvidia/agp/host-bridge
Host Bridge:     PCI device 1039:0746
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       4x 2x 1x 
Registers:       0x1f000217:0x00000114



Its strange because I know a week ago I had ubuntu installed and enabled SBA and FW, and it worked just fine. I'm pretty stumped, maybe they are new nvidia drivers that are screwing me over?

btw, its nvidia driver: 1.0-9631

---

