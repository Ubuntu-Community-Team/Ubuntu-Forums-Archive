---
title: "Power saving script vs. laptop-mode conf, which is better ?"
date: 2009-05-11
forum: Hardware
---

### Post by Axx83 on 2009-05-11
Last week I was struggling with a power saving script to make this laptop (thinkpad x60s) last a little longer.

I used something like this: [xps power savings]("http://ubuntuforums.org/showthread.php?t=847773") plus something to turn autosuspend when on battery, plus some modifications.

These script did teir work but I had a few problems with suspend.

The other day I found out that laptop-mode has a directory where you can modify a couple of config files and let it do everything in auto. So I turned laptop mode on, modifying both /etc/default/acpi-support & /etc/laptop-mode/laptop-mode.conf and tuned all these conf files a bit.

Now I have hard drive management, wireless, usb and all that tuned by laptop-mode. Watt consumption on powertop is the same as before but no more problems with suspend.

Then...why do I see NO ONE making a guide about laptop-mode on this forum while I see tens of power saving scripts ?

Is there a bug with laptop-mode that I don't know of ?

---

