---
title: "Random shutoff: cooling problem?"
date: 2008-07-18
forum: Hardware
---

### Post by treeofdeath on 2008-07-18
Yesterday I installed Xubuntu  on my Toshibalaptop. I decided that after four years, WinXP was going to slow and simply would not meet my performance demands. It worked fine yesterday.
Today, however, it decides at random intervals to shut off entirely. It doesn't begin closing processes and shutting down- it just immediately snaps off. I've never had that problem until today, even with WinXP. The laptop does not overheat easily, but that's the only possible cause that I can gather because almost everything else activates a shut down sequence or shows an error message or *something*. Generally, I can only get on for about 2 minutes, enough to startup and login and then maybe enter a terminal command or two before it shuts off. I have noticed that the fan doesn't turn on at all in the time between turning it on (at wihch point the fan turns on high for about two seconds, as always) and when it shuts itself off. I have difficulty believing its a dust problem, because wouldn't the fan at least make an attempt to activate? The CPU is no higher than is generally expected during booting and login times, which, gratefully, is very low anyway.
Is there anyway to force the fan on or at least check if it works with a command? I've heard of a few other problems with Celeron M processors and Toshiba's apparently degenerate ACPI.

---

### Post by treeofdeath on 2008-07-26
bump

---

### Post by sdennie on 2008-07-26
As you've said, a number of Toshiba laptops have problems like because of ACPI problems.  One possible way to fix the problem would be to boot with "acpi=off".  When the machine starts, hit escape when grub does the countdown and then hit 'e', scroll to the line that starts "kernel" and then hit 'e' again.  At the end of the line add:

```

acpi=off

```

Hit enter and then 'b' to start.  That may help but, it may disable some useful features features of your laptop.  If that's the case, you may have to fix the laptop DSDT.  You can find information (possibly even for your specific machine) on how to do that via google

---

