---
title: "Hardware-caused freeze at startup"
date: 2007-03-20
forum: Hardware &amp; Laptops
---

### Post by LJM on 2007-03-20
I'm experiencing the following problem on startup, i.e. before Ubuntu loads.

The machine freezes at different stages and only loads Ubuntu after several resetting operations. The first point at which it freezes is usually on prompting:

>Verifying DMI Pool Data...

If this hurdle is cleared successfully, it then tends to freeze on prompting:

>GRUB loading, please wait... 1 [second]

or

>GRUB loading, please wait... 0 [second].

Alternatively, it has every now and then immediately displayed the error message:

>CMOS checksum error -- Defaults loaded
>Warning! CPU has been changed.
>Please Enter CPU Speed CMOS Setup and Remember to Save before Exit!

At times, all goes well but GRUB loads as a command screen; when this happens I know no better than to type "reboot" from there.

Finally, on rare occasions, it prompts:

>Activating swap...
>Checking root file system...
>fsck 1.39 (29-May-2006)
>/dev/hda1 has been mounted 30 times without being checked, check forced.
>checking /dev/hda1..................... etc.

Does any of this make any sense? Any clues? Thanks in advance!

---

