---
title: "[64 bit] Problems with RAM and GPU"
date: 2013-04-21
forum: Hardware
---

### Post by Nucleolus on 2013-04-21
Hello and thanks for reading my trouble.

I'm "newbie" in Ubuntu but I have some problems that I have not could solve. I installed Ubuntu 64 bit version in my old laptop in order to improve his performance. This is my configuration:

AMD Turion TL-58 (2 cores - 1.90GHz)
3GB RAM
ATI Radeon x1200

For instance, the system doesn't recognize all the ram memory (Only 2.6 GB) and the laptop goes slower than Windows 8. I think that the problem with ram is because of I don't have the right drivers but I'm not sure.

I love using Ubuntu because it's good to learn about Linux's World but I'm sad to live this experiencie with Ubuntu, the system goes slow.

PD: Ubuntu does not recognize my video card (Unknown) :( How can I do? Where I can download the right drivers? I tried with AMD Catalyst and don't work

Sorry for my english, I'm from Spain :popcorn:

---

### Post by The Cog on 2013-04-21
The free program only shows usable memory. It does not include memory that is occupied by the operating system, so it always looks less than you would expect. Don't worry about that.

As for the GPU, can you post the output of the command 
```
lspci -v
```
which should show us which driver is in use.

---

### Post by Nucleolus on 2013-04-21
Thanks for answering. I feel weird

```
 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series] (prog-if 00 [VGA controller])    Subsystem: Packard Bell B.V. Device c108
    Flags: bus master, fast devsel, latency 64, IRQ 43
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at fd8f0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at 8800 [size=256]
    Memory at fd700000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

```

Uhm, It seems like Ubuntu recognize the drivers but in System Configuration - System - Details - Graphics the "Controller - Driver is Unknown" and the system goes slow

Thanks for your help!! I dind't know about the ram issue

[B]EDIT:

[/B]I put this code in the console
```
[COLOR=#333333][FONT=Courier New]sudo apt-get install mesa-utils[/FONT][/COLOR]

```
and now  System Configuration shows "Gallium 0.4 on ATI RS690" that I know is the correct driver... but I don't know why the system is pretty slow

---

### Post by Nucleolus on 2013-04-22
Up, I have Gallium Drivers but the system is slower than Windows 8 :(

---

### Post by dabl on 2013-04-22
What benchmark are you using to reach your conclusion that your Ubuntu system is slower than Windows 8?  Slower doing what?

---

### Post by d4m1r on 2013-04-22
What version of Ubuntu did you install? Are you sure the proper ATI proprietary drivers were installed?

---

### Post by QIII on 2013-04-22
No proprietary ATI driver will work with that card with any X Server after late 2008/early 2009.

---

### Post by Yellow Pasque on 2013-04-22
> the system doesn't recognize all the ram memory (Only 2.6 GB)
That probably means that the GPU is using 256MB of the RAM (like on Windows). Linux and Windows just report available memory differently.

My suggestion would be to try a different desktop environment than Unity, since Unity is demanding on the GPU and the X1270 is not a powerful GPU (I used to have one). Try xfce/Xubuntu or lxde/Lubuntu.

---

