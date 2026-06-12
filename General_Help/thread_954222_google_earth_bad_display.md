---
title: "google earth bad display"
date: 2008-10-21
forum: General Help
---

### Post by jithin1987 on 2008-10-21
I installed google earth 4.2 on kubuntu 8.10. It giving bad display. Please see my attachment.
How do I fix this?

---

### Post by arda on 2008-10-21
What graphics card do you have? Have you installed the proprietary drivers?
Arda

---

### Post by jithin1987 on 2008-10-21
I use hp compaq 6910p laptop. which has integrated intel graphics chipset. How do I figure out the exact chip number and all?

---

### Post by erlguta on 2008-11-21
> **jithin1987 said:**
> I use hp compaq 6910p laptop. which has integrated intel graphics chipset. How do I figure out the exact chip number and all?

I have the same problem with:
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

ATI does not work (blinking in 3D applications)
Intel have problems too..
Only nvidia?

Come on linux! in this way it is VERY difficult to solve the nº 1 bug in launchpad

---

### Post by Junk_head on 2008-11-21
Do you have compiz effects/desktop effects enabled? Google Earth and Compiz don't mix for some strange reason, I usually disable them when I open up Google Earth and problem solved.

---

### Post by erlguta on 2008-11-22
> **Junk_head said:**
> Do you have compiz effects/desktop effects enabled? Google Earth and Compiz don't mix for some strange reason, I usually disable them when I open up Google Earth and problem solved.

Yes!.
If i disable compiz, Google Earth displays OK.
is a bit annoying to disable it all the time. 
Why is this happening? 
Should i report a bug?

---

### Post by jithin1987 on 2008-11-23
Its the limitation of X server. It cannot hanlde two open gl application together.

[http://forum.kde.org/showthread.php?tid=11227](http://forum.kde.org/showthread.php?tid=11227)

---

### Post by erlguta on 2008-11-24
> **jithin1987 said:**
> Its the limitation of X server. It cannot hanlde two open gl application together.

[http://forum.kde.org/showthread.php?tid=11227](http://forum.kde.org/showthread.php?tid=11227)

mmm, some of light.
Thank you.

---

