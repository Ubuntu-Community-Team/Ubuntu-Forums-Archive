---
title: "Connect to a WPA 2 AP with NO GUI"
date: 2011-08-19
forum: Hardware
---

### Post by Mars11 on 2011-08-19
I'm currently running Ubuntu without a GUI and I need to connect to a wireless network to install one. I would connect using Ethernet, but my computer doesn't have an ethernet port.

---

### Post by Ozymandias_117 on 2011-08-19
Don't know if this will help you, but you can try it.  It's in the Arch Linux guide: [Wireless]("https://wiki.archlinux.org/index.php/Beginners'_Guide#Setup_wireless_in_the_live_environment_.28optional.29")

---

### Post by Mars11 on 2011-08-19
It's just like all the other guides, but I still can't connect.

---

### Post by hsoulen on 2011-08-19
Hello!

iwconfig is pretty much the way to go, but if you have already tried it with no luck maybe your wireless card is not being recognized?

What is your output of:

```
lspci
```

Or if the adapter is USB:

```
lsusb
```

[http://linux.about.com/od/commands/l/blcmdl8_iwconfi.htm]("http://linux.about.com/od/commands/l/blcmdl8_iwconfi.htm")

Cheers,

Hank

---

### Post by Mars11 on 2011-08-19
The output of ```
lspci
``` is ```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```Or if you guys know how I could run ```
sudo apt-get install gnome-shell
``` using a Live CD and have it take affect on the SSD's installation.

---

### Post by Mars11 on 2011-08-19
I just found a USB adapter.

---

