---
title: "LG LS70 Express PCMCIA/Network/Sound/Cardreader"
date: 2005-08-24
forum: Hardware &amp; Laptops
---

### Post by GizmoQ2k on 2005-08-24
Hi,

got an LG LS70 Espress Notebook. Got Ubuntu Installed, but had to blacklist the following modules to get ubuntu runnuning:

yenta_socket
pcmcia
sk98lin

**But now LAN and PCMCIA are not working**. I really dont care about PCMCIA cause i dont really need it, but LAN should be working, cause I dont like to carry my AccessPoint around =)
Anyone can help here?

**Another point is my soundcard:**
Its seems that its not detected by hotplug, so i guess there is a module missing. But as I am kind of new to linux, i dont know how to get this missing module.
Can someone tell me how?

**And the cardreader:**
No reaction when i insert a card.  :mad: 

Here is the output of lspci, if it helps:

[I]0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 3150
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 10)
0000:04:00.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:04:00.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
0000:04:00.3 Unknown mass storage controller: Texas Instruments PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-Layer Cont. an
0000:04:02.0 Network controller: Intel Corp.: Unknown device 4223 (rev 05)[/I]

Would make me very happy if someone could help.  :) 

greetings
Martin

---

