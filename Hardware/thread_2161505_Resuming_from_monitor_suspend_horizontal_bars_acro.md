---
title: "Resuming from monitor suspend horizontal bars across screen"
date: 2013-07-10
forum: Hardware
---

### Post by cebif on 2013-07-10
I am not sure if this is a bug with AMD proprietary drivers, xorg bug or power manager problem but resuming from monitor suspend is nearly always causing 4 thick black bars across the screen. It seems to be getting worse and more likely to happen with every update. I did think it was solved at one stage by me uninstalling Catylist drivers version 13.4, reinstalling xorg then Catylist drivers. The bug looked a bit different before I did that. It was not horizontal black bars but a very patchy corrupted display. I used to press ctrl + alt + delete and sudo top. I would use top to kill xorg. Xorg would immediately restart and I would find myself at a proper looking login screen. After logging in everything also looked fine until the next time. That could be a different bug from the one now with horizontal bars.
So does anyone have the same or know if this might be a Catylist, xorg or power manager problem? Is there any good workaround or should it be reported as a bug. I did a lot of searching in launchpad and AMD linux bug report site but have not found anything.
Video card is: Saphire  HD7850 2GB VRAM Catylist 13.4 proprietary driver
lspci:
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 6819
There is one other thing. I replaced gnome-screensaver with xscreensaver and are using the timer setting in that to turn off the monitor. All the screensavers displayed by xscreensaver are opengl. I'm not certain if I set xscreensaver to only blank the screen before turning off would the bug still happen? I might try

---

### Post by byStanderone on 2013-07-11
...it seems not a bug at all...but a graphic driver issue....am not familiar with your graphics card....but the symptoms you presented somehow points to it.

---

### Post by cebif on 2013-07-11
> **byStanderone said:**
> ...it seems not a bug at all...but a graphic driver issue....am not familiar with your graphics card....but the symptoms you presented somehow points to it.
Well it could be opengl related because with three resumes from monitor suspend using the xscreensaver blank screen, instead of displaying opengl screensavers, there has been no black bars. So AMD drivers supply opengl or opengl part concerned with hardware rendering. Is that correct?

---

### Post by cebif on 2013-07-11
> **byStanderone said:**
> ...it seems not a bug at all...but a graphic driver issue....am not familiar with your graphics card....but the symptoms you presented somehow points to it.
It might really be kernel 3.2.0-49 that I recently updated to. I went back to kernel 3.2.0-48 and re-enabled xscreensaver opengl screensavers. The horizontal bars have not happened again on resume from monitor suspend. I will test a little more with this kernel to be certain. Even if this kernel works, I think there might be another bug associated with 3.2.0-48: resuming from hibernate freezes with the caps lock and num lock flashing. It did not happen in kernel 3.2.0-24 up to about 3.2.0-39. After I have tested with 3.2.0-48 I will go back to 3.2.0-39 for testing with the hibernate resume bug.

---

### Post by cebif on 2013-07-12
It is the kernel that was causing the resume problem. It was not fixed by me going back to 3.2.0-48 but 3.2.0-39. Going back to that kernel also fixed the other bug of the hang resuming from hibernate.

---

