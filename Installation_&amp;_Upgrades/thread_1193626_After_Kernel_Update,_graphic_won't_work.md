---
title: "After Kernel Update, graphic won't work"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by Marzipan1 on 2009-06-21
I don't know how to describe my problem the best, but i will try to give as accurate information as i can.

Okay, so i updated the kernel (using the autoamtic update function). After that was done, i restarted the system, just to find out that somehow the graphic wouldn't work anymore. So i booted with the minimal graphics, and tried to figure out what the problem is.

My first way was to the find driver section of ubuntu itself, well there it found one, but it didn't work.
I searched a bit throw google, and found out that i need to update it per hand, but i got no idea how todo so.

So can you help me?

---

### Post by vegetarianshrimp on 2009-06-21
I suggest just using the old kernel. Restart your computer, and when you see a coundown (3...2...1), press ESC before it gets to zero. This is the grub menu, where you can boot different OSes/kernels. You will see a list of kernels. Using the arrow keys and spacebar, select the third one down. You will then boot using an old kernel. Through there, everything will be normal, and you can install whatever you need to get the newer kernel working.

---

### Post by Gen2ly on 2009-06-21
Reinstall your graphics driver.  The graphic driver gets attached to the kernel so it needs to be added again.

---

