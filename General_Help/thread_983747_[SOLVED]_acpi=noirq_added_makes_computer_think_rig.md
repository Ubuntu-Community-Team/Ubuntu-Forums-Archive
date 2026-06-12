---
title: "[SOLVED] acpi=noirq added makes computer think right key is held down."
date: 2008-11-16
forum: General Help
---

### Post by knux56k on 2008-11-16
Hello,

I had been experiencing the problem with intrepid where it won't boot unless a key is being held down, so I decided I would look up some fixes for it.  I came across one that involved adding "acpi=noirq" to my menu.lst file.  This solved the problem, but now when the computer gets done booting, it thinks the right arrow key is being held down.  If I boot into Windows, it also does the same thing.  After many tries, I finally got back into the menu.lst file (it's very difficult when the cursor is constantly moving to the right ](*,) ) and deleted the "acpi-noirq" from the file.  The boot issue where the key has to be pressed has returned, but still the computer thinks the right arrow key is being held down...  Any help would be greatly appreciated!!

---

### Post by lovinglinux on 2008-11-16
Have you considered the possibility of the key being physically held down without knowing? This happens sometimes in my filthy keyboard.

I'm asking this because it is really unlikely that the same issue appears on Ubuntu and Windows if it is not physically related.

---

### Post by CatKiller on 2008-11-16
> **knux56k said:**
> If I boot into Windows, it also does the same thing.

Then it's just coincidence that it happened at the same time. Your Linux kernel options won't affect Windows in any way.

See if the key is stuck down, and give your keyboard a clean.

---

### Post by knux56k on 2008-11-17
After trying a few different kernel boot parameters last night, it still wasn't working, but when I woke up this morning it magically started working!  I'm guessing the key probably was stuck or something, which is weird because this laptop is fairly new...but who knows.  Thanks for the input!

---

