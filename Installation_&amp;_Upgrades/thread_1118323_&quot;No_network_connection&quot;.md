---
title: "&quot;No network connection&quot;"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by cyberphrog on 2009-04-06
I recently replace the MOBO, processor, and graphics card (old ones got over-heated and I saw this as an opportunity to upgrade).  I reloaded Hardy (after having to adjust the boot options to replace "quiet splash" with "all_generic_ide").  Now that I have the basic OS installed, it's indicating that I have "No network connection" on the desktop GUI.  My machine in plugged into my Netgear router (via ethernet cable) with all the lights on.

HELP!!!  Any advice??  I ran "LSPCI" in terminal and this is what it shows:

00:00.0 Host bridge: Intel Corporation Edaglelake DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Eaglelake PCI Express Root Port (rev 03)
00:03.0 Communication controller: Intel Corporation Eaglelake HECI Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation Unknown device 10ce
00:1a.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation ICH10 HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation ICH10 PCI Express Port 1
00:1c.3 PCI bridge: Intel Corporation ICH10 PCI Express Port 4
00:1d.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation ICH10 LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation ICH10 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation ICH10 SMBus Controller
00:1f.5 IDE interface: Intel Corporation ICH10 2 port SATA IDE Controller
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0641 (rev a1)
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:06.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

---

### Post by cyberphrog on 2009-04-08
Problem fixed -- I upgraded to Intrepid.  The boot-up went off without a hitch and the on-board ethernet is working splendidly.  Perhaps the bios on the new mobo was too far ahead of Hardy?  I dunno.

Semper Phrogs

---

