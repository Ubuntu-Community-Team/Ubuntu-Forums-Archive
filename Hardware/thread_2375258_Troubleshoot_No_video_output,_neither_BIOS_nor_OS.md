---
title: "Troubleshoot: No video output, neither BIOS nor OS"
date: 2017-10-23
forum: Hardware
---

### Post by Kurt_Alan on 2017-10-23
a. powers on
b. one day: normal output; another day: no output upon cold boot

Any steps I missed?

1. Re-seated RAM and swapped positions; tried single vs. double
2. Re-seated SSD
3. Cleared CMOS
4. Swapped known good monitor
5. Swapped cables, DIVX, VGA

Unable to identify faulty component or connection; do not have known good parts to swap.

---

### Post by DuckHook on 2017-10-23
Have you tried swapping the video card? Often the cause of flaky video. If you are using the MOBO video then try using a separate card. If already a separate card, try reseating it. Also, look at your logs. A flaky video subsystem will sometimes (not always) spit out error messages. You could also try running Xenial to see if things are more stable under an LTS.

---

### Post by Kurt_Alan on 2017-10-27
Thank you. Video is embedded in Intel cpu; no video card. Not question of OS instability. Cannot even output BIOS.

---

### Post by efflandt on 2017-10-27
It is possible for on-board graphics to fail. Years ago we had on-board graphics fail on a Dell Optiplex at work. Warranty was only for parts at the time, so Dell sent a new motherboard and it was my first experience completely installing a motherboard and shifting CPU and all connections to it. Although I had upgraded CPUs before upgrading a 386DX33 to Cyrix 486DRx2/66 along with 387 math co-processor and Pentium 100 with Pentium 180 Overdrive (which ran @ 200 MHz due to 66 vs 60 MHz clock speed).

---

### Post by DuckHook on 2017-10-28
> **Kurt_Alan said:**
> Thank you. Video is embedded in Intel cpu; no video card. Not question of OS instability. Cannot even output BIOS.
If you cannot output BIOS, then it is almost certain your video subsystem is shot. Your APU may be okay, but MOBO could be problem. As I mentioned earlier, the only way to test is to install another video card and see if that works.

---

### Post by Kurt_Alan on 2017-10-28
> **DuckHook said:**
> If you cannot output BIOS, then it is almost certain your video subsystem is shot. Your APU may be okay, but MOBO could be problem. As I mentioned earlier, the only way to test is to install another video card and see if that works.

Install another video card? I had missed that. Thank you.

---

### Post by Autodave on 2017-10-28
I have seen where RAM sticks can cause that same problem. However, you should at least see something on the screen as it starts to boot.

---

