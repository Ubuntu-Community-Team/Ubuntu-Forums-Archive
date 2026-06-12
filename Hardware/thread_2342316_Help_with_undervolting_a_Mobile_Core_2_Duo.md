---
title: "Help with undervolting a Mobile Core 2 Duo"
date: 2016-11-05
forum: Hardware
---

### Post by aurora4 on 2016-11-05
Hey everybody,
I have an HP G70 laptop with a Core 2 Duo T9800 @ 2.93GHz that I wish to run Ubuntu MATE on via WUBI as Windows is a tad too clunky as I no longer need it that much since I have ceased gaming on it as I've gotten a console (and the GPU wasn't very good either - GMA4700MHD).

Sadly, this laptop has quite a heat problem and the best way I've found to mitigate this problem is by undervolting the CPU via RMClock on Windows. While on Windows this works very well, on Linux I can't find a good way and tutorial for it that supports Ubuntu 16.04 (or 16.10 but I would prefer an LTS). I know that PHC exists but the latest version that it's available for is Ubuntu 12.04 AFAIK. Temperatures run up to 80-ish C when software decoding a video on YouTube when not using the undervolt and the computer heats up much more when I don't undervolt the CPU.

My undervolting settings are:
P Type       Mult  Voltage
0 SuperLFM 6.0x  0.9V
1 Normal   6.0x  1.0000V
2 Normal   7.0x  1.0000V
3 Normal   8.0x  1.0000V
4 Normal   9.0x  1.0000V
5 Normal   10.0x 1.0125V
6 Normal   11.0x 1.0375V
7 IDA      12.0x 1.0625V



The GPU is a GMA4700MHD and I plan to use VAAPI for the GMA4500MHD (4500/4700MHD are the same, the 4700 name is because the FSB on my CPU is 1066MHz). Has anyone used the g45-h264 branch of VAAPI lately and what do you think about that? I wish to use GPU acceleration to lighten the load on the CPU as much as possible. [https://sourceforge.net/projects/g45h264/](https://sourceforge.net/projects/g45h264/)

In terms of Linux-related skills, I have compiled and installed drivers in the past on Debian based systems so I don't mind compiling and installing something myself. 

Thanks,
Aurora

---

### Post by QIII on 2016-11-05
Hello!

WUBI is no longer maintained and its use is not recommended by the developers.

I would suggest proper dual booting as an alternative.  A WUBI install would likely be unaffected by anything voltage setting you made in Windows.

Cheers!

---

### Post by aurora4 on 2016-11-05
Yeah, I know about that, I don't mind doing proper dual booting if I find a way to get past the undervolting problem :) Thanks!

---

### Post by QIII on 2016-11-05
What adjustments are made available by the BIOS?

Have you cleaned the HSF?  Perhaps disassembled the machine to replace the thermal compund?

I'd consider cooling system issues before emasculating the CPU.

---

### Post by aurora4 on 2016-11-05
I don't do any adjustments in the BIOS as they aren't available sadly. The machine's thermal paste was replaced about a year ago when the CPU was replaced but it heated up from day one sadly. Undervolting via RMClock has not been problematic so far and I've been running it for almost a year without any issues

---

### Post by QIII on 2016-11-05
Is it possible ther thermal paste was not applied properly?  Have you checked the Intel specs to see if the temps you are seeing are out of line?

(Just trying to think about everything else before undervolting, which is a waste of the expense of the CPU.)

---

### Post by aurora4 on 2016-11-05
I'm not sure about whether the thermal paste was applied properly but considering that the laptop has been heating from day one and other people have had the same laptop heat up quite a bit shows that it's probably a design flaw. The temperatures are certainly out of line as when both cores reach 70-85% on 2.93GHz (when undervolted, when it's not undervolted, throttling happens much earlier) and stay that way for 5-10 minutes, the CPU starts to throttle badly as it reaches 100 C.

It wasn't really an expensive purchase as it was only about 65 dollars with installation as it's a used CPU (but it's decent nonetheless). Undervolting is probably what helps keep this laptop alive, getting 70 C while doing light tasks was pretty normal.

---

### Post by QIII on 2016-11-05
Yeah, throttling like that is certainly bad.

Still it may be worth that last-ditch effort to check the HSF thermal compound, etc.

Unfortunately, many mobos that do not have BIOS adjustments are built to allow the OS (read: Windows) to make such adjustments.

But, let's see if someone comes up with a solution for you.

Best wishes!

---

### Post by aurora4 on 2016-11-05
Gonna try using this as it's updated for kernel 4.8 [http://www.linux-phc.org/forum/viewtopic.php?f=7&t=267](http://www.linux-phc.org/forum/viewtopic.php?f=7&t=267)

---

