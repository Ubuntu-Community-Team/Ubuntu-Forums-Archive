---
title: "Changing Video Cards, Kernel panic, Bug: Bad page map in process swapper"
date: 2010-10-16
forum: Hardware
---

### Post by edgardol on 2010-10-16
Hi,
Thanks in advance for any help/clue/suggestion !

I'm using 10.04 on a Desktop.
I changed the video card from an NVidia GeForce FX5600 to an NVidia Quadro4 FX2000 AGP 8X 128 MB. (To be able to use two monitors.)

When the computer starts, after saying that it doesn't find a boot record on a CD (as expected), and saying that it finds it in a hard disk drive (HD0), the screen goes blank, then a flashing cursor shows up on the upper left, and then ... this message is displayed a few times:
BUG: Bad page map in process swapper pte:ffffffff pmd:c64ff067 addr:bffffff6 vm_flags:00100173 anon_vma:(null) mapping:(null) index:bffff
Followed by this message:
Kernel panic - not syncing: No init found. Try passing init=option in Kernel

The machine works fine when changing back to the previous video card. I haven't been able to confirm that the video card works well on another machine yet, but I'll be looking for a place to do that.

Any clue ? Any suggestion ?

Thanks,
Edgardo.

---

