---
title: "Problems with GNOME 2.32.0"
date: 2011-04-17
forum: Hardware
---

### Post by Marcelo Ruiz on 2011-04-17
Hi, I have two problems with GNome 2.32.0 that are driving me crazy (especially the second one).

I have a Toshiba Qosmio X500-Q895S with a Core I7, discrete nvidia 1GB, and 8Gb RAM running Ubuntu Maverick x64 (2.6.35-28-generic).

Maybe someone can tell me how to fix them:

1 - At login, right after entering my password, the transition from gdm to gnome is really slow (the desktop gets fully loaded after more than 30 secs and even after doing so the hard drive activity is really high for another 30 secs). In some forums I read this is related to gnome trying to find a floppy disk and that it should be solved by disabling the floppy from the BIOS. The problem is that my laptop does not have a floppy nor any option in the BIOS related to floppy discs.

2 - When I restart, I used to see the ubuntu splash screen (the same you see when loading with Ubuntu and the moving dots) and now I see a completely red screen and the computer freezes (so it never shutdowns properly).

I am wondering if anyone is experiencing this problems (especially the second one).
Thanks!

---

### Post by Marcelo Ruiz on 2011-04-18
Well, heads up with problem #2: It seems to be an NVidia driver problem (a regression). I downgraded the driver to version 260.19.06 and it seems to work fine.
Problem #1 is still there. Any ideas on how to solve it will be appreciated! :)

---

