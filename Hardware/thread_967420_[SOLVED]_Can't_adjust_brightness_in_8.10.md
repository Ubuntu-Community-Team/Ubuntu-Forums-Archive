---
title: "[SOLVED] Can't adjust brightness in 8.10"
date: 2008-11-02
forum: Hardware
---

### Post by klausner on 2008-11-02
I have a Sony Vaio VGN-Z530N with the Nvidia 9300M graphics. I can't get the screen brightness to adjust. Tried the hardware buttons (Fn-F5), spicctrl, xbacklight, and the panel brightness applet. None work. This is with 8.10, Intrepid Ibex.

Suggestions?

---

### Post by iRPM on 2008-11-02
Hi!

I had the same problem, here, how I have managed it:

```

sudo apt-get install linux-backports-modules-2.6.27-7-generic

```


:)

---

### Post by klausner on 2008-11-02
> **iRPM said:**
> Hi!

I had the same problem, here, how I have managed it:

```

sudo apt-get install linux-backports-modules-2.6.27-7-generic

```


:)

I'll show my ignorance: If the current kernel with 8.01 is 2.6.27-4, how is 2.6.27-7 a backport? ;)

---

### Post by klausner on 2008-11-02
> **iRPM said:**
> Hi!

I had the same problem, here, how I have managed it:

```

sudo apt-get install linux-backports-modules-2.6.27-7-generic

```
:)

Tried this, but 27-7 won't boot. Hangs with the gui progress bar about 1/3 of the way through.
:(

---

### Post by klausner on 2008-11-04
Bump

---

### Post by klausner on 2008-11-05
> **klausner said:**
> Tried this, but 27-7 won't boot. Hangs with the gui progress bar about 1/3 of the way through.
:(

OK. The latest set of patches last night solved the problem of hanging during the boot. But I still can't control the screen brightness, even with 27-7 booted. :icon_frown:

---

### Post by saresca on 2008-11-13
I hope this work for you.

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6167330#post6167330](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6167330#post6167330)

---

### Post by klausner on 2008-12-01
> **saresca said:**
> I hope this work for you.

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6167330#post6167330](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6167330#post6167330)

If you had read the original post, you'd see I already tried xbacklight, and it doesn't work!

---

### Post by klausner on 2008-12-12
Anyone have a solution for this that works on the Vaio?

---

### Post by Ecologger on 2008-12-12
you can try setting the acpi like so,
setpci -s 00:02.0 F4.B=FF in terminal
the last 2 numbers are hex and 00 would be black, FF is full brightness. 
Not my idea, check [http://ubuntuforums.org/showthread.php?t=881127&page=6]("http://ubuntuforums.org/showthread.php?t=881127&page=6")
However, the ultimate solution, for now anyways, is to set back the kernal to a version where the brightness controls worked. 
Good Luck.

---

### Post by jaikenone on 2008-12-16
i have the same exact same model with 8.10, i handle the brightness problem by run "xrandr --output LVDS --set BACKLIGHT_CONTROL legacy" and using the Power Manager Brightness Applet.

Still not working:
build in mic
brightness buttons
video out button
headphone jack works but doesn't turn off speakers

---

### Post by klausner on 2008-12-19
> **jaikenone said:**
> i have the same exact same model with 8.10, i handle the brightness problem by run "xrandr --output LVDS --set BACKLIGHT_CONTROL legacy" and using the Power Manager Brightness Applet.


That does seem to work, though not with the 27-7 kernel. I added it to my .profile, and got it to work initially with 27-4.

But 27-4 (and several other pre-27-7 kernels) had a different problem with frequent hangs while booting. I'm writing this using 27-11, which seems to support the xandr fix, and so far hasn't hung on boot.

Thanks.

---

