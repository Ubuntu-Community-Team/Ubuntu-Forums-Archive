---
title: "Extended screen setup problem"
date: 2009-12-09
forum: Hardware
---

### Post by PetteriP on 2009-12-09
I googled and went through the forum but could not find the exact solution on:
How to set up extended display on Xubuntu 9.10?
The problem most likely is my ancient PC (IBM ThinkPad 600X from year 2000... :D) video drivers, but it's worth asking.

When I plug the external screen on the VGA output the screen clones out nicely. By using the FN-key I can change the view from laptop screen to both to external screen and back again.

On Apps - Settings - Display I can only see the default screen recognized. The output of "lspci | less"
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Communication controller: Agere Systems WinModem 56k (rev 01)
00:06.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
**01:00.0 VGA compatible controller: Neomagic Corporation NM2360 [MagicMedia 256ZX]**
02:00.0 USB Controller: NEC Corporation USB (rev 41)
02:00.1 USB Controller: NEC Corporation USB (rev 41)
02:00.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
06:00.0 Ethernet controller: 3Com Corporation 3cCFE575CT CardBus [Cyclone] (rev 10)
```
shows the same thing - only the default monitor is there.
Needless to say that it's pretty useless to try and find up-to-date drivers for that ;)
Closest ones (and many others) have been installed.

Many a resolution relies on modifying the xorg.conf, but Xubuntu 9.10 doesn't use it.

xrandr or grandr provided no help.

Yeah, yeah, I know, laptop is old and I should get rid of it, but just in case someone already is in the know or is fighting with same thing.

---

### Post by Fafler on 2009-12-09
The Neomagic 256... remember that chip. But not for anything good, really. Had my own troubles with my Toshiba back in the day.

You should try creating a full xorg.conf with xinerama enabled. Xorg should use it, even though it doesn't use a configuration file as default. Are you sure your card has enough memory the use both displays?

---

### Post by PetteriP on 2009-12-09
Thanks, Fafler!

I'll try creating the xorg.conf then, there seems to be a lot related to that so it shouldn't be too difficult. I'll look into it.

Memorywise... Can't say I'm sure. I remember using the PC with projectors in my work way back when, but then again it might have been with a clone screen, can't remember that far back.
Anyhow, I am waiting for some additional memory from the internets, so I'll try again after I install that. Should be later this week.
:D wasn't so easy to find even memory for the box...

---

