---
title: "[SOLVED] Auto-hide for panels"
date: 2008-08-16
forum: General Help
---

### Post by fiddler616 on 2008-08-16
Hey,
One of the (many, many, many, many) things I like about Ubuntu (well, GNOME) over Windows is the usefulness of the panels--I don't know why, but they're just darn handier. However, they do take up space on a little laptop screen, so I was wondering if there is some kind of "hide after x seconds and reappear on mouse-over for x seconds" sort of a deal (if it happened in Windows, it must be possible in Ubuntu!).
Thanks in advance

---

### Post by dje on 2008-08-16
right click on the panels and select properties and click autohide ;)

dje

---

### Post by lisati on 2008-08-16
Yes - there is an "auto-hide" feature similar to that found in Windows. Right-click on the panel you wish to auto-hide, click on "properties", and you should find an option to turn auto-hide on or off.

Hope this helps.

---

### Post by dje on 2008-08-16
you can edit how much of the panel disappears and how long it takes to disappear by pressing Alt +f2 and running:
```
gconf-editor
```
then navigating to apps >> panel >> global and then adjusting the panel_show_delay, panel_minimized_size and panel_hide_delay variables ;)

dje

---

### Post by fiddler616 on 2008-08-17
Thanks...I'm still kind of in shock about the ease of that, and am trying to figure out how it didn't occur to me to check out the "Properties" of the panel. Oh well. Thanks again!

---

### Post by sayakb on 2008-08-17
Please mark the thread as solved.

EDIT: I noticed that you already did :)

---

