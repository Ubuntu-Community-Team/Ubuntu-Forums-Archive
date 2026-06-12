---
title: "Issue with Desktop Settings"
date: 2008-08-06
forum: General Help
---

### Post by timmerson on 2008-08-06
I've recently upgraded from Gutsy to Hardy, and everything was working great until this morning, when I booted up my computer to find that the desktop background image has been replaced by a solid colour. Also, the icons in the Main Menu at the top have disappeared, the window effects have been replaced by a very rough, functional look (so it's looking a little like a windows 98/Gnome crossover). The issue I seem to have is that gconf-editor has removed a lot of the values in its config bit for the desktop, so that it gives <no value> instead of a little checkbox in show_desktop, for example.

There are quite a few of these missing values, so I was wondering if anyone new what the default values were, or how I can find out; and also, why it might be happening so I can make sure it doesn't happen again. TIA

---

### Post by hermes0710 on 2008-08-06
I suggest you create a new user and then take his settings.

---

### Post by timmerson on 2008-08-06
Just tried that. It seems that large portions of my configuration settings have been deleted. Which isn't replaced when a new user exists. Wholesale parts are missing, and stuff like gnome-powermanager isn't working either!

---

