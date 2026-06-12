---
title: "How to make Stalonetray and AWN play nice together?"
date: 2008-10-07
forum: General Help
---

### Post by thanius on 2008-10-07
Hi there!
I'm trying to create a desktop for myself using Avant Window Navigator and Stalonetray to replace the GNOME-panels.
Problem is though, when I have AWN configured not to be overlapped by maximized windows, Stalonetray won't bother to be placed anywhere near Y-48 (AWN drawing height).
Launching Stalonetray before AWN will work, but only until a new icon on stalonetray is redrawn, and it jumps up over the AWN drawing area.

My question is, can I have stalonetray drawn to the bottom layer as i.e. Conky (which doesn't have this problem)? I've spoken with a few on IRC, and they tell me it's an issue on Ubuntu only as Gentoo doesn't have this problem. Perhaps should I compile from source?

If it's NOT possible, even from source; is there a program for xorg that can define the max height of windows so that I can disable this option in AWN and still have the icons (or, actually, the Conky displayed on the wallpaper) visible?

Any help would be appreciated.
Cheers!

/Than

---

### Post by thanius on 2008-10-09
Bump? Bump-a-dump?

---

### Post by loomsen on 2008-10-09
Compiz?

Window placement rules ftw!




But, tbh, I'd uninstall stalonetray right away, as well as AWN...

Stalonetray was a RAM Monster. Tho I got enough, that actually wasn't really what I intended. So you might want to consider just having a gnome panel which is not expanding and simply a notification area there... 

Or give kiba-dock a try. Tray works pretty well. It's my favourite of the known docks anyway.

---

### Post by thanius on 2008-10-09
Tried applying Compiz' window-rules on standalone, but it seems to be bypassed.
Tried kiba-dock, didn't like.
*sigh*
Wish I knew some C so that I could patch stalone myself.

---

