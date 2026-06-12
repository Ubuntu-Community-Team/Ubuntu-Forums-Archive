---
title: "Pavilion dv6-2150us HD sound video"
date: 2010-03-01
forum: Hardware
---

### Post by TusharG on 2010-03-01
I'm trying to install KUbuntu 9.10 on my new HP Pavilion dv6 2150us laptop that has i3 processor. I'm unable to hear any sound on the laptop and the display is limited to 1024x768 using the VESA driver. Any one has idea how to configure sound? Here is lspci output for reference.  

00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Arrandale Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
02:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)

---

### Post by unicorn6 on 2010-03-01
Follow this link i hope you w`ll get your answer.
[http://www.debianhelp.co.uk/sound.htm](http://www.debianhelp.co.uk/sound.htm)
__________________
[Oakland Politics:: Best Weight Loss Book]("http://www.social-bookmarking.net/bookmarks/oakland-politics-best-weight-loss-book/") | [Extratasty - All about training]("http://www.social-bookmarking.net/bookmarks/extratasty-all-about-training/")

---

### Post by TusharG on 2010-03-02
I booted with KUbuntu lucid alpha 3 live CD and to my surprise display was detected to 1366x768 the wireless card was not detected but when I scanned for new hardware I did find my broadcom card and I installed driver software which was installed directly from live CD [ Broadcom Corporation Device 4357 ]
Also when I booted I heard the Kubuntu login sound...  Sound card is also working. However installation script was crashing ) so i did not managed install KUbuntu. So I tried to boot directly into installation mode and that didnt work as well :(

The Good news is KUbuntu 10.4 will have support for my hardware out of the box.

---

