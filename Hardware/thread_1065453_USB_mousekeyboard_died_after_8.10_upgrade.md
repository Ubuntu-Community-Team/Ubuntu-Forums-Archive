---
title: "USB mouse/keyboard died after 8.10 upgrade"
date: 2009-02-09
forum: Hardware
---

### Post by whitej125 on 2009-02-09
I just recently upgraded from Hardy to Intrepid... now, when I boot my Dell 400SC USB devices don't seem to work (namely MS Intelimouse and MS keyboard).

It seemed at first that it was a hardware issue, neither device appeared to be getting power (red mouse light wasn't on).  Then I modded /boot/grub/menu.lst

# defoptions=quiet splash acpi=force irqpoll

[http://ubuntuforums.org/showthread.php?t=854684](http://ubuntuforums.org/showthread.php?t=854684)

The mouse now lights up, but still is not responsive in the desktop.

Thoughts?

---

### Post by whitej125 on 2009-02-09
One more thing... I had intrepid working for a week or so (X and all).  I wonder if a recent update hosed something?

---

