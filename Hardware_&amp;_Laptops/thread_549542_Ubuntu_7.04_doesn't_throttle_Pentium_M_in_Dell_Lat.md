---
title: "Ubuntu 7.04 doesn't throttle Pentium M in Dell Latitude D600 as low as Windows does"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by DasCrushinator on 2007-09-12
I installed Ubuntu 7.04 on my dad's laptop, a Dell Latitude D600, but we immediately noticed it runs hotter while running Ubuntu than Windows.  I check the idle CPU speed on both Windows and Ubuntu and noticed that while the laptop was idle on Windows, the processor runs at 221MHz, while idle in Ubuntu, it runs at 600MHz.

This may not seem like such a big deal but we noticed the battery drains slightly faster, but more importantly, the laptop runs quite a bit hotter.

Does anyone know of a solution for this?

---

### Post by frith on 2007-09-12
Is it throttling at all? In my default installation I had to manually add the utils to scale the cpu - it was the toshutils package in my case, but I think cpufreqd is a more generic version.

If it is throttling, but not enough, I'm pretty confident there would be a setting somewhere you can change (even if its in the source code and you have to recompile :))

---

### Post by DasCrushinator on 2007-09-13
> **frith said:**
> Is it throttling at all? In my default installation I had to manually add the utils to scale the cpu - it was the toshutils package in my case, but I think cpufreqd is a more generic version.

If it is throttling, but not enough, I'm pretty confident there would be a setting somewhere you can change (even if its in the source code and you have to recompile :))

If i remember correctly, I added the CPU frequency scaling applet to his computer to test and it was scaling.  I wouldn't be opposed at all to something like what you suggested, I just wish I knew what that file or utility is. :(

---

