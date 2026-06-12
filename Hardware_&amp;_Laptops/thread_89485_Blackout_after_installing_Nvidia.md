---
title: "Blackout after installing Nvidia"
date: 2005-11-12
forum: Hardware &amp; Laptops
---

### Post by SparkyDawg on 2005-11-12
I followed the guide to installing nvidia drivers, but when I restart all I get is a black screen and Ubuntu fails to start up, I have reinstalled 3 times and just reinstalled for a 4th and do not want to mess it up, what should I do?

---

### Post by Mustard on 2005-11-12
Probably the easiest way to get a display back up and working is to try ```
sudo dpkg-reconfigure xserver-xorg
``` and choose VESA for your driver (choosing defaults for all other options ie. just click through the rest of the options without changing anything).

From there you will have a display at least and be able to start troubleshooting again.

If you don't get a terminal prompt during normal bootup, then try recovery mode (which can be found in the grub menu at startup.  You may have to press ESC to get the grub menu up at startup).

---

### Post by SparkyDawg on 2005-11-13
Thanks a bunch I'll try this.

---

### Post by tseliot on 2005-11-13
[QUOTE=SparkyDawg]I followed the guide to installing nvidia drivers, but when I restart all I get is a black screen and Ubuntu fails to start up, I have reinstalled 3 times and just reinstalled for a 4th and do not want to mess it up, what should I do?[/QUOTE]

Try my guide: [http://ubuntuforums.org/showthread.php?t=75074]("http://ubuntuforums.org/showthread.php?t=75074")

If you already did, please tell me which method of mine you have tried.

I also need the model of your graphic card.

If you have any questions you can ask them in the thread of my guide

---

