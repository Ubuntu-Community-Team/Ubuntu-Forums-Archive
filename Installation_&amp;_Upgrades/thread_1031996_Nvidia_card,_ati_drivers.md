---
title: "Nvidia card, ati drivers??"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by leutnant on 2009-01-05
I have a nvidia 6600 card and have the drivers installed for it; why is the update manager trying to hustle me into installing ati updates?

[[IMG]http://img390.imageshack.us/img390/7282/79997360mj4.th.png[/IMG]](http://img390.imageshack.us/my.php?image=79997360mj4.png)

---

### Post by Tim Sharitt on 2009-01-05
You shoud be able to uninstall the ati drivers without any adverse effects.

---

### Post by leutnant on 2009-01-05
yes, but why is it recommending that I install ati updates? It doesn't make sense :confused: :popcorn:

---

### Post by 2hot6ft2 on 2009-01-05
What do you get from ```
lspci
``` in a terminal?

---

### Post by leutnant on 2009-01-06
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
02:01.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

---

### Post by zika on 2009-01-06
> **leutnant said:**
> I have a nvidia 6600 card and have the drivers installed for it; why is the update manager trying to hustle me into installing ati updates?

for the same reason we from ATI side of the street get updates for nvidia ... ;) they get removed after some time as a slack but that is the ubuntu way of sharing and reconciling people ... ;)

---

### Post by Tim Sharitt on 2009-01-06
The reason you are getting the updates is simply because it is already installed by default and an update is available. There are probably several other drivers install which you don't need, but are installed by default.

I really should have been more clear, sorry.:)

---

### Post by leutnant on 2009-01-06
Phew! thanks for the explanation:)

---

