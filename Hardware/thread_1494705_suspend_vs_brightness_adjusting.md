---
title: "suspend vs brightness adjusting"
date: 2010-05-27
forum: Hardware
---

### Post by Sonador on 2010-05-27
Hi,
i have installed 10.04 (64bit) recently on a notebook acer extensa with graphic intel gma 4500. After default install there is not working brightness adjusting, it can be fixed by adding "nomodeset acpi_backlight=vendor" in grub; it worked so without problem on 9.10 ubuntu, but now in 10.04 adding that words in grub breaks the suspend (it will suspend but when resume from suspend, there is only black screen). Without the "nomodeset..." suspend works good, but brightness adjusting dont work. :confused:

Any suggestions, how to make functional both suspend and brightness adjusting at the same time?

---

### Post by Sonador on 2010-06-04
any solution?

by the way - i have found in another thread: when the notebook is about to come back from suspend and there is only the black screen - push alt+F7 - that works fine but the process vbetool is consuming 99% of CPU, i can kill it (it causes a log off an user, so i log in back); but if i suspend another time and resume-there is the black screen, but this time alt+F7 doesnt help. Sadly, the solution is always so near but i cant never reach it :(

---

### Post by Sonador on 2010-07-20
Finally solution, leaving the grub as default (without the nomodeset acpi...) so the suspend works.

And for the brightness I found nice workaround: [http://www.winmoor.nl/Samsung-R519-Display-Brightness.html](http://www.winmoor.nl/Samsung-R519-Display-Brightness.html), moreover I edited sudoers file (just add path to the scripts and NOPASSWD...), so password is not required.

---

