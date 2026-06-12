---
title: "HDMI port only works in the morning."
date: 2008-05-14
forum: Hardware
---

### Post by BetterSense on 2008-05-14
Yeah, strange. To clarify, it only works properly if the computer is turned off for a few hours and becomes cool.

I have my Sony Tube tv plugged in with HDMI for when I occassion to watch a movie. If I happen to have just started my computer, it will work fine.  Every time I've tried otherwise, the display is tearing, juddering, and 3D effects crash it. Meanwhile my VGA connected main monitor is fine. Usually what happens is I then fiddle around forever trying to get it to work, including rebooting multiple times, then I turn the computer off and use my DVD player as a last resort. When I start the computer back up in the morning, the HDMI port works again just fine, and seems to for a good while; I played about half of a movie without any problems.

I have a Biostar mATX motherboard with a Nvidia 7050/630 chipset, and I'm using a 19" LCD monitor via VGA and my HDTV via HDMI. I've allocated the max amount of video memory in the BIOS (256). I have a 5400+ processor and 4 gigs of ram, running Hardy. There's no changes in the xorg.conf between when it is working and when it isn't.

Do you think the graphics chipset is overheating? CPU temp is 35 even under load, with a scythe ninja heatsink. Should I overclock, or better heatsink my chipset?

---

### Post by Zorael on 2008-05-14
Bah, I wrote a long post until I realized you had an integrated video chipset.

I'd try opening the case up and put an external fan to blow inside (aiming for the gpu). If it works, consider heatsinking it. You could try to measure the temperature if you have a good thermometer of some sort. If you're feeling adventurous, place a finger on the chipset (after properly grounding yourself to get rid of static) and see if it comes away scorched.  There's nothing like good ol' second-degree burns. :>

Reviewing case air flow is always a good idea, too.

---

### Post by BetterSense on 2008-05-14
> **Zorael said:**
> Bah, I wrote a long post until I realized you had an integrated video chipset.

I'd try opening the case up and put an external fan to blow inside (aiming for the gpu). If it works, consider heatsinking it.

Reviewing case air flow is always a good idea, too.


What exactly is the GPU? There is a smallish heatsink attached to the motherboard; I assumed this was the GPU heatsink, so I could blow air on it, or see if it could possibly be removed and replaced by a bigger one. 

It's true I don't have much for case airflow; I have the Ninja mini cardboard-ducted directly to the rear case fan, and the front case fan turned down all the way; having an opinion that the CPU heatsink is mostly what mattered in matters of PC cooling.

---

### Post by Zorael on 2008-05-14
GPU stands for Graphics Processing Unit. So, the videocard's processor. Never having owned a motherboard with integrated video, I couldn't even begin to describe where to find it. If it's a separate chipset (likely), then it should say Nvidia.

The other chipsets on the motherboard are *bridges. Refer to these wikipedia entries on [Northbridges](http://en.wikipedia.org/wiki/Northbridge_%28computing%29) and [Southbridges](http://en.wikipedia.org/wiki/Southbridge_%28computing%29). Think of the Northbridge as the core of the motherboard. If it overheats, well, things can go downhill. Further, they're often cooled by small heatsinks with cheap-as-dirt fans that break down after a few months of use; if cooled at all.
> The northbridge on a particular system's motherboard is the most prominent factor in dictating the number, speed, and type of CPU(s) and the amount, speed, and type of RAM that can be used. Other factors such as voltage regulation and available number of connectors also play a role. Virtually all consumer-level chipsets support only one processor series, with the maximum amount of RAM varying by processor type and motherboard design. Pentium-era machines often had a limitation of 128 MB, while most Pentium 4 machines have a limit of 4 GB. Since the Pentium Pro, the Intel architecture can accommodate physical addresses larger than 32 bits, typically 36 bits, which gives up to 64 GB of addressing (see PAE), though motherboards that can support that much RAM are rare because of other factors (operating system limitations and expense of RAM).

A northbridge typically will only work with one or two different southbridge ASICs; in this respect, it affects some of the other features that a given system can have by limiting which technologies are available on its southbridge partner.

The north bridge hosts its own memory lookup table (I/O memory management unit), a mapping of the addresses and layout in main memory.

---

