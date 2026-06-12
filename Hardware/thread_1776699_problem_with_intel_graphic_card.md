---
title: "problem with intel graphic card"
date: 2011-06-06
forum: Hardware
---

### Post by evilheart on 2011-06-06
i have a built in video card , intel chipest 945GC , but it seems it doesn't work well on lububntu , or ubuntu generally , games doesn't work well , even   native linux games like supertux kart and warsaw. the issue is lag and changing fps , although my graphic card work well on winXp 
"of course using the driver on my motherboard built in chips drivers CD"

these are my pci info 


```
-PCI Devices-
Host bridge		: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
VGA compatible controller		: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
Audio device		: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
PCI bridge		: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
PCI bridge		: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01) (prog-if 00 [Normal decode])
USB Controller		: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
USB Controller		: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
USB Controller		: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
USB Controller		: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
USB Controller		: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
PCI bridge		: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
ISA bridge		: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
IDE interface		: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 80 [Master])
SMBus		: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
Ethernet controller		: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
Communication controller		: Rockwell International HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01)

```

is there any thing i can configure , or any tool that can fix

---

### Post by Zevaka on 2011-06-06
you say that games work okay in Windows with such card? It's integrated GPU, it's not supposed to run games, or any kind of heavy/3D applications

---

### Post by evilheart on 2011-06-06
> **Zevaka said:**
> you say that games work okay in Windows with such card? It's integrated GPU, it's not supposed to run games, or any kind of heavy/3D applications

well , it does ,not not for the newest games , but i can play generals zero hour , florensia "MMOrpg" , silkroad , unreal tournament 4 , counter strike condition zero with good performance.

it isn't perfect , but it isn't that useless also.

---

### Post by mastablasta on 2011-06-07
> **Zevaka said:**
> you say that games work okay in Windows with such card? It's integrated GPU, it's not supposed to run games, or any kind of heavy/3D applications
 
 
not true. this is only the case in older Intel chips.
 
problem here is this is an older chip. drivers are probably not that good in Linux. what you could do is try adding the Edgers PPA (btw what Ubuntu are you running?).
 
Also Intel just improved the drivers. but i am not sure hwo fast this update will come to Ubuntu.

---

