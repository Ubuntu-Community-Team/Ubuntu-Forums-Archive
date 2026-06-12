---
title: "Various problems with wubi and live cd."
date: 2008-08-26
forum: General Help
---

### Post by Iku Tri on 2008-08-26
Hi, I have been having some problems with wubi and the cd.

I installed different variants of ubuntu through wubi [Tryed it again, over time], and I got it to start once, then on a reboot it [all of them] would not fully start, and to go to a black screen to what seems a text based boot.

Later, back in Vista, I uninstall wubi. I say no backup. When I start my computer, the boot menu shows up. The option is still there. I try again later, with a different type, and it just does the same thing...I uninstall it, same thing. Now there are four ones there, including vista.

Later on, recently, I swap drives to a fresh one, used once in a failed boot in a different computer, [To troubleshoot it] and when I boot from the cd I burned, it gets to the menu. I try the live cd option, and the same thing. It went to a text based boot.

Is my drive messed up? Is this fixable?

---

### Post by phidia on 2008-08-26
When the screen drops to the commandline rather then a GUI it usually means the installer/live cd is having a problem identifing your graphics card.
You can try the command > sudo dpkg-reconfigure -phigh xserver-xorg and see if that gets you your desktop.
If that's not the problem then you will need to provide more of the messages you are seeing.

---

### Post by Iku Tri on 2008-08-27
Ok, I will try that, and see if it works. Would installing new drivers for the gfx card help as well??

---

