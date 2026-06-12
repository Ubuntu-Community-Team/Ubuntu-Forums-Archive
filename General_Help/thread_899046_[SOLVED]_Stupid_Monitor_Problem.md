---
title: "[SOLVED] Stupid Monitor Problem"
date: 2008-08-23
forum: General Help
---

### Post by acrousey on 2008-08-23
My monitor is not listed in "sudo gksu displayconfig-gtk". It's a really old monitor. I think the best idea would be to just get a new one, but while I have it, I think I should use it. It is a PACOM model # 4Fe and it was manufactured in 1995. That's all I know about the monitor. I have no documents as it was given to me by a friend a few years back. 

The problem that I keep having is that the Plug'n'Play option only allows a "high" screen resolution of 800x600. I know that it can go higher than that, but I'm having trouble with getting it fixed like that again. It will either be perfect working within the main part with the login/splash screen either being too big (so large it can't be centered on screen) or it will flicker. 

Is there a quick fix I can do? Could I just choose another option within "sudo gksu displayconfig-gtk" that would be an equivalent to my monitor? Or could I manually fix the monitor problem with "sudo nano /etc/X11/xorg.conf"? The only problem with the xorg.conf option is that I don't know the hsync or vsync of this monitor. I know I'm asking for a lot, but I would gladly accept any help. Thanks!

---

### Post by overdrank on 2008-08-24
> **acrousey said:**
> My monitor is not listed in "sudo gksu displayconfig-gtk". It's a really old monitor. I think the best idea would be to just get a new one, but while I have it, I think I should use it. It is a PACOM model # 4Fe and it was manufactured in 1995. That's all I know about the monitor. I have no documents as it was given to me by a friend a few years back. 

The problem that I keep having is that the Plug'n'Play option only allows a "high" screen resolution of 800x600. I know that it can go higher than that, but I'm having trouble with getting it fixed like that again. It will either be perfect working within the main part with the login/splash screen either being too big (so large it can't be centered on screen) or it will flicker. 

Is there a quick fix I can do? Could I just choose another option within "sudo gksu displayconfig-gtk" that would be an equivalent to my monitor? Or could I manually fix the monitor problem with "sudo nano /etc/X11/xorg.conf"? The only problem with the xorg.conf option is that I don't know the hsync or vsync of this monitor. I know I'm asking for a lot, but I would gladly accept any help. Thanks!

Hi and the command is just ```
gksu displayconfig-gtk
``` What is the model of the graphics card and have you installed the drivers if any are needed?

---

### Post by acrousey on 2008-08-24
There isn't a graphics card. I think it's integrated with the processor. I have a Pentium 3 processor on this machine, otherwise I don't know anything else.

---

### Post by overdrank on 2008-08-24
> **acrousey said:**
> There isn't a graphics card. I think it's integrated with the processor. I have a Pentium 3 processor on this machine, otherwise I don't know anything else.

Ok if you have integrated graphics you can find the model from the command ```
lspci
``` and look for VGA. You may be able to choose a better resolution for you monitor when using the display configure command.

---

### Post by acrousey on 2008-08-24
This is what I get when I do lspci. I guess it's VGA compatible. What can I do then?


```
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:05.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
01:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
01:0a.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)

```

---

### Post by acrousey on 2008-08-25
After doing some guessing and testing with monitor options, I found out that my PACOM Data, Inc monitor is equivalent to a Korea Data Services one. I spent all of last week trying to find the HorizSync and VertRefresh online for my monitor, but it seems that this company must have fallen off the face of the earth. I guess a lot can happen in 10 years (this monitor was manufactured in 1995!).

---

