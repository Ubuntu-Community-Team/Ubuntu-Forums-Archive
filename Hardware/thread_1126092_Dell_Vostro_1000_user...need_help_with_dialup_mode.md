---
title: "Dell Vostro 1000 user...need help with dialup modem"
date: 2009-04-15
forum: Hardware
---

### Post by RangerReady23 on 2009-04-15
Hello all...I am an *extremely* new user of Ubuntu, and while I've managed to get most of my bugs and quirks worked out, I need some help desperately with one. My laptop, a Dell Vostro 1000, uses a fairly standard Conexant dial-up modem, which currently is my only option for connecting to the internet. Ubuntu, however...doesn't seem to have a clue that it's there. I've installed my service provider via WINE (since there isn't a native Ubuntu/Linux version), but I need to get the modem up and working so it can recognize it. Any help would be most appreciated.

---

### Post by MaindotC on 2009-04-15
I sincerely doubt the software you install in Wine will be able to use the modem.  First, let's see if Ubuntu detects the presence of your dial-up adapter.  If the dial-up adapter is integrated into the motherboard or a pci card, post the output of:
```

lspci

```
Please be sure the card is turned on in the BIOS.

---

### Post by RangerReady23 on 2009-04-15
lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)

---

### Post by MaindotC on 2009-04-15
You should see something like:
```

00:1f.6 Modem: Intel Corp. 82801DB AC'97 Modem Controller (rev 03)

```
Are you sure you have the modem turned on in the BIOS?

---

### Post by RangerReady23 on 2009-04-15
I entered my computer's setup screen when I started up the machine, so as to access the BIOS functions, and I didn't see an option for modem control, unless there's another method I'm not aware of (which is entirely possible).

---

### Post by MaindotC on 2009-04-15
You should have an option in your BIOS to enable or disable hardware controllers like the Ethernet controller, the wireless controller, and in this case the Modem controller.  Can you go through the all the menus in the BIOS and double check please?

---

### Post by RangerReady23 on 2009-04-17
Went there, looked at menus...no option, just as said before.

---

### Post by MaindotC on 2009-04-18
I don't think I can help you any further.  However, I did google "dell vostro 1000 ubuntu" and one of the results is the [Laptop Testing Team](https://wiki.ubuntu.com/LaptopTestingTeam/DellVostro1000?action=info).  Try contacting these users to see if they can help you with the modem issue.

---

