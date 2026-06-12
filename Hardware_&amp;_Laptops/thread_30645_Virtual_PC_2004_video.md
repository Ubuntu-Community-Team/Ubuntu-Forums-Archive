---
title: "Virtual PC 2004 video"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by gigabitfx on 2005-04-29
well i managed to installed 5.04 in virtual pc, but when it boots the gui video is distored.  i need to get into xconfig to try a couple of resolutions, but when i hit cntrl+alt+backspace it exists x windows into a terminal but then loads it right back up again do the distorted video configuration.  here are my questions.

1.  how do i boot into the console only, is there a safemode with console support hotkey?

2.  once i successfully boot into the console which program to i run to test various resolutions/video configurations.

its been awhile working with linux, and im stilla windows fan, thus im lost in all this manual configuration.

---

### Post by Juergen on 2005-04-30
Hmm, it seems they removed the howto :-(

You need to change the (default-)colordepth to 16bit.

Do the following:
When you see your distorted screen, press <ctrl>+<alt>+<f2>, this should show a virtual console.
Log in.
Type ```
sudo nano /etc/X11/xorg.conf
```and enter your password again.
Scroll down to 'Section "Screen"' and change the entry for 'DefaultDepth' from 24 to 16.
Type <ctrl>+<x> and confirm to save the changes.
Type 'logout'.
Press <alt>+<f7> to get back to your graphical login.
Press <ctrl>+<alt>+<backspace>, this should restart X11 with the correct colordepth - if not, reboot.

---

### Post by VstarAl on 2005-10-16
Your instructions worked like a champ.

Thank you!!

---

