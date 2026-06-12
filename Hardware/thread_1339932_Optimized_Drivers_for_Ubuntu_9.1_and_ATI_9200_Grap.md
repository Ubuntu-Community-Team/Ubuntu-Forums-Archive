---
title: "Optimized Drivers for Ubuntu 9.1 and ATI 9200 Graphics?"
date: 2009-11-28
forum: Hardware
---

### Post by SNYP40A1 on 2009-11-28
I have a ATI 9200 Graphics card.  I just installed Ubuntu 9.1.  The resolution is correct and the graphics look clear, but it's very choppy when moving windows and when a window is fully explanded (Firefox, Solitare, etc), all I see in the window is black.  There used to be restricted drivers available for Ubuntu 7.04 and my card.  Can I get better graphics in Ubuntu 9.1 without having to replace my perfectly good video card?

---

### Post by jocko on 2009-11-28
See [this thread]("http://ubuntuforums.org/showthread.php?t=1290449"), and try my fix in post #6. It should help with the choppy behaviour, but I'm not sure if it will help with the black windows.

---

### Post by SNYP40A1 on 2009-11-28
Too bad that they dropped support for it.  The graphics are just fine under Windows XP and their latest drivers still support my card.  Why can't I just use one of their older drivers when they still supported my card?  There's about a 2 second delay whenever I try to minimize / maximize my windows.

---

### Post by jocko on 2009-11-28
The only way to use the older driver is if you downgrade to a kernel and an xorg version that was supported by that old driver. I don't think that's a very good idea, as it will probably force you to downgrade other parts of your system as well, or make your system unstable.

With the proper settings I bet the current open source driver will perform better than the three years old fglrx driver...

And: the current windows driver does not support your card either. They dropped support (in both the windows and linux driver) for anything older than radeon 9500 three years ago, and anything older than radeon hd2xxx this spring. But maybe they still package the legacy driver in the windows installer (that's possible in windows XP, as the kernel and whatever corresponds to the xserver is still the same)...

---

### Post by SNYP40A1 on 2009-11-28
> **jocko said:**
> The only way to use the older driver is if you downgrade to a kernel and an xorg version that was supported by that old driver. I don't think that's a very good idea, as it will probably force you to downgrade other parts of your system as well, or make your system unstable.

With the proper settings I bet the current open source driver will perform better than the three years old fglrx driver...

And: the current windows driver does not support your card either. They dropped support (in both the windows and linux driver) for anything older than radeon 9500 three years ago, and anything older than radeon hd2xxx this spring. But maybe they still package the legacy driver in the windows installer (that's possible in windows XP, as the kernel and whatever corresponds to the xserver is still the same)...

Jocko, I agree.  Since WinXP has not changed, they could just repackage the drivers.  I guess it's a lot more work to maintain updated drivers for Linux for that reason.  New Xorg requires new drivers.  I'll post another thread asking for optimized 9200 SE config settings.

---

### Post by jocko on 2009-11-28
Check [this post]("http://ubuntuforums.org/showpost.php?p=8221972&postcount=6"), and [the rest of the same thread]("http://ubuntuforums.org/showthread.php?t=1308027"). It looks like it's about the same problem as you have, and there seems to be some fixes.

---

### Post by SNYP40A1 on 2009-11-28
I just rebooted my computer this morning and now it works fine.  Not sure what fixed it.  I downloaded a bunch of updates last night after the installation so it must have pulled an updated driver or settings.

I did look for the xorg.conf file and I don't see it:

```

Seattle@Boxer:/etc/X11$ ls -a
.             default-display-manager  xinit       Xsession.d
..            fonts                    xkb         Xsession.options
app-defaults  rgb.txt                  Xresources  XvMCConfig
cursors       X                        Xsession    Xwrapper.config

```

---

