---
title: "Very low frame rate on Ubuntu 12.04 using NVIDIA card"
date: 2012-11-09
forum: Hardware
---

### Post by thnewguy on 2012-11-09
I recently installed Ubuntu 12.04 (64-bit) on my desktop this week and I've noticed the video performance is quite low. I've got a NVIDIA card GeForce 6150 in it and I installed the recommended proprietary driver. At the moment I'm getting a frame rate of about 6 FPS. Obviously this makes any sort of gaming impossible. and I'm curious as to how I might gain better performance?

I've tried switching to using Unity 2D, I've tried dropping Unity all together and just logging into Openbox and I tried reverting back to the open source driver. So far nothing has raised my FPS above about 8-10.

According to the NVIDIA settings panel I'm using driver version 295.40 and a newer, experimental driver, is available. Has anyone tested the latest beta driver? Is it stable enough to use on a day-to-day basis?

---

### Post by BicyclerBoy on 2012-11-09
There would not have been any performance improvements for old cards.

The 6150 is the oldest/slowest card still supported by the current driver.
The 6150 has no openGL power & possible but limited VDPAU for video decode playback.

The nForce 730/750/780/980 were the better ones but they're all hopeless.

Is this a mobo chipset graphics GPU?

The nvidia 7950 (possible AGP) is about 20x faster.

---

### Post by thnewguy on 2012-11-09
This is a motherboard graphics card.

I tried the experimental NVIDIA driver and it not only didn't improve performance, but it prevented my OS from booting. I can't even get recovery mode to work. I'm going to re-install and stick with my humble low-end graphics.

---

### Post by BicyclerBoy on 2012-11-10
Some of the humble mobo graphics had their good points..low power & full HDA hdmi audio & VDPAU before the discrete cards..

7800GS is prob fastest nVidia AGP that was common.

The last AMD/ATI AGP was better but maybe not with linux..

You might find an old nVidia 7300GT for free..

---

### Post by deadflowr on 2012-11-10
You'll probably have more success installing the current-updates version over the the standard currents version.
I believe the updates version is 304.whatever-whatever.

However the 6150 card has had poor support since 12.04 was released.
Sad really, seeing as to how many people are using it.

---

### Post by BicyclerBoy on 2012-11-10
The 6000s family is still supported by the latest driver..
nVidia provides 2 legacy driver branches & provides builds for diff Xorg versions.

How is that poor support?
The std ubuntu desktop demands more GPU resources & old cards do not have any.

---

