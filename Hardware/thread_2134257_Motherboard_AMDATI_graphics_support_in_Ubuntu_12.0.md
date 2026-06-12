---
title: "Motherboard AMD/ATI graphics support in Ubuntu 12.04 (64 bit)"
date: 2013-04-10
forum: Hardware
---

### Post by foberle on 2013-04-10
I first installed Ubuntu 12.04 last year and, in general, found it to be quite satisfactory aside from the fact that there seems to be no support for parallel ports or 3.5" disk drives - but this is an O/S obviously aimed at hobbyists and gamers, so that wasn't a big shock. I went through a period where I utilized the Compiz-Config settings manager to establish the desired placement and sizes of the windows for my various applications, and so forth.

And then, since I permitted software updates, an upgrade was installed that removed many of the graphics capabilities of the system.

At that point, I could only run the Unity 2D interface, meaning that the icons on the left side were now BIG, I could no longer control the placement of windows, and could no longer drag windows from one desktop to another. Bummer - it's like going back to Windows 3.1.

From what I was able to find out by trolling the web, Unity had removed its substitute software that made up for the lack of a stand-alone graphics card.

Is there a way to load a driver that might support Unity 3D?

If I run the command lspci -v on my Ubuntu 12.04 system, I get the following:
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780L [Radeon HD 3000] (prog-if 00 [VGA controller])
    Subsystem: Giga-byte Technology Device d000
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at ee00 [size=256]
    Memory at fdff0000 (32-bit, non-prefetchable) [size=64K]
    Memory at fde00000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel modules: radeon

A search for RS780 in the Ubuntu Software Center gives: "X.Org X server - AMD/ATI Radeon display driver"
Pressing the "More Info" button suggests that this is what I might want, but when I choose the Install button, I get the following warning:
"If you install xserver-xorg-video-radeon-its-quantal, future updates will not include new items in the Ubuntu desktop system set. Are you sure you want to continue?"

Note the reference to Quantal, which I don't have. Is there a "Precise" version of this somewhere?

Will any of these things help restore the 3D capabilities, or is it time to try out yet another OS? I kind of like Ubuntu and Unity (at least the 12.04 version), but its capabilities seem to be diminishing over time, and this seems like the wrong direction.

Any help or advice would be much appreciated. Thanks.

---

