---
title: "Thinkpad T43P and Ubuntu 8.10"
date: 2009-03-11
forum: Hardware
---

### Post by dmakfan on 2009-03-11
Hello,

Just thought I'd quickly post my experience in getting my t43p thinkpad and Ubuntu 8.10 "working".  I really only ran into two issues where I had to do anything out of the ordinary (for someone who doesn't want to muck around too much).

1.  I had to go into /boot/grub/menu.lst and add "nohpet" (without quotes) to the kernel line.  It seems that without this, my machine would periodically hang.  Searching around on the net eventually seemed to indicate that the problem was with the hw watchdog, and that this shows up as a non maskable interrupt (NMI) error in the system logs.

2.  When trying to install the restricted ATI drivers from System->Administrator->Restricted Hardware Drivers, clicking the "Activate" button brought up the little dialog that said it was installing, but then it seemed to fail silently.  The driver was not activated, and no error was given.  I went into the Synaptics Package Manager, and searched for "fglrx", and just installed a bunch of those (I can't remember which ones off the top of my head :) ), and then after having done that, I went back into System->Administrator->Restricted HW Drivers, and clicking on the "Activate" button worked and the UI showed that I needed to reboot my machine for things to take effect.  I haven't fully tested it out, and I have seen a few little glitches in the rendering (like when hitting ctrl-alt-cursor to switch between desktops, it doesn't draw that overlay properly anymore), but for the most part, it seems to be working.

I'm also not sure but suspend may not be working properly anymore after #2.  It was working before I switched the driver, though when it came back, my windows sometimes had a thicker border around them :)  I'll do more tests when I get a chance.

Cheers!

---

