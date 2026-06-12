---
title: "Wrong display mode"
date: 2016-06-07
forum: Hardware
---

### Post by sebastian-gutzwiller on 2016-06-07
Hi all

After upgrading my PC (i686) from Ubuntu 10.04.4 to 14.04.4 (kernel 4.2.0-27) I only see the upper     left detail of the whole screen.
    
    In the Xorg (1.17.2) log file I found that the mode was probed to 1024x768     instead of 640x480 that could be caused by the direct rendering manager (i915 v1.6.0) raising a kernel error message.

Is there a proper way to force the mode by loading display data to the kernel? If yes what tools are available to do that?

TIA Sebastian

---

### Post by christiaan3 on 2016-06-07
I hope I understand your problem right..

You are able to adjust your display in the grub file. 
enter it with sudo nano /etc/defaults/grub

Remove the # on the beginning of the line, where it shows the resolution.
Next enter your 640x480 resolution.
Enter the command " sudo upgrade-grub " 
Then restart your machine.

---

### Post by sebastian-gutzwiller on 2016-06-08
At the moment is the display resolution of grub not so important.

While & after booting I only see a detail of the whole screen. Any tips?

---

