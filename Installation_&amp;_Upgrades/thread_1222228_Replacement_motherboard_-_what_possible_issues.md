---
title: "Replacement motherboard - what possible issues?"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by risingsun on 2009-07-24
After a hard reset due to the machine freezing my machine no longer reaches POST unfortunately. (The LED combination informs me that it's hanging on "decompressing BIOS to RAM for fast boot", so presumably it's either the ram or the motherboard in some form.)

I decided I would get a new motherboard to replace it to see if it's the problem (if not I could find a use for it anyway) but my dilema is that since I purchased it a year ago it doesn't appear to be made anymore. I can get one of the same socket type for the CPU but I was curious what issues this might raise with my Ubuntu installation. I'm not really familiar with things such as the kernel so I wouldn't know if it would have to be rebuilt due to different integrated motherboard components etc. Would anyone be able to enlighten me on this issue? :)

Many thanks.

---

### Post by Rocket2DMn on 2009-07-24
Unless you have a custom built kernel already on your Ubuntu machine, swapping the motherboard shouldn't be a problem.  Just like when you pop in a Live CD on any system, the hardware should be detected at boot and should run normally.
If you are using integrated graphics and the video card manufacturer is different, then you may need to reinstall video drivers, but otherwise it should be fine.  Integrated Intel graphics are fairly common, and they should work normally.

---

