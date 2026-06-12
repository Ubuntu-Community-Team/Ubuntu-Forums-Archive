---
title: "links2 -g doesn't run within screen"
date: 2008-08-24
forum: General Help
---

### Post by futonrevolutionary on 2008-08-24
Here's what I'm trying to do. I'm trying to run links2, a graphical browser that runs on the framebuffer instead of X, within screen. Here's what happens. I can set up the screen session and whatnot and then split it so I can have two screened windows side by side, but if I run sudo links2 -g in one, it goes fullscreen and ignores my screen session. I want it to run inside screen so I can run something else in the other screen session.

(By the way, in case you're wondering why I'm running links2 as root, here's the error that pops up when I don't:

       ---------------------- DirectFB v0.9.25 ---------------------
             (c) 2000-2002  convergence integrated media GmbH
             (c) 2002-2004  convergence GmbH
        -----------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2006-12-04 07:00)
(*) Direct/Memcpy: Using MMXEXT optimized memcpy()
(!) DirectFB/core/vt: Error opening `/dev/tty0'!
    --> Permission denied
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
svgalib: Cannot get I/O permissions.




I guess I should also mention that I've added vga=791 into grub as a boot option. Before that, using the framebuffer didn't work at all. Anyone had this problem? All I want is a way to run links2 in graphical mode, in splitscreen so I can multitask, and without x. It has to be possible.

---

