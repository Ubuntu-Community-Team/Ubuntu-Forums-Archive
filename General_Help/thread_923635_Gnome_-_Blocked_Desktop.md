---
title: "Gnome - Blocked Desktop"
date: 2008-09-18
forum: General Help
---

### Post by nahuel_89p on 2008-09-18
Hi people, I installed the app "ubuntu tweak" to customize my desktop, among other things that aren't really important.
The point is that suddenly, my icons on my desktop disappeared. Besides, my desktop has another worrying symptoms: it doesnt response to the right-click, which means that the right-click menu isn't displayed...
Also, I can't drag and drop any icon from a folder to my desktop, it just "rebounds". Lastly, I cant make any selection with my pointer, by saying this i mean that the classic square that is drawn every time you hold the left click and move the pointer isn't shown.
Summarizing, my desktop is blocked.
I restarted everything I modified with the tweak app, but the desktop is still blocked. I think that the last drop was the activation of the option "nautilus with root privileges) or "nautilus with wallpaper". I deactivated both, but nothing comes to normal.
The bar (panel) in my desktop works ok. Screenlets works ok too, and i clarify that im currently working with emerald and compiz.
What do you suggest?

P.d:1) I can see my icons in the "desktop" folder. 2) I've already tried with restarting and reinstalling nautilus, but nothing seems to heal my ubuntu desktop.

Thanks in advance! And sorry for my english, i hope you understood everything i wrote, I'm Argentinian.

---

### Post by northern lights on 2008-09-18
> **nahuel_89p said:**
> 2) I've already tried with restarting and reinstalling nautilus, but nothing seems to heal my ubuntu desktop.

I think you're alreadyon the right track, as nautilus, apart from being the filebrowser, also drawas the desktop. I f you run```
gconf-editor
```check whether "show_desktop" is enabled under "apps/nautilus/preferences"

---

### Post by nahuel_89p on 2008-09-18
Thanks for your quick anwser... but I've done it already, and it didn't work...

I'm afraid this is serious... but the fact that at the begging i can see the icons for a second, doesn't tell you something else?
P.d: i also uninstalled ubuntu-tweak, and rebooted.

---

### Post by northern lights on 2008-09-18
> **nahuel_89p said:**
> [...] I've done it already, and it didn't work...
I'm afraid this is serious.
I don't want to and can't judge the seriousness of the issue beyond the point that you're undoubtedly in more trouble than I had assumed / hoped you'd be.

> **nahuel_89p said:**
> but the fact that at the begging i can see the icons for a second, doesn't tell you something else?
Assuming that "begging" is meant to be "beginning", this makes it even more trifling. To me at least, that is.

> **nahuel_89p said:**
> I can't drag and drop any icon from a folder to my desktop, it just "rebounds". [...] I think that the last drop was the activation of the option "nautilus with root privileges) or "nautilus with wallpaper".These two facts point towards your issue being related to screwed up permissions (since nautilus is supposed to draw the desktop, "nautilus with wallpaper" should be rather normal an option). In nautilus, right-click on the "Desktop" folder in '/home/USER/' (where USER is your username) and check ownership and permissions. What does it say?

---

### Post by nahuel_89p on 2008-09-18
Owner: nahuel
folder access: create and delete files
file acces: --

GRoup: nahuel
folder access: create and delete files
file acces: --

Others:
folder access: create and delete files
file acces: --

execution: allow to execute files as applications (this one is half marked)
SeLinux context: unknown

button which label says "apply permissions to all files contained"

This is the simple view, i can choose for a detailed view by exploring the nautilus preferences with "gconf-editor".

P.d: Remember that the wallpaper is fine, no problems with it, nor the menu, the panes.
P.D2: As i set all file permissions to "reading and writing", they goes back to the annoying "--" but I'm not sure if that's the point.

Anyway, I can open the files and folders contained in the "desktop" folder.

---

