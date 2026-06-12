---
title: "Ubuntu / PopOS - displays got disconected, GPU / driver crashes"
date: 2024-04-28
forum: Hardware
---

### Post by jarekdudzinski on 2024-04-28
Hi. I'm having strange problem. Under PopOS (latest version, fully updated, I've tested various nvidia drivers versions there, installed fresh system, ...) and on Ubuntu 24.04 LTS (clean install, default nvidia driver installed by os) my GPU (or driver) just crashes, display/s (tested with one and two connected) got disconnected ("no signal"). System itself runs, just app that used the GPU crashes - I've also tested this with one screen connected to iGPU.
It happens when I start playing game using Lutris (windows game), Steam, or just rendering in Blender using GPU.

On nVidia forums I got few suggestions:
- "GPU is just dying" - impossible: it works perfectly under Windows (I'm mostly using this for rendering in Blender), games won't crash, ...
- "the psu is breaking down on power spikes" - same thing, PSU is ok, I have 850W platinum one with i7-13700K and RTX 3060Ti, so it's powerfull enough with big safety margin. Also, under Windows, I overclocked CPU (5.1 GHz on all cores) - computer works there like a charm.

My specs:
ROG Strix Z790-I Gaming - first with older BIOS that I was using before, then, after problem started occurring, I have updated to the latest one
Intel i7-13700K
Gigabyte GeForce RTX 3060Ti Eagle
ram - tested this with two different sets of Kingoston DDR5-5200, one 32GB, second 64GB
nvme ssd - also tested with two different drives (one Sandisk, one WD Black)

nVidia log report:
[ATTACH]293714[/ATTACH]
this one is from my first install of PopOS, which I was using for work.

Doesn't matter what I try - fresh install, PopOS or Ubuntu, different nvme SSD (WD Black was giving me some errors - I switched port, then changed to Sandisk), different memory set, different PSU (got second computer with 650W PSU) - nothing helps. Sometimes it's ok for few renders / an hour of gaming, sometimes it crashes (on fresh OS install!) just after starting Blender.
Just reinstalled Windows - tested Blender, some games - rock-stable, as always.

Any ideas what else should I check / test? I'm really desperate to get rid of windows... - but for now need to finish work :(

---

### Post by MAFoElffen on 2024-04-29
What version of Ubuntu is this? That makes a big difference. PopOS is 'Edge', so is running a lot later kernel 6.8.x) than Ubuntu 22.04.4 w/ the HWE Stack (6.5.x).

NVidia Drivers for Ubuntu 22.04.4 w/ kernels 6.5.x had a problems where the ggc compiler needed to be the same version as the kernel was compiled with, to be able to compile the kernel's nvidia modules... See where that goes? I have work-arounds for that, but need to know if that is what is going on first. Ubuntu 24.04 is on kernel 6.8, and current PopOS have a newer ggc compiler, so are not affected by that.

Would you please fill in the blanks of that information?

---

### Post by jarekdudzinski on 2024-04-30
It was Ubuntu 24.04 LTS, not 22.x

---

### Post by jarekdudzinski on 2024-04-30
SHORT UPDATE: found the reason of crashes - power connector on cable between PSU and GPU... :D

LONG UPDATE:
I did more investigation after problem started occurring on Windows too - which never happened before. Would never thought about power cable - because cable was pretty new, and I didn't disconnected it too often. Unfortunately, when checking computer with second PSU - I didn't changed the cable, as both PSUs are from the same manufacturer... :)
Funny thing is, after system reinstall (no matter if it was linux or windows), crashes never occurred on the beginning. I was able to use computer for few hours without problems. Then - they got slowly worse and worse... getting to a point, when computer crashed just by opening Blender with default, empty scene.
Also I wonder why under linux the problem was bigger (crashes occurred more often and quicker) than on Windows?

Anyway - after running FurMark spanned across two displays, opened game in windowed mode and Blender rendering scene using GPU - all at once, for about 2-3h - no crashes. And today I was working for about 3 hours already (GPU rendering) - still rock-solid :)

---

