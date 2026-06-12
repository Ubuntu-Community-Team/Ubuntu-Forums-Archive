---
title: "[SOLVED] nVIDIA EVGA e-GeForce FX 5200"
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by sdlynx on 2008-02-12
I recently purchased and installed an nVIDIA EVGA e-GeForce FX 5200 into my Windows/Linux Dual-Boot computer.  It works fine with Windows, but on Linux I get the Ubuntu loading screen (orange bar) and then the monitor just turns off... I can tell the computer is still running but the monitor isn't... I know that this monitor is working because right now I'm writing this post on it.  Also, my Linux used to work on this same monitor.

At the start of GRUB I can pick from Ubuntu, Ubuntu Recovery, Memtest, and Windows XP (if that helps).

Does anybody know how I can solve this dilemma?

---

### Post by overdrank on 2008-02-13
> **sdlynx said:**
> I recently purchased and installed an nVIDIA EVGA e-GeForce FX 5200 into my Windows/Linux Dual-Boot computer.  It works fine with Windows, but on Linux I get the Ubuntu loading screen (orange bar) and then the monitor just turns off... I can tell the computer is still running but the monitor isn't... I know that this monitor is working because right now I'm writing this post on it.  Also, my Linux used to work on this same monitor.

At the start of GRUB I can pick from Ubuntu, Ubuntu Recovery, Memtest, and Windows XP (if that helps).

Does anybody know how I can solve this dilemma?

HI and welcome, what was the model of the graphics card you replace with the nvidia 5200 and did you uninstall the drivers first? You can try and boot into recovery mode which is usually the second choice in the grub. Then reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then use the command ```
reboot
``` hopefully this will get you to a GUI, Desktop. Good luck.

---

### Post by sdlynx on 2008-02-13
> **overdrank said:**
> HI and welcome, what was the model of the graphics card you replace with the nvidia 5200 and did you uninstall the drivers first?

My old graphics card was an ATI RAGE 128 PRO Ultra GL (you can imagine why I wanted to replace it it had like 16 or 24 MB memory).  Now I am kind of new to Linux I mostly use Windows but I do enjoy Linux.  Exactly how do I uninstall drivers on Linux?

Also, one of my contacts told me that reinstalling the X Window System might work.  Should I give this a try?

---

### Post by sdlynx on 2008-02-13
Wait that is exactly what that command is isn't it, to reconfigure X-Window System?  I should have realized that.

---

### Post by sdlynx on 2008-02-13
Yes thank you so much I have logged into Linux and so far everything is working fine!!!!:D

---

### Post by overdrank on 2008-02-13
> **sdlynx said:**
> Yes thank you so much I have logged into Linux and so far everything is working fine!!!!:D

Congrats and good luck! :popcorn:

---

