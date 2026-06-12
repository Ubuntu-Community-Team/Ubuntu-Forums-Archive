---
title: "Help seeing if my PC is ubuntu compatible"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by ekmon1582 on 2008-04-02
How do I tell if the video card in my laptop is good enough to run Ubuntu? I've been having a lot of trouble with display of Ubuntu, so I'm thinking my video card may be the reason.

---

### Post by dannyboy79 on 2008-04-02
if you have already installed it or using the livecd, open a terminal session by hitting alt & f2, then in the box that appears, type in gnome-terminal. then in the terminal enter this command and hit enter

lspci -v

and paste the results back here.

---

### Post by ekmon1582 on 2008-04-02
OK here they are.

00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
        Flags: fast devsel

00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
        Flags: bus master, medium devsel, latency 0

00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II] (prog-if 8a [Master SecP PriP])
        Flags: bus master, fast devsel, latency 64
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at c000 [size=16]

00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter (prog-if 00 [VGA])
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=8M]

00:03.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 40)
        Subsystem: Advanced Micro Devices [AMD] PCnet - Fast 79C971
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at c020 [size=32]
        Memory at f0000000 (32-bit, non-prefetchable) [size=4K]

00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
        Flags: bus master, fast devsel, latency 0, IRQ 10
        I/O ports at c040 [size=32]
        Memory at f0400000 (32-bit, non-prefetchable) [size=4M]

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
        Flags: bus master, medium devsel, latency 0, IRQ 9

---

### Post by ekmon1582 on 2008-04-03
So does it look like it is? (I didn't put that emote in there)

---

### Post by dannyboy79 on 2008-04-03
im sorry, after googling and looking around I don't know about linux support of that graphics card. did you try the livecd or you said you have it installed already? so you're saying it's just slow graphics or what's wrong? are you using the vesa driver? issue this command and paste back the results.

cat /etc/X11/xorg.conf | grep Driver

---

### Post by ekmon1582 on 2008-04-03
No, but say OK. Last time I had it installed with an install disc on my virtual machine, and I save 1 pic to the desktop, after that when I started it up, it was so scrambled i couldn't do anything, also when I try to change to a small resolution it was scrambled. But yes I used an install disc to install it. I'm not sure about the driver, I think I am. Here's the results.

        Driver          "kbd"
        Driver          "mouse"
        Driver          "synaptics"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "vesa"

PS. sorry if I seem to get jumpy.

---

### Post by dannyboy79 on 2008-04-03
are you running in a virtual environment now? i am really not sure which driver you should be using if vesa isn't even working.

---

### Post by ekmon1582 on 2008-04-03
At the moment no, the screen is so small I can't do much right now.

---

