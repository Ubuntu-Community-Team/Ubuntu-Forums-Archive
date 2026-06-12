---
title: "No sound card detected in my AMD opteron"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by sastha on 2009-03-12
Hi

I tried to install ubuntu 8.04.2 on my AMD opteron dual core machine.

My problem is : Sound card is not detected

Let me furnish the detail i have collected

Mother board : Supermicro H8SSL-i

IMO,
this computer should have an in-built sound card

====

Result for "lspci"

00:01.0 PCI bridge: Broadcom BCM5785 [HT1000] PCI/PCI-X Bridge
00:02.0 Host bridge: Broadcom BCM5785 [HT1000] Legacy South Bridge
00:02.1 IDE interface: Broadcom BCM5785 [HT1000] IDE
00:02.2 ISA bridge: Broadcom BCM5785 [HT1000] LPC
00:03.0 USB Controller: Broadcom BCM5785 [HT1000] USB (rev 01)
00:03.1 USB Controller: Broadcom BCM5785 [HT1000] USB (rev 01)
00:03.2 USB Controller: Broadcom BCM5785 [HT1000] USB (rev 01)
00:05.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0d.0 PCI bridge: Broadcom BCM5785 [HT1000] PCI/PCI-X Bridge (rev b2)
01:0e.0 IDE interface: Broadcom BCM5785 [HT1000] SATA (PATA/IDE Mode)
01:0e.1 IDE interface: Broadcom BCM5785 [HT1000] SATA (PATA/IDE Mode)
02:03.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 10)
02:03.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 10)
==
Result for "aplay -l"
aplay: device_list:205: no sound cards found..

===

I am stuck and I do not know how to proceed from here.

your help is highly appreciated.

Thanks,
sastha

---

### Post by tmoble on 2009-03-12
Interesting, why do you think it has built-in sound card?  Did you check before you bought it?

see:  [http://www.supermicro.com/Aplus/motherboard/Opteron/HT1000/H8ssl-i.cfm]("http://www.supermicro.com/Aplus/motherboard/Opteron/HT1000/H8ssl-i.cfm")

Supermicro doesn't seem to think it has built-in sound hardware.

---

### Post by sastha on 2009-03-13
hmm...

Looking at the Multimedia provision in the front panel, I assumed that :(

Anyways via another post, I realized and fixed it.

Thanks man!

---

