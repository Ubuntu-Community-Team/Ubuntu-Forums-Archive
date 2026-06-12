---
title: "Bad graphics Intel i5"
date: 2011-10-13
forum: Hardware
---

### Post by xtremesupremacy3 on 2011-10-13
Hey, 
I bought a new laptop, a Gateway.
Anyway, when I installed Ubuntu 11.10 on it all worked straight out of the box (or so I thought), Unity 3D fired up, and all looked nice.

But then I noticed that my Fn button for brightness levels didn't work as they should. The notification shows they work but no change happens to the brightness even though the notifier says it should be.

That wasn't too big an issue until I tried playing 0AD...wow it's laggy.
I tried other games and they are all extremely slow and pretty much unplayable. Now I'm thinking it's to do with my integrated graphics card, so here is what I have:

Processor: Intel® Core™ i5 CPU M 450 @ 2.40GHz × 4
Graphics Card: Intel® Ironlake Mobile x86/MMX/SSE2 
RAM: 3GB

Here is the output of lspci regarding the VGA:

```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
```

Anyone have any idea on what to do?

Thanks

---

### Post by xtremesupremacy3 on 2011-10-13
Ok so I turned of Vsync and it made some improvement to the lag of the game...although it's still slow.

---

### Post by xtremesupremacy3 on 2011-10-16
Nobody at all?

I'm running the i915 driver in case that helps.
I should have said that earlier, sorry

Arthur

---

### Post by xtremesupremacy3 on 2011-10-16
Well I'm going to mark this as solved. After trying some native 3D games (eg Tremulous) it runs very smooth, but seems it's mostly wine games. So therefore problem solved, as for the brightness issue that's quite trivial I assume.

---

### Post by nullus on 2012-11-10
Actually having the same problems with intel i5 HD 3400 graphics on Ubuntu 12.04.

I can't change screen brightness and game performance is sluggish.
Did you ever find a fix for this?

Not sure if these two are related, but if my screen turns off (as in lock or hibernate), it can't be turned back on, and my vga port output seems non-existent.

I have hunch that these are all related to mismatched and bad intel HD drivers, but haven't figured out which drivers I need exactly.

---

### Post by xtremesupremacy3 on 2012-11-10
Hello,

Well, most of the graphics issues are resolved for me.
The newest version of 0ad has fixed my earlier issues and allows me to play smoothly for at least half an hour, after that it begins to get sluggish. I suspect that has to do with perhaps a memory leak within the game rather than the graphics card.

I do not have any issues with hibernation however, when my computer turns off after inactivity, it can be switched on again without issues. So I am not too sure whether they are related.

As for the brightness controls, these are still not fixed, and whenever I need to adjust Gamma settings (Amnesia for example) this will not work.

But out of curiousity, what are your specs?

---

### Post by nullus on 2012-11-17
What spec exactly were you looking for? I have an HP Pavillion dm4.

My lspci:

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
```

---

