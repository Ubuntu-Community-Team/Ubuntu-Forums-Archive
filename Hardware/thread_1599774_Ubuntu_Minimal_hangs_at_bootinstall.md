---
title: "Ubuntu Minimal hangs at boot/install"
date: 2010-10-18
forum: Hardware
---

### Post by jensvdb on 2010-10-18
Hello,

I have an annoying problem with my laptop, a Dell Vostro 1510 (supposedly a hardware problem)... It's a dual-boot environment (Ubuntu Minimal 10.04/Openbox + Windows 7).

My problem is that when I want to boot Ubuntu, 90% of the times it just hangs at startup (so I get the Grub2 menu, and select one of the boot options).
* Windows 7 boots without any problem.
* If I select the standard boot procedure for Ubuntu, it displays a flashing cursor in the top-left corner of the screen.
* If I select "rescue mode" option, a lot of text (hardware detection etc) is displayed on the screen and just when it's done detecting my USB devices, everything hangs. No hard disk activity anymore, nothing... The only thing left to do is unplugging the power supply.
What I DO see is a message when I unplug, for example, my USB mouse, saying that a device is disconnected...
Sometimes I also see a message like this "atkbd.c:## e00e [...] use setkeycodes".

I've already tried the following possible solutions:
* Installing Ubuntu Minimal 10.10/10.04
* disabling the SATA controller in BIOS (AHCI -> ATA mode)
(both with the "quiet" option disabled)
When the SATA controller is disabled, I get a message like this: Ata3.0: Sata link down
again, everything hangs.

Only one time (in the several attempts to install Ubuntu Minimal) the installer went as far as installing the base packages, but then the installer crashed there; hard disk activity suddenly stopped.

I have also tried to boot the Live CD (10.10), which succeeds.

These problems only started a while after I configured my Ubuntu Minimal/Openbox, but then after a few tries my Ubuntu started normally...

My goal is to have a Minimal Ubuntu command-line system with Openbox, so not a resource-consuming full version...

I suppose this is some hardware related error, but after hours of research, I still haven't found what the cause could be...

If needed, I can post a list of my hardware...

Thanks in advance,
JVdB

---

### Post by jensvdb on 2010-10-30
*update*

Last week I've reinstalled OpenBox to another partition.
It ran OK for one week and now I have the exact same problem. The only extra packages I installed (intentionally) are softwarepackages; no drivers, no power management, etc...

Can anyone help me plz, I would really appreciate it ;)

J

Edit: The version of Ubuntu is 10.10

---

### Post by jensvdb on 2010-10-30
*update* (again)

I think I solved the problem by disabling the Plymouth splash screen (thus removing the params "splash quiet" and replacing it by "text".

I don't understand what plymouth has to do with the boot crash, though.

J

---

