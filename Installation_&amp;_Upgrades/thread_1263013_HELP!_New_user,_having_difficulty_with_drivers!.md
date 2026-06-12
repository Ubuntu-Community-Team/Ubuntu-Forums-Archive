---
title: "HELP! New user, having difficulty with drivers!"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by Dirty_Andres on 2009-09-10
Hello all, I'm running Ubuntu 9.04 on an acer travelmate 290, sound, wireless etc. works fine.
Having difficulty finding out where to get Nvidia Drivers for Ubuntu from. There are several packs on the repositories, but I've not found one that will support my card.

The graphics card I have is an intel 82852/855GM Integrated Graphics Device Rev.02,
I'm pretty certain that it's an nvidia driver, as the laptop had nvidia mobile installed when it was running windows.

I've searched the web for hours for any answers to my dilemma which is why I've posted here.


Any help appreciated.

---

### Post by wojox on 2009-09-10
Run this command in terminal and post back output:

```
lspci | grep -i nvidia
```

---

### Post by Dirty_Andres on 2009-09-10
Hey there mate, cheers for the quick reply, what turned up was the following, but I don't know what you meant by the "grep -i nvidia" part. 




[LEFT] > 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
01:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
andres@andres-laptop:~$ grep -i nvidia
[/LEFT]

---

### Post by Dirty_Andres on 2009-09-10
I've sussed out that my graphics processor is an intel 82852/855M type.

Unfortunately when I go to system - administration - hardware drivers, nothing turns up!

I don't know if there are any drivers available in the repositories, or if it's some kind of malfunction, but I would really like to find out what version of drivers I'm using and if possible update them, as the video playback is horrible when using youtube and full-screening. Video was ok under windows, I'd like to get it running just as well, if not better under ubuntu.

---

### Post by Mark Phelps on 2009-09-11
You have video drivers already installed for your Intel chipset or you wouldn't be getting any video at all.  The hardware drivers selection is for restricted drivers -- and there are none for Intel chipsets.

---

### Post by Dirty_Andres on 2009-09-12
Cheers mate, I had a feeling there might not have been any alternatives to the default ones.

Ah well, looks like I'm stuck with generic driver, unless I manage to find a way of fitting a new motherboard inside my travelmate 290 for cheap.......ha.


Thanks for the patience and advice folks.

---

