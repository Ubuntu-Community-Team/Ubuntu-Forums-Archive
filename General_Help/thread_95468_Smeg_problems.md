---
title: "Smeg problems"
date: 2005-11-26
forum: General Help
---

### Post by bhagabhi on 2005-11-26
Is there a way to restore the gnome menu to the way it was when it was freshly installed? I have played around with smeg a little too much obviously - Now I can't move my games folder anywhere but not into the "root" of the menu - where I want it.


any hints / tips? perhaps somewhere in the filesystem where this can be edited via configurable files?

---

### Post by charlesbrooking on 2005-11-26
[QUOTE=bhagabhi]Is there a way to restore the gnome menu to the way it was when it was freshly installed? I have played around with smeg a little too much obviously - Now I can't move my games folder anywhere but not into the "root" of the menu - where I want it.


any hints / tips? perhaps somewhere in the filesystem where this can be edited via configurable files?[/QUOTE]

Look at ~/.config/menus/applications.menu, ~/.local/share/applications, and /usr/share/applications/. There may be others, but that's all I can think of.

---

### Post by bhagabhi on 2005-11-26
Oh!

My "~/.config/menus/applications.menu" was really screwed up, so I cleaned it some - And now I have wanted results. 

Many thanks!

---

### Post by charlesbrooking on 2005-11-28
[QUOTE=bhagabhi]Oh!

My "~/.config/menus/applications.menu" was really screwed up, so I cleaned it some - And now I have wanted results. 

Many thanks![/QUOTE]

Glad it all worked out. :)

---

