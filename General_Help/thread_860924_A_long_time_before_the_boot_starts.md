---
title: "A long time before the boot starts"
date: 2008-07-16
forum: General Help
---

### Post by noamr on 2008-07-16
Hello,

When my computer boots, after the GRUB menu exits, there are about 60 seconds when I have a splash screen with an orange rectangle going back and forth. Only after this long minute my screen goes to text mode, writes "Reading files needed to boot", and starts doing useful things.

I have an IBM X40 laptop, running Hardy.

Can you suggest ways to find what is actually going on in this minute, or how to make it go away?

Thanks a lot,
Noam

---

### Post by dcstar on 2008-07-16
> **noamr said:**
> Hello,

When my computer boots, after the GRUB menu exits, there are about 60 seconds when I have a splash screen with an orange rectangle going back and forth. Only after this long minute my screen goes to text mode, writes "Reading files needed to boot", and starts doing useful things.
.......

Probably a timeout waiting for some hardware to respond. You can press CTRL-ALT-F1 or CTRL-ALT-F10 during boot to see the text boot progress.

Do a forum search for your hardware to see if this problem has a solution.

---

### Post by noamr on 2008-07-16
Thanks for your reply! I pressed Ctrl+Alt+F1 during boot, and there was only a message from usplash at the beginning, and then nothing until "reading files needed to boot" a minute later.

Is there a way to get a log which will list what my computer is waiting for?

---

