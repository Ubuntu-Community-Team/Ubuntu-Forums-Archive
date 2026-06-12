---
title: "Will the NVIDIA 6150 proprietary driver be fixed for 16.04?"
date: 2016-04-24
forum: Hardware
---

### Post by sgian on 2016-04-24
I installed ubuntu gnome 16.04 64 bit and it worked fine as far as I could tell until I installed the proprietary driver for the GeForce 6150SE nForce 430 integrated graphics.  Then it would become unresponsive and then crash within half a minute of logging in.  I went into recovery mode and saw in the logs that the gdm was having trouble, and xorg was still being referenced.  So I got the regular Ubuntu 16.04 64 bit with Unity and reinstalled.  That didn't work either with the proprietary driver.  Since I bought this computer in 2010, is the driver support for these graphics going to be fixed?  It works fine in 14.04 with the proprietary driver, but I want to keep this computer past 2019 when 14.04 support ends, if it is still working.

Specs of this computer...
eMachines ET1331G-07W
AMD Athlon II 250u dual core
MCP61PM-GM Rev 2.4 motherboard
NVIDIA GeForce 6150SE nForce 430 integrated graphics
4 GB RAM

It used to have an old Radeon R5450 graphics card, but I took that out because AMD won't do proprietary drivers anymore for that card.  I hoped that NVIDIA would work fine.

---

### Post by $yl9pAR%t on 2016-04-24
I have all the problems you have described above with one exception, my GeForce 6150 did not work with Ubuntu 14.04 since May 2015, hence my ask. Could you tell me which xorg and kernel version you have on your working Ubuntu 14.04?

Or even better output of:

```
inxi -b
```

Thanks in advance.

---

### Post by sgian on 2016-04-24
Sorry, I should have mentioned that when I had a working 14.04, it was with a Radeon R5450 graphics card installed.  With the proprietary AMD driver and Oracle Java, my son played minecraft all he wanted on 14.04 without lag.  But not realizing that the NVIDIA 6150 integrated graphics is problematic, I took out the Radeon card in the hopes that I could get this computer to work on 16.04.  And the NVIDIA 6150 works for me in admin profiles without problem when the open source driver is being used.  It is just that the open source driver isn't good enough for my son's minecraft, and it does get a pattern on the screen and freeze when he tries to watch youtube on Chrome in a standard profile.  Here is the output for the current ubuntu gnome 16.04 with open source driver for the NVIDIA 6150 graphics...

```
System:    Host: emach-ubu16 Kernel: 4.4.0-21-generic x86_64 (64 bit)
           Desktop: Gnome 3.18.4 Distro: Ubuntu 16.04 xenial
Machine:   System: eMachines product: ET1331G
           Mobo: eMachines model: MCP61PM-GM
           Bios: AMI v: P01-A2 date: 12/10/2009
CPU:       Dual core AMD Athlon II X2 250u (-MCP-) speed/max: 1400/1600 MHz
Graphics:  Card: NVIDIA C61 [GeForce 6150SE nForce 430]
           Display Server: X.Org 1.18.3 driver: N/A
           Resolution: 1600x900@60.00hz
           GLX Renderer: Gallium 0.4 on NV4C GLX Version: 2.1 Mesa 11.2.0
Network:   Card: NVIDIA MCP61 Ethernet driver: forcedeth
Drives:    HDD Total Size: 640.1GB (5.5% used)
Info:      Processes: 213 Uptime: 14 min Memory: 1003.1/3699.9MB
           Client: Shell (bash) inxi: 2.2.35 

```

I had already ordered a NVIDIA GT 720 for another computer, I think I'll sell the old Radeon card on ebay or something and put the GT 720 into this computer instead so my son can play his minecraft.

---

### Post by $yl9pAR%t on 2016-04-24
I have forgotten to add, Xubuntu 16.04 works very well with GF 6150 and proprietary nvidia-304 driver, but of course if you prefer Unity or GNOME GF 720 is good choice.

---

