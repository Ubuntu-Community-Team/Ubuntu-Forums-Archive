---
title: "Function F8"
date: 2009-10-23
forum: Hardware
---

### Post by del_fairley on 2009-10-23
Hi all,

I've been running Ubuntu on my old Inspiron 5150 laptop for a while now - and it's all good (big improvement over my previous XP/SuSE9 dual boot setup). However... today I tried connecting an external data projector for the first time, and found the Function-F8 key doesn't work - so couldn't switch to the external display. Is there a fix for this?
lspci output below:

djfairley@dels-laptop[djfairley] lspci                                [ 8:02PM]
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller

Running default nVidia driver:
djfairley@dels-laptop[djfairley] fgrep drivers/ /var/log/Xorg.0.log   [ 7:49PM]
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so

thanks in advance!

Del.

---

### Post by rwt911 on 2009-10-23
You may want to update you NVIDIA driver or the Kernel. NVIDIA driver download page can be found [here]("http://www.nvidia.com/Download/index.aspx?lang=en-us"), and precompiled Ubuntu kernels can be found [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/").

---

