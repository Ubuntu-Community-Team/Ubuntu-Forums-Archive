---
title: "start-up issues"
date: 2008-05-30
forum: Hardware
---

### Post by MALEADt on 2008-05-30
Hi all,

I have recently installed bootchart to optimize my boot process a bit. However, I cannot resolve two minor issues who does slow down the boot process by about 1/4th...

First of all, an image _[of the boot process (click here)](http://users.telenet.be/maleadt/bootchart.jpg)_.

You can clearly see there is a zombie fsck process around the 24th second, doing _absolutely nothing_ for abouth 5 seconds. It does not use any CPU, neither does it accesses my hard-drives, quite useless if you ask me.
As far as I can see, the fsck process I'm talking about spawns a reiserfsck process to check my (ReiserFS formatted) root partition. I suppose this is done by *checkroot.sh*. However, after the reiserfsck process has successfully finished the fsck-parent process keeps on hanging for about 5 seconds.
Has somebody got any idea if this is normal, and if not how I could resolve this issue?

A second (minor) problem is the firmware loading of the cx25840 module (cx25840_fw). That firmware loading process accesses my hard-drive quite happily, which I would not mind if I needed that module (which I don't)... I do need the cx2341x module for my Hauppauge tuner card, but the cx25840 module is not needed at all for my system (lsmod shows no relationship between both modules, and the cx25840 module is not used by any other module).
So I tried blacklisting the cx25840 module. Alas, the firmware still got loaded, resulting in a 5 second high IO level, which slows down the entire boot process of course. Side note: when I blacklisted the cx25840, my TV tuner still worked perfectly, which proves I do not need that module at all.
Is there any way to blacklist the firmware loading process? I'd be happy to reduce the boot-up process by another few seconds :)

Thanks in advance!
maleadt

---

