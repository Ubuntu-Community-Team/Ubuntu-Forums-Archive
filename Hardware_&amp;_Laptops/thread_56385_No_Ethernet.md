---
title: "No Ethernet"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by leaded on 2005-08-12
I just did a default Ubuntu install on a new Dell Dimension 5100C. Setup did not detect any network interfaces, even though the motherboard has giga ethernet. I finished the install anyway and tried to add the device manually. System -> Administration -> Networking only shows ppp0, and it's not configured. Looking at System -> Administration -> Device Manager doesn't really show me anything about an ethernet device.

My boss has the same computer and he's trying to get Fedora 4 running on it. He's having the same issue. Someone had him run /sbin/lspci, which I tried on Ubuntu but it doesn't exist. At any rate, we were able to get some useful information about our systems (since the Dell product page is horrible!).

```
# /sbin/lspci
00:00.0 Host bridge: Intel Corporation Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation PCI Express Graphics Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation Integrated Graphics Controller (rev 02)
00:1b.0 Class 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
03:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```

Does anyone know how I can get this ethernet device, the Intel 82801G, working? Is there a generic driver I can use in the meantime?

---

### Post by leaded on 2005-08-12
In our Fedora install, I tried modprobe e100 and e1000 and it didn't get me anything.

---

