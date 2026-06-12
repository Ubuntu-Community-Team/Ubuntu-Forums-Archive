---
title: "Can't Find Motherboard NIC (supported realtek chip set)"
date: 2013-07-19
forum: Hardware
---

### Post by edctexas on 2013-07-19
Originally, I tried the hardware in my box with Knoppix.  Knoppix finds all the NICs in the box (3 PCI, one motherboard).  Then I switched to Ubuntu 13.04.  The OS only finds the 3 PCI units.  I have googled the problem and tried loading several packages which find/report on hardware.  All of these approaches only seem to reveal info on the installed and "found" hardware.  I am fairly new to Ubuntu and was impressed with the way Knoppix and Ubuntu installed and run. Yes the motherboard NIC is enabled in the BIOS.  Is there a way to force discovery of hardware?  Is there a reason that discovery failed to find the NIC when Knoppix and Linux Mint 13 both found the MB NIC?

EDC

---

### Post by Yellow Pasque on 2013-07-19
The first thing is to make sure lspci recognizes it and see what kernel module (if any) is loaded:
```
lspci -v
```

---

### Post by edctexas on 2013-07-19
well that's interesting!  lspci -v now shows the MB NIC (realtek RTL-8139) with Kernel driver 8139too and NOW two of the PCI NICs, rather than the three PCI NICs.  The PCI cards are all Netgear with the RTL8169 chip.  It finds one on IRQ16 and the other on IRQ 16.  The MB is on IRQ9.

Previously lspci showed the three PCI card NICs and not the MB NIC.  any other ideas?

---

### Post by edctexas on 2013-07-19
Problem resolved. I sure appreciate the help!  I removed the PCI cards. Restarted the system.  Mother board NIC OK.  Then Shutdown and reinstalled the PCI NICs.  System now reports all 4 NICs.  This old machine will now bridge and route Braodband Hamnet and the two two subnets here at the house.  Tnx  EDC

---

