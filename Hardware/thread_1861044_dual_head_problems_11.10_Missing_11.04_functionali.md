---
title: "dual head problems 11.10 Missing 11.04 functionality"
date: 2011-10-15
forum: Hardware
---

### Post by Neill_R on 2011-10-15
Hi

Firstly there does not seem to be the functionality in 11.10 that was there in 11.04. namely in recovery console mode one can no-longer boot into low graphics mode it is no longer an option from the menu. Why was it removed?

                                                       ========================================

Okay i have a packard bell i-media 1328/1 PC with a S3 PCI card fitted with the bios mode switch AGP/PCI set to PCI I can in Windows XP pro SP3 run a dual head PC with the desktop extended across the tow monitors in 1048 780 resolution. DELL 17" llyamo ProLite E383S.

However with UBUNTU i must be in BIOS AGP mode and then the motherboard PCI card will work otherwise in PCI mode I must use low resolution graphics mode. 

Can you help me  or advise me as to what i can do to get it working please (in PCI BIOS setting DUAL HEAD)

Do I need this driver installed 
[https://launchpad.net/ubuntu/lucid/+source/xserver-xorg-video-s3/1:0.6.3-1](https://launchpad.net/ubuntu/lucid/+source/xserver-xorg-video-s3/1:0.6.3-1) 

following  [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)  

neill@Charles-Ubuntu:~$ lspci | grep VGA
00:0b.0 VGA compatible controller:S3 Inc. 86c968 [Vision 968 VRAM] rev 0
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
neill@Charles-Ubuntu:~$ 

and

sudo lshw -C video  (give this in either BIOS setting)

*-display UNCLAIMED
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:c8000000-cfffffff memory:db000000-db01ffff ioport:a000(size=128)
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 86c968 [Vision 968 VRAM] rev 0
       vendor: S3 Inc.
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller
       configuration: latency=0
       resources: memory:80000000-83ffffff memory:84020000-8402ffff

---

