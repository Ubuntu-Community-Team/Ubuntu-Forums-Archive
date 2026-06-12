---
title: "cli console is distorted on Acer Aspire 3002WLC"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by russelld on 2005-10-23
The console (Crtl+Alt+F1) and boot screen is distorted where the top is a bit cut of the bottom.
see the photos:
[http://home.exetel.com.au/randombits/AcerAspire3002WLC/]("http://home.exetel.com.au/randombits/AcerAspire3002WLC/")

your help is appreciated!

---

### Post by jobezone on 2005-12-13
I have an Aspire 3003LMi, and the bottom part of the graphical boot and the virtual terminal is off-screen (cut off).
Your problem is a slightly simillar situation. I think that the way to solve this would be to use a different resolution for the console and splash screen through the framebuffer driver. I loaded mine (module named sisfb ), but it isn't instantly being used (unlike in debian testing, where just by loading that module, after boot the vt's and text boot screen used a bigger resolution, sucessfully showing all the text on the screen).

---

### Post by fergus.b on 2005-12-15
[QUOTE=jobezone]I have an Aspire 3003LMi, and the bottom part of the graphical boot and the virtual terminal is off-screen (cut off).[/QUOTE]
I have this problem too and I'm busy hunting for a solution. Let me know if you find anything (and vise-versa). Thanks!

---

### Post by fergus.b on 2005-12-15
jobezone have a look at [this post](http://ubuntuforums.org/showpost.php?p=576863&postcount=2) by silex to see how to fix this problem. By adding 'vga=792' to my kernel line in /boot/grub/menu.lst I was able to get the virtual terminal fit on the screen and the resolution is much better now and allows more text to be displayed at once.

---

### Post by ranf on 2005-12-15
I don't have an Acer. But I also had lines off-screen. Removing the "splash" option from the kernel parameters helped.
I don't need a graphical splash screen if it breaks usability of tty1.

---

### Post by jobezone on 2005-12-15
Thanks a lot, this will help me a lot!

---

