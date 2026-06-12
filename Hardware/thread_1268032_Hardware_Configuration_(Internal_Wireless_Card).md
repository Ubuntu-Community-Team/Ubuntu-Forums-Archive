---
title: "Hardware Configuration (Internal Wireless Card)"
date: 2009-09-16
forum: Hardware
---

### Post by gkapoor77 on 2009-09-16
Hi there,

I just picked up a 6-7 year old ASUS L3800 laptop from my in laws house. Wiped out the hard drive and I installed Ubuntu 9.04 (Jaunty Jackalope). I have no idea what configuration the laptop (Intel Processor, RAM, Harddrive etc.).

Most importantly I don't even know if the laptop has wireless internet capability (internal wireless card). I tried doing some physical search in the back of laptop and also looking into configuration of L3800 laptops but no luck. 

I also ran '**lspci -v | less**' and couldn't tell if wireless card exist or not and what kind? Could you please help me find out if I have a wireless card. Any commands or programs would be great!

---

### Post by gkapoor77 on 2009-09-16
Here's the output of lspci for your reference:

gkapoor77@Ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8 )
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8 )
02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller

---

