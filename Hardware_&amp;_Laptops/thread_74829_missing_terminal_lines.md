---
title: "missing terminal lines?"
date: 2005-10-12
forum: Hardware &amp; Laptops
---

### Post by rwalrus on 2005-10-12
Recently installed Hoary on my Averatec 3250; and I notice something odd:  in a terminal (be it the framebuffer during boot or a regular virt. terminal), the bottom 3-4 lines are missing, in that they scroll past the screen.  i.e. I display a large text file, and can't see the last few lines or the command prompt.  The graphics card is a Via Unichrome, which I know is stupid buggy and problematic, but this seems odd, and I've never encountered it before.

Any thoughts?  I'd be happy to post a config file or two, but I can't think which ones would be relavent.

---

### Post by ubuntumaneh on 2005-10-12
This may sound very dumb, for it is not the best of the solutions. Anyway, I installed Ubuntu in a Toshiba satellite 2100cds, and video card is a s3 virge. I had the same problem that you are describing. The fake solution was to go for a different driver (it is running very good with vesa). So try this:

$ sudo dpkg-reconfigure xserver-sorg

and go for the configuration. Try and error different video cards. 

Good luck!

---

### Post by ubuntumaneh on 2005-10-12
sorry:

$ sudo dpkg-reconfigure xserver-xorg

---

### Post by rwalrus on 2005-10-12
Gave it a try, we'll see what happens.  My only quibble is that the problem is not in X...only in a virtual terminal or during boot.  Thanks, though.

---

### Post by ubuntumaneh on 2005-10-12
When during the boot does the problem with the lines begin? Is it possible to be a hardware problem?

---

### Post by rwalrus on 2005-10-12
[QUOTE=ubuntumaneh]When during the boot does the problem with the lines begin?[/QUOTE]
It seems to begin just as soon as the initrd loads, framebuffer splash or not.  My best guess is that the kernel is trying to be clever with my graphics hardware, i.e. using a specific driver rather than just generic "vesa" or some such.

[QUOTE=ubuntumaneh]Is it possible to be a hardware problem?[/QUOTE]  I don't think so.  I've never experienced this before; the laptop has had both windows and gentoo on it at various times.  That being said, it might be a *driver* problem, the graphics hardware is kinda funky.  Like I said above, I'm betting that the kernel is loading a specific driver for the console framebuffer device.

---

