---
title: "Ubuntu with Fujitsu/Siemens Esprimo E5600 Desktop PC"
date: 2013-01-30
forum: Hardware
---

### Post by thanes on 2013-01-30
I can install Ubuntu 11.04 on this machine and upgrade it to 11.10. But when I try to use 12.04 or 12.10, with either Unity, Xbuntu, or even Lubuntu, the screen goes black after I choose to install or try the DVD, until I reboot the computer.

I would like to upgrade the computer at least to 12.04, but am scared of the screen not working. Is there a problem/bug/whatever that is keeping a later version of Ubuntu from working with this hardware? And is there a way to fix the bug, or a work around that would allow me to upgrade without problems?

It could be a lack of a SIS driver, but I and other's would need that driver on future DVDs to be able to try the distribution?

Below is a list of the computer's hardware specifics translated from German:

FSC Esprimo E5600 Desktop PC
Model: Esprimo
Series: E5600 Desktop Series
Processor
Type: AMD
Model: Sempron 3000 +
CPU Cores: 1
Speed: 1.8 GHz
Chipset / Motherboard
Chipset / Motherboard: Intel mPGA939
System board D2264
Memory Specification
Main memory
Inst.Speicher: 2x 512 MB
Currently available deals on memory upgrades you can order easily in our Afterbuy order processing. Please note the 2 RAM slots are already occupied.
e.g. 512MB / 333MHz / used from € 5, -
Type: DDR1
Memory limitation
max. Memory: 4 GB
Memory Bank Assignment: 2x 512MB occupied / free 2x
HDD
Type: IDE
Form Factor: 3.5 "
Memory Capacity: 40 GB
Currently available deals on larger hard drives (daily rates according to current availability) you can order easily in our Afterbuy checkout
HDD interface: P-ATA
Optical Drive
Drive type Internal: no optical drive
Currently available deals on drives, you can order easily in our Afterbuy checkout
e.g. DVD writer SATA / new from € 17.95
Interface: P-ATA or S-ATA possible
Graphics:
OnBoard: SiS 661FX graphics (shared memory max 32MB)
Connections: VGA in addition DVI Adapter (Low Profile)
Internal connectors:
Rack 5.25 "1x / ODD
Slot 3.5 "1x / HDD
Floppy 1x slot
IDE: 1x
SATA: 2x
PCIe 2x / 1x them x16 (low profile)
PCI: 2x (low profile)
DIMM: 4x (DDR1)
Connectors:
Network: 10/100/1000 onboard
Serial: 1x
Parallel: 1x
VGA: 1x
FireWire: No
USB Ports: 6x USB 2.0 (2x front)
Keyboard / Mouse 2 PS / 2 (mouse / keyboard)
Audio:
Chipset: AC97 Audio onboard
Speaker: onBoard
Audio Input: 1 x audio / 1x Mic
1x Audio Output ::
Keyboard / display unit:
Keyboard / mouse without
Currently available services for new keyboards / mice, you can order easily in our Afterbuy checkout
as USB keyboard and optical mouse black / new from € 9.95
Dimensions / Weight
Dimensions: approx 380 x 340 x 98 (depth / width / height)
Weight: (may vary depending on equipment) 8 kg
Operating System / Software
Operating system: no
Software: without
For more information
Upgrade: Current promotions for Aurüstoptionen see in our checkout.
Warranty: 12 months warranty second according to our terms and conditions for retail
14 days underwriting of merchant
Condition: Used
Good working condition with wear. Roughly cleaned.
Delivery / Notes: PC power cord included
Drivers can be found on the Support page of FSC and the component manufacturers. We can basically make any statements about the functionality with self-installation of operating systems, and ensure that current or updated vendor drivers verfübar.
According to the datasheet the FSC devices are compatible with Windows 98, 2000 and XP.
According to customer feedback and Internet reports, the device is designed for operation with various Linux distributions and with a few limitations (due to lack of graphics 3D graphics capability or lack of driver Sis) 7 for Windows Vista / Windows
A collection of links to drivers, Guides etc will be available on our me-side

---

### Post by PCNetSpec on 2013-01-30
Have you tried:-

**xforcevesa**

as a kernel boot parameter ?

---

### Post by oldfred on 2013-01-30
No idea how well it is suported. But if I run this it shows among many others:

dpkg -l|grep xserver-xorg-video
ii  xserver-xorg-video-sis                 1:0.10.3-3build2                        X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb              1:0.9.4-2build2                         X.Org X server -- SiS USB display driver

But full Ubuntu may not work or work well with that video system. Have you tried liveCD of Xubuutu  or Lubuntu?

       Xubuntu, a "lightweight" distribution based on the Xfce desktop environment or add LXDE desktop (is not lubuntu)
    
       Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box.

---

