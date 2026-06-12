---
title: "Radeon 9500NP with Open Source Drivers"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by alephnaught on 2007-05-08
I'm using a Radeon 9500 non-pro video card with the open source radeon drivers, and I've been trying to get Beryl to work with AIGLX. I've had some success, but unfortunately I have horrible checkerboarding artifacts all over the screen.

A bit of background on the 9500 NP cards - they actually have 8 pixel pipelines, but have 4 disabled. Some of the cards can be modded up by enabling those pipelines, however some of them, such as mine, have faulty pipelines and so produce artifacts when attempting to do this.

I noticed that the artifacts produced by using Beryl were similar to those generated when I attempted to mod my card. Thinking that perhaps my card was being misdetected, I specified the ChipID for the 9500NP (0x4144) in xorg.conf, hoping this would fix it. No joy.

My conclusions from a lot of detective work are that the open source radeon drivers treat all 9500s the same, irrespective of the ChipID. Hence, it tries to use all 8 pipelines, and generates artifacts.

Does anybody know of a way around this, besides using the proprietary drivers (which I'd rather avoid)?

---

