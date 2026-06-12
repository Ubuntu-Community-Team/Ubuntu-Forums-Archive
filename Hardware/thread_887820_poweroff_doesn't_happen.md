---
title: "poweroff doesn't happen"
date: 2008-08-12
forum: Hardware
---

### Post by Nopposan on 2008-08-12
Hello there helpful ubuntu fans.

I have a small problem with my latest Xubuntu installation.  FYI, I'm using a Compaq Presario 5304 with a Pentium 2 M processor, 256 MB RAM and a 20 GB IDE hard drive.

The problem is that when I select Quit-->Shutdown, the computer hangs after the usplash countdown bar indicates that all processes have been exited and stopped.  Therefore, I have to manually power off by pressing the power button.  However, when I run the latest stable version of DSL (Damn Small Linux), the computer powers off very nicely.

What the heck, I'll post the output of lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 530 Host (rev 02)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge) (rev b1)
00:01.1 Class ff00: Silicon Integrated Systems [SiS] ACPI
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 11)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:09.0 Communication controller: Agere Systems 56k WinModem (rev 01)
00:0b.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
00:0f.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 530/620 PCI/AGP VGA Display Adapter (rev a2)

```

So, it seems that my system hardware is intended to use ACPI.

Some more information: The BIOS for this old box has no new updates, but what I'm running is from 1999.  There is a message posted immediately upon boot-up that ACPI is not supported for BIOS as old as mine and that therefore "ACPI=force" should be used.  Nevertheless, I believe DSL disables ACPI and APMD at boot, I remember seeing the messages go by, but still somehow manages to perform a shutdown and poweroff.

Please help out if you can.

Thank you.

---

### Post by clubsoda on 2008-09-05
Hi Nopposan,

It seems the 2.6.24-21 kernel may have an [ACPI issue](http://ubuntuforums.org/showthread.php?t=909121) on certain machines, not all as old as ours. :) Try an earlier kernel - my machine likes 2.6.22-14.

Do both your "Quit" buttons work?  The one on the panel works fine for me but the one in the Applications menu is broken.

Cheers.

---

