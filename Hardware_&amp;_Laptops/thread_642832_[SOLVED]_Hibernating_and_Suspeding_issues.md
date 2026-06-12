---
title: "[SOLVED] Hibernating and Suspeding issues"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by HoMie_G on 2007-12-17
heyo,

I have an ASUS g1s with UBUNTU 7.10 and XP installed. When i first got XP i had a problem hibernating. Apparently having too much RAM (2GB) causes this issue sometimes. Anyways, did a little research and downloaded a fix from Microsoft's website. When i installed UBUNTU i could not hibernate or suspend. These are the cases:

1. When i suspend, it goes through and suspends; However, when i try to wake my laptop i don't get anything on the screen, just a black screen that forces me to shut down the computer by pressing the power button. 

2. When I hibernate, it does not hibernate and i get all sorts of flashy screens and stuff. Then i get the log in pop up box as if i locked my computer. After i log in, i get a pop up saying hibernate did not go through.

I searched on the forums here but i did not find a solid way to solve this problem. Thanks in advance and my bad if there was a simple solution that i over looked :D

peace

---

### Post by d0nny2600 on 2007-12-17
It is more than likely an issue with your video card. Are you using an ATI graphics card by chance?

---

### Post by HoMie_G on 2007-12-17
No, the laptop's video card is an Nvdia Geforce 8600m GT.

---

### Post by hardyn on 2007-12-17
I had the same problem previous to gutsy, not things are working pretty well... BUT in the past the following things have worked for me:

1) disable compiz fusion.
2) add  "vga=791" to the grub boot string.  /etc/boot/grub/

---

### Post by HoMie_G on 2008-02-03
check the "hibernating/suspending" step:

[http://ubuntuforums.org/showthread.php?p=4261830#post4261830](http://ubuntuforums.org/showthread.php?p=4261830#post4261830)

---

