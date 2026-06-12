---
title: "GnomeDo index?"
date: 2008-11-26
forum: General Help
---

### Post by jeenuv on 2008-11-26
I find GnomeDo very useful in launching programs. But I see that GnomeDo doesn't display programs I newly installed. I recently installed AllTray and GHB (HandBrake GUI) but GnomeDo doesn't pick them automatically -- I've to type the full names to launch it. On the other hand, say for programs like Pidgin, I just need to type P and GnomeDo picks it up. I tried looking up GnomeDo preferences to make it re-index (if at all it works that way) but didn't find anything. Also there are other annoyances like I type "home", it shows correct icon, but my home folder just doesn't launch! Any tweaks for this?

I tried to look for a GnomeDo forum/user group, but couldn't find any!

Thanks
Jeenu

---

### Post by euphonism on 2008-11-26
For newly installed programs I suggest restarting gnome-do. Upon restart it will re-index your programs. Also remember that each time you launch a program it moves it up in the priority list, so upon second or third launch you should be able to type a letter or two for it to recognize the application you intend to launch. I've also noticed that it hangs when trying to launch the home folder and think it's probably a bug. So here was my workaround: go to System-->Preferences-->Main Menu and create a new item under Accessories called Home Folder with the command "nautilus /home/xxxxxx/" where xxxxxx is your username. Restart gnome-do and once it re-indexes the programs you can launch the new menu item by typing "Home Folder" (or whatever else you want to call it).

---

### Post by jeenuv on 2008-11-26
I've already restarted my system a couple of times! But I've never noticed GnomeDo increasing the priority for some programs (say for example, scripts my ~/bin directory) even though I tend to launch it quite often. Yeah, and I do so by typing the complete name of executable!

---

