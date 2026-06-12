---
title: "[SOLVED] Toshiba Satellite M45-S165 hangs on boot"
date: 2008-10-26
forum: Hardware
---

### Post by DoubleMcLovin on 2008-10-26
So I managed to get my laptop to install Ubuntu 8.04.1 by running the parameters "noapci nolacpi vga=771" and using the alternative install disk.

However, after the install I go to boot the OS only to be greeted by 1 of several things, half the background loading properly and the top half being black, bottom half of screen being a checkerboard of white and black rectangles and top half black, or static on the bottom and the top half black. All of these followed by the system hanging if I don't get to tty1 fast.

The latop does have an ATI graphics card onbord, and when I go to tty1 I was able to run "sudo nano /etc/X11/xorg.conf" and found that the area that describes my video driver only reads as:

```
Section "Device"
        Identifier        "Configured Video Decice"
EndSection
```

I tried appending it as

```
Section "Device"
        Identifier        "Configured Video Decice"
        Driver        "ati"
EndSection
```

But that did nothing. Any suggestions?

[COLOR="Red"]EDIT: SOLVED[/COLOR]
nevermind...

immediately after posting this, I wondered if "vesa" would do better then ati for a driver.... it did....

For anyone with the same problem as me, change

```
Section "Device"
        Identifier        "Configured Video Decice"
EndSection
```

to


```
Section "Device"
        Identifier        "Configured Video Decice"
        Driver            "vesa"
EndSection
```

and problem solved.
tags: Toshiba satellite M45-S165 video display error hang on boot no startx

---

