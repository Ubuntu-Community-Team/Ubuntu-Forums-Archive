---
title: "Intermittent USB mouse problem"
date: 2005-02-15
forum: Hardware &amp; Laptops
---

### Post by prospectofdeath on 2005-02-15
I've got a small USB mouse problem.

I've got a Logitech MX700 USB mouse plugged into my computer and it works fine under all the other operating systems I've had installed on this computer (XP, Win2k, FC1-3, Slackware 10) but I've got an inconsistent problem with Ubuntu (Warty). Roughly 1 out of 5 times booting into Ubuntu (it's a dual boot with Win2k) the mouse won't work at all. I can't find any control panels or scripts that will attempt to re-'find' the mouse so I'm left to reboot the system.

I've tried using the scientific method to determine the problem but there doesn't seem to be a pattern. Sometimes it happens on a 'cold boot', sometimes it happens when I've been rebooting from Win2k to Ubuntu. It has *always* corrected itself after a clean reboot.

I'm also using a Logitech USB keyboard and haven't had any problems with that.

When I installed Ubuntu it didn't give me any trouble with my mouse so I've left my XF86Config-4 alone.

Here's the mouse section for reference (although it seems to be the standard settings):

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection
```

Thoughts?

---

