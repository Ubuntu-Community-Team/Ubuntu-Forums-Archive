---
title: "Acer Aspire V5-122P cannot adjust brightness"
date: 2014-06-06
forum: Hardware
---

### Post by jack980517 on 2014-06-06
Hi everyone,
I installed Ubuntu GNOME 14.04 LTS recently (but installed ubuntu-desktop so I'm using Unity) and found that I cannot adjust brightness using the Fn+Left/Right keys. I tried adding acpi_osi=Linux and acpi_backlight=vendor, but this made the OSD disappear completely. The default screen brightness is too high, and it's causing image retention on the screen even when I just used the computer for about half an hour (this will usually happen when an area on the screen continuously displays the same image/color for a long time). I'm worrying that the screen might overwork. I installed the driver from AMD official website (the graphic card is Radeon HD 8250) but the situation is still the same.
I found some solution about adjusting brightness with terminal commands. I haven't tested them yet, because I don't want them. I want the Fn+Left/Right keys to be working.
Please help! Thanks!

---

### Post by Toz on 2014-06-06
This is a known bug. These bug reports may be useful to follow or get involved with:
- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1315834]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1315834")
- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1322004]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1322004")

---

