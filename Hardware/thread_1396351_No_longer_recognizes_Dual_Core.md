---
title: "No longer recognizes Dual Core"
date: 2010-02-01
forum: Hardware
---

### Post by dougHines on 2010-02-01
I was goofing around in my system and I think I may have broke it.  My system monitor use to show 2 processors.. but now only 1.  I was curious if there was a way to fix this, or if i would have to rebuild my system to get my second proc back.

---

### Post by jerrrys on 2010-02-02
what kind of processor do you have?

---

### Post by dougHines on 2010-02-02
I'm running a Pentium 4 Dual CoreDuo proc.

---

### Post by kayvortex on 2010-02-02
Man, that must have been some messing about. Do you remember what you did? Did you echo commands to /proc or /sys, or mess around with your grub entries?

Anyway, what does
```
cat /sys/devices/system/cpu/cpu1/online
```
print out?

Could you also post you grub file: /boot/grub/menu.lst or /boot/grub/grub.cfg (whichever one exists).

---

### Post by dougHines on 2010-02-02
yeah, I'll post all of that information tonight when I get off of work.

---

### Post by dougHines on 2010-02-07
So I restarted my machine and apparently everything works now.  Talk about Ghosts in the machine.

---

### Post by kayvortex on 2010-02-07
> So I restarted my machine and apparently everything works now. Talk about Ghosts in the machine.

I'll say! I'm glad the "problem" has been solved.

---

