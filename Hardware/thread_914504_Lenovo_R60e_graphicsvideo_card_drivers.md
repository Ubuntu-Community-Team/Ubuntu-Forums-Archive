---
title: "Lenovo R60e graphics/video card drivers"
date: 2008-09-08
forum: Hardware
---

### Post by Machina987 on 2008-09-08
I have no idea how to install my video/graphic card driver on Ubuntu. If someone could please help me out it would be much appreciated.

---

### Post by cdaringe on 2008-09-08
well, lets start here.  what kind of graphics card do you have?

if you aren't sure, open up a terminal and type in
```

lspci

```

it will spit out a bunch of text.  you'll have to look for some sort of video or VGA line.  mine says:
"05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)"

**if you have an nvidia card**, i **personally** would install the proprietary video card driver.

```

sudo apt-get install nvidia-glx-new && nvidia-settings

```

restart your computer or restart X (i just do ctrl+alt+backspace...but i don't know if that the most graceful method)

```

sudo nvidia-settings

```

here you can configure your resolution and screens!

if you have an card or something else...somebody else?

---

### Post by Machina987 on 2008-09-09
This is what I got:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)

---

### Post by Machina987 on 2008-09-10
Is there no one who can help me with this issue?

---

