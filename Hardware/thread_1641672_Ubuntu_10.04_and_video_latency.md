---
title: "Ubuntu 10.04 and video latency"
date: 2010-12-09
forum: Hardware
---

### Post by HC007 on 2010-12-09
Hello, all, a success story to hopefully help others.  I installed Ubuntu 10.04 on a home-built PC which I had lying around from an old client.  I am using the system to run a CNC table (Fireball v.90) and was having a lot of video latency with the base-install (provided by EMC2 via Probotix, which includes the EMC2 software).

When I would drag windows around the screen I would get ghost images of the window and the processor utilization would jump to 100%.  The system has an ASUS A8V-VM motherboard, AMD Athlon 3500+ processor, and 2 GB of RAM.  The video was provided by a VIA chipset on the motherboard (integrated graphics).  I had Video Effects (System->Preferences->Appearance / Visual Effects tab) set to None.  Hoping it was just a video card problem (and reading lots of pages about various video cards that worked and didn't with Ubuntu/Linux) I bought a new video card to try it out.

I bought a Gigabyte GV-N240D3-1GI card with an nVidia GeForce 240 chipset and 1 GB of VRAM.  I installed it, disabled the onboard card, rebooted and Ubuntu loaded right up, no problems.  I tried the dragging windows thing and still got 100% processor utilization but not nearly as much window ghosting as I had before.  I went to Visual Effects and thought maybe turning it to Extra would enable the hardware acceleration on the card.  Ubuntu prompted me to install the nVidia proprietary drivers and I allowed it.  It reset the Visual Effects to None and told me to reboot and reselect the Visual Effects.  After rebooting I did NOT change the Visual Effects and ran System Monitor and opened Firefox, the same thing I had done with both the VIA chipset video and with the Gigabyte card after I first booted to it.  However, now, when I drag a window rapidly around the screen, I have almost no latency with the video and the processor utilization doesn't go over 80%.  Not perfect but a major improvement.  For me, the best part was that the Latency test included with EMC2 that had reported over 500,000 ns latency for both the Servo thread and the Base thread dropped to less than 25,000 each.

Hope this helps.

--HC

---

### Post by steve7777777 on 2010-12-09
Great! Thanks for sharing!

---

