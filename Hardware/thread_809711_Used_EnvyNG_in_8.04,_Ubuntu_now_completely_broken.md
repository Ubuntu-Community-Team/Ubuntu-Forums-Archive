---
title: "Used EnvyNG in 8.04, Ubuntu now completely broken"
date: 2008-05-27
forum: Hardware
---

### Post by jamesbeatty on 2008-05-27
I have an nVidia 8600GTS in my computer -- since it wasn't on the compatibility list, I assumed that I needed to install the nVidia drivers to get 3D support working (the 2D support was fine). Envy seemed like the easiest way to do that, so I installed it from Synaptic (envy-gtk), ran it with auto-detect, and then restarted when it asked me to. 

The first sign something was up was when there were two entries for Ubuntu in Grub (dualbooting with Vista); one was the entry that had previously been there (the number ends with 16) and a new one on top with a number that ends in 17. (I can post the exact text of the entries if that's important). 

I chose the new entry (ending in 17). It loaded almost normal, although after the progress bar filled up it flashed to some text output of what looked like the booting process (again, if this might be important, I can post the text) and then the screen flashed a couple times, and an error warning popped up in front of a black screen telling me that the drivers for my video card were not working. It sent me to a window with one tab for the display settings (resolution was limited to either 640x480 or 800x600, native for my display is 1680x1050) and one for picking out a driver that might work. I picked the nv_new driver, since that had previously been working, and hit OK. The window went away, and I had control of the cursor (which was an X) in front of a black screen for about 5 seconds before the cursor disappeared too. I let it sit like that (completely black screen) for about five minutes before restarting.

The second time I picked the old Ubuntu entry (ending in 16) and had the exact same experience.

I'm guessing that I need to use the Recovery Mode, my questions are which Recovery Mode (for the .17 or .16?), and what should I do in it?

I'm sorry if this is kind of long-winded, but I am a complete n00b in terms of Linux, so I don't know what is/isn't important and just tried to be fairly complete and descriptive.

---

### Post by overdrank on 2008-05-27
HI and you can try and and boot into recovery mode which is usually the second choice in the grub and I would say the recovery mode for the lastest kernel. Then reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then use the command ```
sudo reboot
``` hopefully this will get you to a GUI, Desktop. Good luck.

---

### Post by inportb on 2008-05-27
So it appears that your system is not completely broken (just the graphics), and the thread title's inaccurate ;p

Anyway...

> **jamesbeatty said:**
> The first sign something was up was when there were two entries for Ubuntu in Grub (dualbooting with Vista); one was the entry that had previously been there (the number ends with 16) and a new one on top with a number that ends in 17. (I can post the exact text of the entries if that's important).

I can tell you that 2.6.24-17 is the new kernel everyone's got. It's no cause for alarm.

If you boot into recovery mode, you can run xfix from the friendly menu. If that fails, try removing and purging the current video driver and installing the one in the repositories (which worked for you)

---

### Post by jamesbeatty on 2008-05-27
Yeah, this worked perfectly, thanks!

---

