---
title: "Help! Nvidia stole my menu bar!"
date: 2011-06-14
forum: Hardware
---

### Post by FuturistCorporation on 2011-06-14
I just installed the Nvidia graphics drivers for my macbook pro and after I rebooted my computer, the menu bar is gone. This means I can't reach any of the options for desktop settings, open firefox, open the terminal, etc. I thought it might be a desktop resolution thing because the Ubuntu logo at startup was extra big, but I can't get to any of the settings to change the resolution, because I have no menu bar. I went into the /dev/ folder, and I could see the nvidia drivers "nvidia0" and "nvidiactl" that got installed, but I can't open the terminal to make myself root to where I could delete them, because I have no menu bar. If I hit alt+F2, nothing happens. I thought it was possible that the window was opening out of frame, but if I just invisibly type "terminal" or "byobu" and hit enter, again, nothing happens. I can still see all my desktops icons and they are the same size, which makes me think, maybe it's not a resolution thing after all? Help!

---

### Post by FuturistCorporation on 2011-06-14
Ok I wrote a shell script to log myself in as root, delete those two nvidia drivers, and reboot. I made it executable and ran it. Only problem is I still don't have a menu bar! Any ideas?

---

### Post by FuturistCorporation on 2011-06-14
Ok another problem I was able to solve myself. Once I got the terminal open with a script, I just had to run apt-get --purge remove nvidia*

---

