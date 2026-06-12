---
title: "Crackling sound on HDMI ATI HD7790"
date: 2014-10-13
forum: Hardware
---

### Post by lion_mp on 2014-10-13
[COLOR=#333333][FONT=UbuntuRegular]I am new on Linux but I try to start use, however this if my first big problem. On my card I am not able to use HDMI for sound. I have crackling sound. This is info about my hardware: 
1) By typing [/FONT][/COLOR]lspci[COLOR=#333333][FONT=UbuntuRegular] come out this information:
[/FONT][/COLOR]```
[FONT=Ubuntu Mono]00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)[/FONT]
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Bonaire XT [Radeon HD 7790/8770 / R9 260 OEM]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device aac0
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
[COLOR=#222222]04:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)[/COLOR]
```[FONT=UbuntuRegular]
[/FONT][FONT=UbuntuRegular]2) With the command [/FONT]cat /proc/asound/cards[FONT=UbuntuRegular]:
[/FONT]```
[COLOR=#222222]0 [PCH]:HDA-Intel - HDA Intel PCH[/COLOR]              HDA Intel PCH at 0xf0a10000 irq 45
 1 [Generic]: HDA-Intel - HD-Audio Generic
[COLOR=#222222]              HD-Audio Generic at 0xf0860000 irq 47[/COLOR]
```[FONT=UbuntuRegular]
[/FONT][FONT=UbuntuRegular]3) With the command [/FONT]aplay -l
```
[COLOR=#222222]karta 0: PCH [HDA Intel PCH], urz&#261;dzenie 0: ALC887-VD Analog [ALC887-VD Analog][/COLOR]  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 1: Generic [HD-Audio Generic], urz&#261;dzenie 3: HDMI 0 [HDMI 0]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 1: Generic [HD-Audio Generic], urz&#261;dzenie 7: HDMI 1 [HDMI 1]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 1: Generic [HD-Audio Generic], urz&#261;dzenie 8: HDMI 2 [HDMI 2]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 1: Generic [HD-Audio Generic], urz&#261;dzenie 9: HDMI 3 [HDMI 3]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 1: Generic [HD-Audio Generic], urz&#261;dzenie 10: HDMI 4 [HDMI 4]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 1: Generic [HD-Audio Generic], urz&#261;dzenie 11: HDMI 5 [HDMI 5]
  Urz&#261;dzenia podrz&#281;dne: 1/1
[COLOR=#222222]  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0[/COLOR]
```
[FONT=UbuntuRegular]I have already tested, but not solve problem:
```
[COLOR=#222222][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX="radeon.audio=1" in /etc/default/grub
[/FONT][/COLOR]
```
and
```
 load-module module-udev-detect tsched=0
``` 
Any idea what should I do?[/FONT]

---

### Post by Vladlenin5000 on 2014-10-13
Have you tried the proprietary ATI/AMD drivers for the graphics chip? The HDMI audio is controlled by that, you know...

---

### Post by lion_mp on 2014-10-14
Hi,
I used default and also tried binary driver from producer which where suggested in **Additional Drivers **[COLOR=#333333][FONT=Ubuntu]manager in Ubuntu.[/FONT][/COLOR]

Thanks,
Mariusz

---

### Post by lion_mp on 2014-10-18
Hi,
Is there anybody who could help me? I tried everythink I even updated my kernel to 3.16, installed latest proprietatary ATI drivers, but always the same. Crackling sound

Thanks,
Mariusz

---

### Post by Vladlenin5000 on 2014-10-18
So the symptom is the same with the open source driver or the proprietary one? If so, I'm starting to suspect there might be some hardware issue... Have you dome the usual troubleshooting already? Another HDMI cable, testing the same end device (TV/monitor or other) with a different HDMI source, etc.?

---

