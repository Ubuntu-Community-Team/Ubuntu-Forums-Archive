---
title: "GRUB problem after uninstall within Windows"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by curedum on 2009-07-05
I thought that installing Ubuntu within Windows was completely safe, but apparently not. 

I installed Ubuntu 9.04 within Windows, then I rebooted and chose Ubuntu from the dual boot menu. It started to boot up OK then crashed. Not feeling too impressed, I rebooted into Windows then uninstalled Ubuntu via control panel. Unfortunately now every time I boot up I get the dual boot menu (? GRUB). I tried using Mbrfix, but no better. Worse, I now find I can't roll-back Windows XP using System Restore.

Please could someone help me to fully restore my Windows XP setup?

Regards
John

---

### Post by enli on 2009-07-05
I myself havnt used Ubuntu in windows but if I understand correctly the windows bootloader is showing you two choices to boot from, 1 for normal windows and other for ubuntu.

If this is the case open the Run dialogue by Winkey+R and type "notepad C:\boot.ini". File menu > Save as > save it somewhere in case you mess it up. Back to notepad window, remove the reference line containing Ubuntu.

---

### Post by curedum on 2009-07-05
Many thanks, enli. I had come across that file through   System Properties/Advanced/Startup settings   but I was unsure if editing it might make the problem even worse! Anyway my PC is now booting up normally.

Thank you again

John

---

