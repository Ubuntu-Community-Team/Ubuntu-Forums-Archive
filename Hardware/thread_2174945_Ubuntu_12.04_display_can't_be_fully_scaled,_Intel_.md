---
title: "Ubuntu 12.04 display can't be fully scaled, Intel Ivybridge Mobile graphic card"
date: 2013-09-16
forum: Hardware
---

### Post by vikko on 2013-09-16
Hi, I'm using a NUC running Ubuntu 12.04 connected to a Sharp LCD TV, the graphic card is Intel Ivybridge Mobile x86/MMX/SSE2.

The problem is the screen is not fully scaled, all the edges are covered by the LCD TV. I read some posts recommending to check the CCC which is not applicable to Intel one, adjust the display manager which I can't find in this system at the moment and therefore can't adjust the scales, and to fix overscan which I couldn't find the option in the TV. So anymore advices on this problem please? I feel so poor about this tricky issue. Thank you in advance!

---

### Post by bcschmerker on 2013-09-17
Which graphics processor is in your system?  I ran into the issue described this Thread on an eMachines®/Acer® EL1210-09 augmented with a Shuttle® PSU and an Asus® EN210/DI/512MD3(LP) (nVIDIA® GT218 GPU) driving the stock eMachines®/Acer® LE1987 display unit (a 1440x900px used as the primary display); I eventually needed the Packages nvidia-current and nvidia-settings to fix an overscan problem on an RCA® L26HD31R LCD televsion unit (mfd. by TTE Technology Inc.) fed from the GeForce® 8200 GPU integrated into the nVIDIA® MCP78S chipset as the secondary display.  Systems with ATi® GPU's with overscan problems would need the Packages fglrx and fglrx-amdcccle.  Don't know what Packages are needed for systems with GPU/DU-mismatch-induced overscan issues running the stock Intel® Multimedia Accelerator.

---

### Post by vikko on 2013-09-17
Thank you for the replay. Here is my graphic card information:

*-display
description: VGA compatible controller
product: 3rd Gen Core processor Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 09
width: 64 bits
clock: 33MHz
capabilities: msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:43 memory:f7800000-f7bffff memory:e0000000-efffffffioport:f000(size=64).

So you are suggesting to update the graphic card driver. Sorry that I'm still newbie to Linux...

---

### Post by bcschmerker on 2013-09-18
This is as I suspected.  I've little experience with Intel® GPU's without Microsoft® Windows® XP, 6.0 and 7.0, so am stumped on the required driver for controllability not in X.org.

---

### Post by bcschmerker on 2014-02-13
**Update:**  The [Ubuntu-X Team](https://launchpad.net/~ubuntu-x-swat) maintains a Repository at Launchpad™ for updated drivers for Intel® Media Accelerators™ both in the chipsets of pre-2nd-Generation-Core™ systems and on the CPU dies of the 3rd- and 4th-Generation Core™ Processors, programmable into APT as follows from the Terminal:
```
sudo add-apt-repository ppa:ubuntu-x-swat/intel-graphics-updates
sudo apt-get update

```The Ubuntu-X Team can answer any questions about driver Packages needful for particular Intel® Media Accelerator™ families.

---

