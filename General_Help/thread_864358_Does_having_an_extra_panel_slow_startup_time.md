---
title: "Does having an extra panel slow startup time?"
date: 2008-07-19
forum: General Help
---

### Post by Morty007 on 2008-07-19
I have 2 panels, top and bottom. I got rid of the top one and just did a bottom, but I really like 2 of them so things don't get crowded. 

When I rebooted with just the 1 panel, the startup time seemed a little faster. Am I imagining things? What slows down startup time in linux?

---

### Post by jpeddicord on 2008-07-21
> **Morty007 said:**
> I have 2 panels, top and bottom. I got rid of the top one and just did a bottom, but I really like 2 of them so things don't get crowded. 

When I rebooted with just the 1 panel, the startup time seemed a little faster. Am I imagining things? What slows down startup time in linux?

It won't slow down the startup time from power on to the login screen, but it will slow down the time it takes to load your desktop after you log in. All of the panel objects have to be started each time.

Most system services are things that can slow down startup time, while user-started applications (gnome-do/xchat/pidgin/etc at boot) will only slow down the time it takes to sign in.

---

### Post by Morty007 on 2008-07-21
Would putting the desktop drawer on the panel and then putting the folders you want in there be any better? 

I prefer both panels but I can do a single one.

---

