---
title: "kernel parameter vga=031b not working first time round"
date: 2005-01-13
forum: Hardware &amp; Laptops
---

### Post by gnutered on 2005-01-13
I like changing the screen resolution during bootup.  My Compaq Evo N800w is 1600x1200, which should be vga mode 031b.

Putting 'vga=031b' on the kernel line for grub causes it to fail, and prompts me to scan for modes, or just boot with the default mode.  Doing a scan returns a list of 0F** modes.

The funny thing is, after scanning, I can enter mode 031b and she works fine.

Any clues as to what I can do to get my nice bootup?

Tony Lewis

---

### Post by jdong on 2005-01-13
031b is a Hexadecimal value. You must specify it as either **vga=0x31b**, or **vga=795** (Decimal conversion)

---

### Post by gnutered on 2005-01-13
[QUOTE=jdong]031b is a Hexadecimal value. You must specify it as either **vga=0x31b**, or **vga=795** (Decimal conversion)[/QUOTE]

I tried that originally = 0x31f and 0x31b, but no joy.  Also, after a scan, 031b works (as opposed to 0**x** 31b

I did try some decimal numbers, not sure if I did 795.

I'll give it a go at next boot, but I'm not convince that the hex thing is the problem.

Thanks,

Tony

---

### Post by gnutered on 2005-01-16
[QUOTE=gnutered]I tried that originally = 0x31f and 0x31b, but no joy[/QUOTE]

Actually, I tried "vga=031b" again, editting the GRUB boot parameters and she worked fine.  I *thought*  I'd tried it, honest.

Tony

---

