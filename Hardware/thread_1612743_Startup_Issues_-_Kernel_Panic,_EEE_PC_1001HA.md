---
title: "Startup Issues - Kernel Panic, EEE PC 1001HA"
date: 2010-11-03
forum: Hardware
---

### Post by Joshun on 2010-11-03
Generally, I am very pleased with Ubuntu Linux on my Eee Pc. However, there is one very annoying issue. My eee occasionally freezes on boot (seems like a kernel panic), it usually does this once each day. Sometimes when it does this jumbled words suddenly appear on the screen and scroll up really fast, and then it freezes. I am really unsure what is causing is. Initially I thought it was an issue with the wifi card (ralink, rt3090), however changing the driver made no difference (i've tried rt2860sta, rt3090sta, rt2800pci, and ndiswrapper). Lspci gives:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe


```Please could someone help me with this.
Thanks for your support
Joshua

EDIT: This problem appears in Lucid, and still happens now that i've upgraded to Maverick. A fresh install makes no difference.

---

### Post by Joshun on 2010-11-08
I am trying the WICD Network Manager instead of ubuntu's default network manager to see if this resolves the problem.

---

### Post by cr0m on 2010-11-08
I'd like to help. I have the same laptop and have been running Lucid for about a week now, but haven't experienced this problem.

Here's what lspci gives me:

```

00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

```

Maybe we can compare systems and see if there are any significant differences. I'm running 10.4 (lucid) as I mentioned, with all updates applied, plus the Poulsbo drivers. I've also done both the tweaks mentioned for attempting to fix suspend problems mentioned here:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Tweaks](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Tweaks)

Let me know what other information I can provide that might help you out.

*edit:* Interesting. It looks like the Poulsbo drivers are handling a lot more on my machine than yours (if I'm interpreting the output from lspci correctly). Have you installed those drivers? Instructions are on the link above.

---

### Post by Joshun on 2010-11-09
Thanks very much for your reply, cr0m. I think you have a different laptop though (it sounds similar) because yours is 1101HA and mine is 1001HA. Yours uses an atheros wifi card and poulsbo graphics, mines express integrated graphics and uses a ralink card.

---

### Post by cr0m on 2010-11-09
Very sorry! I misread your model #. Hope you find someone who can help you out.

---

### Post by Joshun on 2010-11-20
After a lot of testing, it seems like the loading of the module (rt2860sta/rt2800pci) is causing the system to freeze, rather than the network-manager starting. Is anyone else experiencing freezes on an asus eeepc 1001ha?

---

### Post by cheyennemountain on 2010-12-30
Experiencing the same probems on my Asus eee 1015p. Looks exactly the same: kernel panic on loading the rt2800 driver.

lspci:

```
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
```

Using wicd wouldn't solve the problem. Actually wicd removes and loads driver modules on each connection startup, so the system freezes on every atempt to set up a connection.

---

### Post by Joshun on 2011-01-13
I have found sometimes you can use alt and sysrq (r, e, i, s, u, b) to reboot the system, but sometimes it locks up so much you can't:o

---

### Post by Joshun on 2011-01-15
I am now testing [this]("http://www.ramoonus.nl/2011/01/linux-kernel-2-6-37-installation-guide-for-ubuntu-linux/") kernel.

---

### Post by Joshun on 2011-01-16
Just upgraded my [bios]("http://support.asus.com/download/download.aspx") from 1201 to 1401 using the built in ezflash. It said that it would improve wifi so maybe it would affect this.

---

### Post by Joshun on 2011-01-16
Just upgraded my [bios]("http://support.asus.com/download/download.aspx") from 1203 to 1401 using the built in ezflash. It said that it would improve wifi so maybe it would affect this.

---

### Post by Joshun on 2011-02-16
After a LOT of testing, it appears wifi problems happen on Windows XP also - it has occasional times when it just doesn't connect8-[. My netbook must have a hardware fault or something, for it to happen on another operating system. What a stupid person I am in thinking this was ubuntu):P.

---

