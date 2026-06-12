---
title: "I think I have a hardware issue"
date: 2009-12-07
forum: Hardware
---

### Post by pearldrums on 2009-12-07
so I've been having issues booting up lately, and I'm sure its hardware because it effects Ubuntu and Windows and I've re-installed the bootloader (along with all of ubuntu) without seeing any change. I cant really tell you what happens, but sometimes the operating systems like to load, and some times they don't. However, the computer boots up grub without any difficulty.

I ran memtest. Its supposed to check your RAM right? Well, it started rattling errors of like nobodies business. After 50 min there were more than 2000 errors and I had to go to work, so I left it running. When I got back the computer had shut down. Does this mean that one of my sticks of memory is bad? I've had bad RAM before and it did cause issues booting up some times, but it also caused the computer to do other quirky things and randomly crash, this isn't happening.

What do my memtest results mean, and do you think they may be related to my issues booting up?

---

### Post by lloyd_b on 2009-12-07
If memtest is reporting errors, then something is wrong.  A bad memory stick is the most likely candidate, but it could be a motherboard issue as well.

If your system allows it, remove one of the memory sticks, and run memtest again.  Then switch the memory sticks, and run it again.  If you only get errors on one, then you've identified the problem.

Exactly what kind of problems a memory issue can cause depends on exactly where in memory the error is - if it's at a low address, then it could easily affect the boot-up sequence.  At a higher location, it might boot cleanly, but then fail once a program tried to access that memory location.

Regardless of whether the memory is the *only* problem on the system, it is *a* problem on the system, and you need to fix it before you can determine whether there's another problem or not.

Lloyd B.

---

### Post by pearldrums on 2009-12-09
thanks lloyd, it did turn out to be a bad stick of ram (so far). It was the mate to the one I had go bad about a year ago. I'd like to say that I'll never buy OCZ again, but the other two sticks in there that have been working for 4 years are OCZ. *shrug* I guess I just need to shy away from the cheap ones.

---

