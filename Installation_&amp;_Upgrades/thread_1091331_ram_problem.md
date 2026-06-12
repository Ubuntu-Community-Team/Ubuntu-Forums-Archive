---
title: "ram problem"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by uttaran on 2009-03-09
i've ubuntu 8.10.Previously i had 256MB ram. So ubuntu didn't run. I've bought another 512MB ram but Ubuntu still doesn't open. it hangs after the welcome music plays. But it ran fine on a pc with 1GB ram. I'm very worried. Gutsy did run on my pc for 2 years. What to do??????????

---

### Post by albandy on 2009-03-09
I hope you're using the same kind of RAM, if latency or frequency are different can cause system hangs.
Try removing the 256MB module

---

### Post by uttaran on 2009-03-09
Both rams are exactly same...Xp runs fine. Still i did as u said..but it failed as well. the system hanged in the same area.

---

### Post by Neo_The_User on 2009-03-09
Define Ubuntu not running. Exact error output would be helpful.

---

### Post by Partyboi2 on 2009-03-09
> **uttaran said:**
> i've ubuntu 8.10.Previously i had 256MB ram. So ubuntu didn't run. I've bought another 512MB ram but Ubuntu still doesn't open. it hangs after the welcome music plays. But it ran fine on a pc with 1GB ram. I'm very worried. Gutsy did run on my pc for 2 years. What to do??????????
What graphics card are you using.?

---

### Post by Neo_The_User on 2009-03-09
> **Partyboi2 said:**
> What graphics card are you using.?

Yeah that info would be helpful as well.

---

### Post by uttaran on 2009-03-10
Well, the logon screen is appearing. then i put my user name and password and press enter. the music plays. then the screen becomes orange....that's it. there it stops and nothing more happens.
my  hardware configuration is

Processor
Model : Intel(R) Pentium(R) 4 CPU 2.26GHz
Speed : 2.27GHz
Cores per Processor : 1 Unit(s)
Threads per Core : 1 Unit(s)
Internal Data Cache : 8kB, Synchronous, Write-Thru, 4-way, 64 byte line size, 2 lines per sector
L2 On-board Cache : 512kB, ECC, Synchronous, ATC, 8-way, 64 byte line size, 2 lines per sector

System
System : KOBIAN PI845GLM
Mainboard : KOBIAN PI845GLM
Bus(es) : ISA PCI IMB USB
Multi-Processor (MP) Support : No
Multi-Processor Advanced PIC (APIC) : Yes
System BIOS : American Megatrends Inc. Version 07.00T
Total Memory : 768MB DDR

Chipset
Model : Intel 82845G/GL/GE Brookdale Host-Hub Interface Bridge (B1-step)
Front Side Bus Speed : 4x 133MHz (532MHz)
Total Memory : 768MB DDR
Shared Memory : 1MB
Memory Bus Speed : 2x 133MHz (266MHz)

Video System
Adapter : Intel(R) 82845G/GL/GE/PE/GV Graphics Controller (128MB DDR, 266MHz, PCI)

Storage Devices
ST3160215A 160GB (ATA100, 3.5", 2MB Cache) : 149GB (C:) (D:) (E:)
HL-DT-ST RW/DVD GCC-4522B (ATA33, DVD+-R, CD-RW, 2MB Cache) : N/A (G:)

Peripherals
LPC Hub Controller 1 : Intel 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
Audio Device : ECS C-Media AC'97 Audio Device
Audio Codec : 4D49h 0083h
Serial Port(s) : 1
Parallel Port(s) : 1
Disk Controller : Intel 82801DB/DBL (ICH4/ICH4-L) UltraATA/100 EIDE Controller
USB Controller 1 : Intel 82801DB/DBL USB UHCI Controller #1 (ICH4/ICH4-L B0 step)
USB Controller 2 : Intel 82801DB/DBL USB UHCI Controller #2 (ICH4/ICH4-L B0 step)
USB Controller 3 : Intel 82801DB/DBL USB UHCI Controller #3 (ICH4/ICH4-L B0 step)
USB Controller 4 : Intel 82801DB/DBL USB 2.0 EHCI Controller (ICH4/ICH4-L B0 step)

Printers and Faxes
Printer : HP Deskjet 3740 Series (USB, Colour)

Network Services
Network Adapter : Realtek RTL8139 Family PCI Fast Ethernet NIC - Packet Scheduler Miniport (Ethernet, 100Mbps)

I hope it'll b enough.by the way, can u tell me if my motherboard supports UltraDMA mode 5?if yes, how to activate it?

---

### Post by Partyboi2 on 2009-03-10
If you have upgraded to intrepid you may be having a conflict between compiz and your graphics card and need to remove the compiz packages to get to a working Desktop.
At the login screen press Ctrl+Alt+F2 and 
```
 sudo apt-get remove compiz compiz-core
```
Then press Ctrl+Alt+F7 or F8 to get back to a gui login screen.

---

### Post by uttaran on 2009-03-10
Thank u Very much....u just saved me from innumerable viruses!!!!!!!UBUNTU ROCKS

---

