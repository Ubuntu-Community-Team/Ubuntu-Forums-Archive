---
title: "Screen not centered."
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by Unbuntunebie on 2009-02-06
I'm having an issue with the Unbuntu install and am not really sure how to go back at this point. I ran the install disc and played around with Unbuntu for a little bit and really liked it so I decided to install it, but after the install I only get 1/4 of the screen and it is the bottom right corner so I can not use any of the menus to try to troubleshoot it. I have a 500 GB usb external drive which I partitioned for the install and in windows mode I don't see that partition at all. 

Are there any keyboard commands I can try to run to see if I can fix this problem, and if not how do I wipe this install (and the boot option menu) and try again?

---

### Post by dstew on 2009-02-06
Try the **xfix** command from the terminal command line, if you can get one. You should be able to get a command line with ctrl-alt-F1. Enter```
sudo xfix
```Be careful to put in the correct type of monitor. To restart the X-windowing system, I think you use ctrl-alt-backspace.

---

### Post by Unbuntunebie on 2009-02-08
I ran the sudo xfix from the command terminal and it said it was an unrecognizable command. Is there any variation of that command, or an alternative that might help?

---

### Post by ennnzo on 2009-02-08
Does your monitor have an Auto Adjustment button or option in the menu? I had that problem before, but once I clicked on the Auto Adjustment button, my screen was fixed.

---

### Post by uvaraj6 on 2009-02-08
try to  lower your screen resolution

---

