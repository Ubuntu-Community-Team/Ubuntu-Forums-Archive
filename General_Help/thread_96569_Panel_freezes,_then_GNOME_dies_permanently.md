---
title: "Panel freezes, then GNOME dies permanently"
date: 2005-11-29
forum: General Help
---

### Post by Legion on 2005-11-29
I was using GNOME for a few hours, when the bottom panel locked up. Everything else worked fine. I killall'd gnome-panel, which killed the bottom and top panels, and brought them back - except they came back frozen (completely blank, no icons or anything, non-responsive to input).

Then, I tried a reboot, and now GNOME won't launch at all. GDM comes up, and I can log in, but all I get is a brown (non-wallpapered) desktop and the startup sound. Nothing else ever comes up.

*sigh*  Back to Windows to use my PC. Any ideas as to how to fix the problem?

---

### Post by Hairy_Palms on 2005-11-29
hmm at gdm press alt-f2 to go to the command line then try reinstalling gdm with apt-get

---

### Post by Legion on 2005-11-30
Did no good, still b0rked.

Looks like I will have to completely reinstall the OS. That's ridiculous.

---

### Post by Murgle on 2005-11-30
Can you give us the output of your Xorg log or at least the end part cuz that is where the problem will be?  You can get it by typing in the terminal "cat /var/log/Xorg.0.log" and give us the last couple lines?

---

