---
title: "Pinnacle Pctv Stereo Problem"
date: 2008-06-21
forum: Hardware
---

### Post by Futureking on 2008-06-21
HI,

I have Pinnacle PCTV Stereo Card for watching tv. It works fine in Windows. In Linux it is detected. But I want to know that how to watch tv?
Skype detected a device Pinnacle pctv Stereo. Therefore I know it is detected. 
I tried. xine, tvtime, xawtv, mythtv. But failed. However one time mythtv showed some picture in poor quality without sound. mythtv is very hard to configure.

I just want a simple software that can recieve signals from pctv stereo card. I have Dish Tv on my home therefore my card recieves only 1 channel. To watch more channel I use my dishtv remote.

---

### Post by anandbabu20 on 2008-07-12
Could you please tell the specific model no of your tvtuner device.

It seems that most of the Pinnacle products are well supported in Linux. You may have to give the correct tuner no while loading the modules.

I own a Pinnacle PCTV USB2 works very well in tvtime.

---

### Post by Futureking on 2008-07-12
In the box of my tv tuner card only "Pinnacle PCTV Stereo" is given. It is an internal PCI card.
How to find its exact model number?

---

### Post by ljonesj on 2008-07-12
lspci should do it

---

### Post by Futureking on 2008-07-13
This is what I got from lspci command.

> ~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:02.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
01:03.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


---

