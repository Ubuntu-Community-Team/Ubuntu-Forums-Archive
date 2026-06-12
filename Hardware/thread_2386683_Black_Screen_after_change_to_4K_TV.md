---
title: "Black Screen after change to 4K TV"
date: 2018-03-08
forum: Hardware
---

### Post by sbreckheimer on 2018-03-08
Hi,
two weeks ago I received a Lattepanda 4G/64G. This board makes me really enthusiastic and Ubuntu Mate 17.10 worked out of the box on my computer display and my old TV. Both have a 1920x1080 resolution.

Now I have got a new TV (4K Sony) and when I connect this computer as a 4K resolution and Ubuntu stops working with a black screen right after the boot splash screen (Mate logo). Only the mouse cursor is working.

Is there a way to get it working on a 4K screen or better: a way to fix the resolution to the working 1920x1080?

Only recovery mode works great. At 800x600...

I have already installed the latest Intel drivers for Ubuntu from Intel website but they did not solve my problem. Only when I connect the system back to my computer display everything is working fine again.
Regards,
Sebastian

---

### Post by Autodave on 2018-03-09
Since no one else has jumped in...........

I am assuming that you have a good enough HDMI cable for this? An older, cheaper one will not work.

In recovery mode, can you see if the PC is even acknowledging that it found the TV?

---

### Post by sbreckheimer on 2018-03-10
I have tried different HDMI cables upper version 1.4 first. Also tried a very old one in the hope it would be to old and get a 1080p signal. The TV everytime says its input signal is at 3840x2160.

Concerning your second question, the TV is shown as an unknown device in the screen settings in recovery mode.

Maybe that is the reason but how can I solve it?

---

### Post by Autodave on 2018-03-10
What exactly are you running: Ubuntu, Xubuntu, ?  What version?

What video card is in the machine? Have you installed any drivers for it? If so, what one and where did you get it from?

---

### Post by sbreckheimer on 2018-03-10
I am running an Ubuntu Mate 17.10 on the computer. All current updates are installed on the machine.

lspci gives me the following output:
```

00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 36)
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers (rev 36)
00:03.0 Multimedia controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit (rev 36)
00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 36)
00:11.0 SD Host controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SDIO Controller (rev 36)
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 36)
00:1a.0 Encryption controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine (rev 36)
00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 36)

```

I don't know how important it is but 
```
dmesg | grep [vV][gG][aA] 
```
gives the output
```

[    0.264704] pci 0000:00:02.0: vgaarb: setting as boot VGA device
[    0.264704] pci 0000:00:02.0: vgaarb: VGA device added: decodes=io+mem,owns=io+mem,locks=none
[    0.264704] pci 0000:00:02.0: vgaarb: bridge control possible
[    0.264704] vgaarb: loaded
[    2.252179] fb0: EFI VGA frame buffer device
[    2.859682] fb: switching to inteldrmfb from EFI VGA
[    2.859901] [drm] Replacing VGA console driver
[    2.867199] i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=io+mem

```

lshw shows the exact CPU is "Intel(R) Atom(TM) x5-Z8350  CPU @ 1.44GHz" and concerning the display
```

*-display
             Beschreibung: VGA compatible controller
             Produkt: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers
             Hersteller: Intel Corporation
             Physische ID: 2
             Bus-Informationen: pci@0000:00:02.0
             Version: 36
             Breite: 64 bits
             Takt: 33MHz
             Fähigkeiten: vga_controller bus_master cap_list rom
             Konfiguration: driver=i915 latency=0
             Ressourcen: irq:298 memory:90000000-90ffffff memory:80000000-8fffffff ioport:f000(Größe=64) memory:c0000-dffff

```
(Sorry... German output but I hope it's clear enough)

I have installed the drivers from Intel itself (Intel's website) after I noticed that I get the black screen with mouse cursor everytime I boot the system up on the 4K TV. Installing these drivers did not have any effect for me and it seems to be not necessary 'cause Ubuntu 17.10 and higher are almost up-to-date with it. At least the installation did not destroy my computer :) it is still working fine on my computer display which has only 1080p.

---

### Post by sbreckheimer on 2018-03-10
Oops, sorry the above dmesg ouput was taken from the working 1080p monitor. I'm now on the 4K - in recovery mode dmesg says:
```

[    0.266208] pci 0000:00:02.0: vgaarb: setting as boot VGA device
[    0.266208] pci 0000:00:02.0: vgaarb: VGA device added: decodes=io+mem,owns=io+mem,locks=none
[    0.266208] pci 0000:00:02.0: vgaarb: bridge control possible
[    0.266208] vgaarb: loaded
[    2.271357] fb0: EFI VGA frame buffer device

```

There are some lines missing.

---

