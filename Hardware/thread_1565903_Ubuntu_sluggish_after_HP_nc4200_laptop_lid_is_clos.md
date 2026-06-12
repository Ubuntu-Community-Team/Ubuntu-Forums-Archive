---
title: "Ubuntu sluggish after HP nc4200 laptop lid is closed"
date: 2010-09-01
forum: Hardware
---

### Post by solidsnake204 on 2010-09-01
I have a HP Compaq nc4200 laptop with Windows XP and Ubuntu 10.04 installed.

Ubuntu works fine (Except for suspending and hibernating) on the laptop until I shut the lid. When I open the lid again every few seconds the laptop freezes.

When I go into the log viewer, this is printed in the Xorg.0.log every time the laptop freezes:

```
(II) PM Event received: Capability Changed
I830PMEvent: Capability change
(II) intel(0): EDID vendor "CMO", prod id 4612
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)

```

Sometimes, I get these lines too:
```
AT Translated Set 2 keyboard: dropping event due to full queue!
AT Translated Set 2 keyboard: dropping event due to full queue!
```

I am running Ubuntu 10.04 with Linux kernel 2.6.32-24.

The laptop has an Intel 915GM Chipset with GMA 900 graphics.

The problem is fixed when I install LXDM and use that as my display manager, but then I lose the shutdown option in the menu.

---

