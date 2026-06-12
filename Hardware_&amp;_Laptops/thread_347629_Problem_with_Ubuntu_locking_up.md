---
title: "Problem with Ubuntu locking up"
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by beniwtv on 2007-01-27
Hi.

I own a HP Pavilion dv6106eu laptop.

So far I managed to resolve nearly all the issues with the hardware configuration under Ubuntu.

However, a problem still remains: Ubuntu locks up frequently.

I have a temperature monitoring system - but the CPU, Graphic card and the HDD remain cool.

Now, my question: How do I start troubleshooting the problem? 

I have reviewed dmesg en the messages logs, but nothing comes up.

Quick facts about the system:

AMD Athlon 64 Turion x2 @ 1.6 GHZ
512 MB DDR2 RAM (1 module)
80 GB internal S-ATA HDD
GeForce Go 6150 128 MB shared
Nvidia nforce chipset

All works great except the lockups....

I can also play Nexuiz without any problems, as long as I want when the laptop does ot lockup.

Hope anyone can help me!

Note: Also, debian has the same problems.
Note 2: I *think* it's not only X locking up, since I can't even use any keyboard command when it happens.

---

### Post by beniwtv on 2007-01-29
BUMP! Any ideas? :(

---

### Post by Moulton on 2007-02-04
I have a similar problem, and I've determined that the lockup occurs when I am typing on the keyboard (in any application).  If I am browsing with the mouse and not typing, it never locks up.

This leads me to suspect the bug is in the kernel keyboard driver, or perhaps the X.Org keyboard driver.

---

### Post by beniwtv on 2007-02-05
Well, I installed Feisty this weekend and so far I had no real freezes. *Crossing fingers*.

Strange thing to note is:

1. When I'm in single mode (console only), and there's scrolling text output, it will freeze.
2: GFX card is at 79º C. Talked with HP about it and they say it's normal...
3. Desktop hadn't any freezes since Edgy.
4. Nothing shows up in any log.
5. In Edgy, freezes happened after enabling ndiswrapper - guess Nvidia + ndiswrapper have some problems too...

I guess my probem was (or is) ndiswrapper... We will see.

---

