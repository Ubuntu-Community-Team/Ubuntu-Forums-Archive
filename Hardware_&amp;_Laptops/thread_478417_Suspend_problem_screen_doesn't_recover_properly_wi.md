---
title: "Suspend problem: screen doesn't recover properly with Feisty on ThinkPad T60p"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by wanorris on 2007-06-19
Hi! I have a ThinkPad T60p running a fully-updated installation of Feisty. I believe it has an ATI Mobility FireGL V5200 graphics adapter with 256 MB, but it might be the V5250 rev. It shows up in lspci as "ATI Technologies Inc Unknown device 71d4".

When I suspend the system, everything seems to work fine.

However, when I try to turn it back on, it doesn't work properly. Everything seems to come back on, and the screen backlight kicks on like everything is working, but the screen never changes from solid black, so I can't log back in and use the system. I've tried using the mouse and any key combinations I could think of, but nothing seems to make the screen come back on.

Any ideas?

Thanks in advance,

Andy

---

### Post by frigaut on 2007-06-19
I have a intel graphic card 950GM, on a T60, so it might be a completely different problem, but you could try passing acpi_sleep=s3_bios,s3_mode to your kernel parameters.

Or dig up the web deeper, I'm sure you'll find an answer there (did you try thinkwiki.org?)

---

### Post by Vitus on 2007-06-20
> any key combinations I could think of

Does this include switching to the console (Ctrl-Alt-F1)?  This did the trick for me.  And can afterwards configured to happen automatically.

---

