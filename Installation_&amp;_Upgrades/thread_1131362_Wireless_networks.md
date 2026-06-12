---
title: "Wireless networks"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by jose alberto on 2009-04-20
I am new at Ubuntu. Just downloaded v 8.10 and it does not detect wireless networks.

---

### Post by inobe on 2009-04-20
welcome Jose

i would suggest connecting hard wired to get all your system updates before anything else "very important"

get updates and when they are done reboot.

upon startup your wireless card should work, if not post some system information at that time.

go to applications> accessories> terminal.

type 

```
lspci
```

copy and paste the output on your next post, do this after the updates and your card still doesn't work.

---

### Post by jose alberto on 2009-04-21
Thanks !   I'll get back with the results

---

### Post by jose alberto on 2009-04-21
I downloaded and installed all upgrades, then restarted the pc, and still unable to detect wireless networks.

copied all info found in >accessories >terminal and its quite extensive... you want it all or something specific ?

---

### Post by RedSingularity on 2009-04-21
Sure post all of it.  It will allow us to see your wireless chip.

---

### Post by jose alberto on 2009-04-21
Following is what 'terminal' displayed:


00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by RedSingularity on 2009-04-21
Did you check System>Admin>Hardware Drivers?

---

### Post by jose alberto on 2009-04-22
Hardware drivers displayed:  Support for Atheros 802.11 wireless LAN cards
At the bottom of the window it shows: Driver is activated and currently in use.

Yet, no wireless conections are detected...

Frustrating...

---

### Post by niqmk on 2009-04-22
seems your driver has been detected.
use wifi-radar to see a ssid

---

