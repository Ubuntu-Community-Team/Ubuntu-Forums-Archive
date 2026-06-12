---
title: "Problems with lcd screen brightness"
date: 2011-05-23
forum: Hardware
---

### Post by claracc on 2011-05-23
Hallo,

I have installed ubuntu 10.04.02 on an old laptop ( 1997 bios, 1GHz CPU pentium III, 512 MB ram from which, 64 MB go for the sis 630 vga card, 20 GB HD), and it works very well, keeping in mind the old hardware of the laptop).

I only have two problems:

I cannot reduce the brightness of the screen, it is in its maximum. I have tried adding to panel the mini brightness app, it doesn work, it says it is not possible to obtain the brightness from laptop's panel. I tried with gconf-editor in gnome-power-manager --> backlight and set ac_brightness to 60 or 50 but brightness is the same. I have tried using setpci command, no success, running xbacklight neither.

I have two keyboard keys to increase and decrease brightness Fn F10 and Fn F9, and they work, but the range to reduce brightness is very small (too bright yet). Originally this laptop came with windows millenium, then it had xp, and the screen brightness was smaller than now, it didn't damage the eyes.

The other problem is that when I put to sleep laptop with the Fn Esc key, laptop sleep but when resume, I have to change the hour becuase it stays in the hour it went to sleep.

I think this problems are related with acpi or apm software to communicate with the bios, but I don know how to solve the problems. 

lspci command gives:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 630 Host (rev 31)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 82)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
00:01.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:0a.0 CardBus bridge: Texas Instruments PCI4410 PC card Cardbus Controller (rev 02)
00:0a.1 FireWire (IEEE 1394): Texas Instruments PCI4410 FireWire Controller (rev 02)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 31)

And this is part of Xorg.o.log which I think could be relevant for brightness problem:

VideoRAM: 65536 KB
(II) SIS(0): Using 12288K of framebuffer memory at offset 0K
(--) SIS(0): Hardware supports two video overlays
(--) SIS(0): Detected LVDS transmitter (External chip ID 4)
(--) SIS(0): Detected Chrontel 7005 TV encoder (ID 0x3a; chip ID 4)
(--) SIS(0): Chrontel: No TV detected.
(--) SIS(0): No CRT1/VGA detected
(--) SIS(0): Detected LCD/plasma panel (1024x768, 12, non-exp., RGB18 [c2e9ff])
(==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SIS(0): CRT1 gamma correction is enabled
(--) SIS(0): CRT2 gamma correction not supported by hardware
(--) SIS(0): Memory bandwidth at 32 bpp is 267.268 MHz
(--) SIS(0): Detected LCD PanelDelayCompensation 0x04
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"

Perhaps I have to load certain specific modules to control brightness and suspension ?

Thank you very much in advance, any help is very welcome.

---

### Post by claracc on 2011-05-25
Bump?

About brightness problem, I have tried to add in grub2 the acpi=force option, also I have tried to load the video module: sudo modprobe video, since there is the module video.ko available, but in spite of this, under /proc/acpi/video there isn't anything as /VGA/LCD/brightness where to put the brightness values.

Other thing I don't understand is why setpci command does nothing, i.e.: sudo setpci -s 01:00.0 f4.b=1f and screen brightness continues at 100%.

It could be related to the xorg-driver-sis I am using?, I should try with other video driver for sis?.

---

