---
title: "Audigy sound failed"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by willemto on 2009-11-02
After starting 9.10 Kernel 2.6.18-16, I can not get the sound to work. My system has the following card:

06:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
    Subsystem: Creative Labs Device 2001
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at 1000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: EMU10K1_Audigy
    Kernel modules: snd-emu10k1

willem@linuxbox:~$ aplay -l
aplay: device_list:223: no soundcards found...

willem@linuxbox:~$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory

What do I do? None of the web advice has worked thus far.

---

### Post by willemto on 2009-11-03
I found a solution after a day of struggle.

1. Trying to run any sound on ubunto called kernel 2.6.28-13 does not work.
2. I installed grub2
3. Following the instructions from [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) and compiling [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.31.5.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.31.5.tar.bz2).

The new kernel was automatically added to grub2, and hey presto, sound again. Cut and Paste seems to now work better than ever than with the ubuntu dirrived kernels. It also seems faster.

Hope this is helpful to somebody. (I still can not boot ubuntu kernel 2.6.31-14-generic.)

---

