---
title: "what happened to NVIDIA drivers?"
date: 2023-11-30
forum: Hardware
---

### Post by mon^rch on 2023-11-30
hi guys, I like to keep things fresh so I installed Mantic Minotaur and I really like all the changes; save for a few. what happened to nvidia legacy support? my nvidia videocard worked fine in the previous release, so one would think...

01:00.0 VGA compatible controller: NVIDIA Corporation GF114 [GeForce GTX 560 Ti] (rev a1)

I tried the offficial nvidia drivers from nvidia and the installer fails in recovery mode.

help, ubuntu without a decent graphics driver is a bit slow

...thanks in advance

---

### Post by #&amp;thj^% on 2023-11-30
They dropped support for your card a while back, some have better results adding a third party source.
Please see and try here: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by TheFu on 2023-11-30
nvidia drops support for old cards all the time.  Welcome to proprietary software.  

Remember when all our peripherals stopped working from WinXP to all later releases because nobody upgraded old drivers for non-new hardware?  Same thing.  Companies make money selling things.  Ideally, they'd like us to pay monthly, forever.  If you get 10 yrs from a GPU release date, count yourself lucky.

I have some printers, scanners and slide scanners that stopped working then.  BTW, I was also burned by nvidia dropping support for my trusty GPU.  I made the mistake of getting a newer, cheap, 1030 GT which had better support, but came with buggy nvidia drivers that would screw something up in the system about once a year. Finally, my solution was to get an AMD Ryzen with a built-in iGPU that was faster, used less power, and had drivers shipped with the Linux kernel. Since doing that, I haven't had any GPU driver issues after I upgraded to a supported kernel version.  New iGPUs required at least 5.10.x kernels for the support to be built-in and I stayed on the 4.15.x kernel line from 18.04 for a few months after the new system was built before moving to 20.04.

---

### Post by dltech on 2023-12-15
I tried launchpad drivers for my 450, but it caused a black screen, while on ubuntu 22.04 they was in native repo and worked.

---

### Post by oygle on 2023-12-17
> **1fallen said:**
> They dropped support for your card a while back, some have better results adding a third party source.
Please see and try here: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

That probably xplains why I have had serious graphic card problems lately - [https://ubuntuforums.org/showthread.php?t=2493512](https://ubuntuforums.org/showthread.php?t=2493512)

---

### Post by him610 on 2023-12-18
@TheFu
> ... my solution was to get an AMD Ryzen with a built-in iGPU that was faster, used less power, and had drivers shipped with the Linux kernel.
This is what I decided to do also. I had been considering upgrading my GFX card, but I remembered reading of your experience with Ryzen 5-5600G and I thought to myself, "Why not?"
My Ryzen 5-5600G arrives tomorrow.

---

### Post by dltech on 2023-12-22
The same problem with 390 driver, xorg crashes with ```
malloc(): unaligned tcache chunk detected
```

Stupid error of kernel module builders led to segfault. Linux lose it's main advantage in any hardware support, and becames windows-98 like useless.

---

### Post by BicyclerBoy on 2023-12-31
Unfair to blame them. Not their responsibility.
Nvidia often patches the old legacy driver series so they still work with later kernels.

Unfortunately, the GTX560 just fails outside of coverage by 470 legacy driver (470 still builds against kernel 6.5).

---

