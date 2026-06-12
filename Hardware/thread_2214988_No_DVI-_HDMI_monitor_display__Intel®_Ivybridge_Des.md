---
title: "No DVI- HDMI monitor display  Intel® Ivybridge Desktop graphics ubuntu 13.10"
date: 2014-04-04
forum: Hardware
---

### Post by pavlosant on 2014-04-04
I am trying to have two monitors connected to my DELL PC with Intel® Core™ i5-3470 CPU @ 3.20GHz × 4. My graphics card is Intel® Ivybridge Desktop. 
One monitor is connected with VGA and it works fine.
The other monitor is connected with DVI->HDMI and is not detected by UBUNTU 13.10.
I also have Windows 8 on my PC and both monitors work OK with Windows. But in Ubuntu I am having trouble. 
When I boot the PC the HDMI monitor displays the grub. When I select ubuntu then it goes to power safe mode and the VGA screen works only. 
I also tried booting with only the DVI->HDMI monitor connected but again after the grub screen it goes black to power safe mode.
I tried downloading the latest Intel drivers from links I found in other posts here at the forums but nothing worked yet. I have tried so many different things and I cannot remember to post them all here now.
I need both monitors to work as I use many programs and terminals for work on the same time and it will be  really useful for me to have both setup with ubuntu.
Can someone help me please?
If it is off help I give you the output of lspci and xrand. 


lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)





xrandr
VGA1 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)



Thank you.

---

