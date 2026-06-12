---
title: "High Pitch wine due to ACPI stuff, please help me stop it"
date: 2006-02-02
forum: Hardware &amp; Laptops
---

### Post by nehalem on 2006-02-02
Hi guys,
I got a new laptop and everything works great (compaq nc8230).  For the first time suspend and hibernate is working on linux.  There is one major problem however, when on battery mode there is this high pitch wine.  

While I haven't been able to find anybody having the same problem with this model, the problem described appears to be quite common with Linux on laptops (especially IBM models).  Here are some resources:
[http://www.ussg.iu.edu/hypermail/linux/kernel/0410.0/1707.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0410.0/1707.html)
[http://www.thinkwiki.org/wiki/Problem_with_high_pitch_noises](http://www.thinkwiki.org/wiki/Problem_with_high_pitch_noises)

The solutions I've found are disabling certain power modes or making a change in a header file (1000hz to 100hz) and, I think, having to compile a new kernel.

**My questions:**
Has anyone been able to get around this on breezy.  There are references to breezy on the thinkwike site but still I would love to know from you guys.

Do I have to recompile the kernel to change this?

This is what the thinkwiki has to say about it:
> Change the "HZ" kernel constants to alter the frequency of timer interrupts. Discussion:

    * Andreas Karnahl: i've read in several forums it has something to do with the "idle"-state (or "C3") of the processor. There is a frequency called "timer interrupt" (or so mething like that). Since kernel 2.6x it is set to 1000 Hz by default (compared to 100 Hz in Kernel 2.4x). The exact reason i don't know, but it is safe to change this frequency to 100 Hz in kernel 2.6x (by the way, windows up to XP uses 100 Hz by default).
      Just do the following:

    In [path to kernel-sources]/include/asm-i386/param.h find the line

        #define HZ 1000 

    and change the value of HZ to 100:

        #define HZ 100 

    Then recompile the kernel.
    After i changed it on my ThinkPad A30 (under SuSE 9.2 and 9.3) and recompiling the kernel the high pitch noise is gone away. 

Lastly, I've compiled a kernel once.  I have everything working now, is there a way to ensure that it will keep things compatible with my present settings?  This is a major concern for me and I'm a noob with kernel stuff (I frankly never wanted to have to become anything but a noob but this noise is very annoying).

Thanks a lot in advance!

---

### Post by MighMoS on 2006-02-02
Recompiling your kernel and switching it to 100Hz shouldn't break anything, with the possible exception of binary kernel modules, which you may have to reinstall (such as nvidia's drivers).

---

### Post by nehalem on 2006-02-02
Is this guide the way to go?

[http://ubuntuforums.org/showthread.php?t=85064&highlight=kernel](http://ubuntuforums.org/showthread.php?t=85064&highlight=kernel)

---

### Post by MighMoS on 2006-02-02
Yeap.

---

