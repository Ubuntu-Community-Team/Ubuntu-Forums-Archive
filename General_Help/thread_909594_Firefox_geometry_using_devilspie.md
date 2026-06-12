---
title: "Firefox geometry using devilspie"
date: 2008-09-03
forum: General Help
---

### Post by gen.alcazar on 2008-09-03
Hi folks:

I use hardy heron with devilspie 0.21-1, and have been successfully using it to "pin" all my pidgin chat windows to all workspaces.  Today, I tried to use it to set the default geometry of firefox, and have run into some problems.  My devilspie configuration script looks like this:

```
(if 
        (is (application_name) "Firefox")
            (geometry "800x600+0+0")
)
```

This is in conformance with what the debug output of devilspie looks like (application name etc.).

```
user@host:~/.devilspie$ devilspie
Window Title: 'Synaptic Package Manager '; Application Name: 'synaptic'; Class: 'Synaptic'; Geometry: 1400x1025+0+0
Window Title: 'Ubuntu Forums - Post New Thread - Mozilla Firefox'; Application Name: 'Firefox'; Class: 'Firefox'; Geometry: 1280x1024+1400+0
Window Title: 'user@host: ~/.mozilla/firefox/nmdj5l24.default'; Application Name: 'user@host: ~/.mozilla/firefox/nmdj5l24.default'; Class: 'Gnome-terminal'; Geometry: 895x777+1400+0
Window Title: 'user@host: ~/.devilspie'; Application Name: 'user@host: ~/.devilspie'; Class: 'Gnome-terminal'; Geometry: 895x777+505+0
Window Title: 'Unsaved Document 1 (~/Desktop) - gedit'; Application Name: 'gedit'; Class: 'Gedit'; Geometry: 1280x1024+1400+0
Window Title: 'user@host: ~/.devilspie'; Application Name: 'user@host: ~/.devilspie'; Class: 'Gnome-terminal'; Geometry: 825x735+70+42
Window Title: 'Desktop'; Application Name: 'File Manager'; Class: 'Nautilus'; Geometry: 2680x1050+0+0
Window Title: 'Left Edge Panel'; Application Name: 'Left Edge Panel'; Class: 'Gnome-panel'; Geometry: 25x102+-24+920
Window Title: 'Bottom Expanded Edge Panel'; Application Name: 'Bottom Expanded Edge Panel'; Class: 'Gnome-panel'; Geometry: 1400x25+0+1025
```

Now here's what I'm seeing:

1. If firefox starts maximized, it ignores the geometry changes configured via devilspie.
2. If I start firefox maximized, unmaximize it, close it, and start it again, it remembers previous "unmaximized" geometry and tries to open it the same way (as expected), but then gets resized using devilspie's configuration.
3. If I maximize firefox, close it and start it again, it will open in the maximized mode (again, as expected) and will ignore devilspie settings as described in #1.

Any idea what I'm missing here?  How can I get firefox to obey devilspie settings irrespective of maximized mode?

Thanks!

---

### Post by gen.alcazar on 2008-09-03
Forgot to mention, I'm not using compiz.  Plain metacity.

Thanks!

---

### Post by gen.alcazar on 2008-09-03
Here's a dumb workaround I figured.  It works for now, but seems lame.  If someone has a better idea, please post.  Essentially, I'm unmaximizing the window, making the geometry changes, and maximizing again.  It slows down the opening phase a bit.

```
(if
        (and
            (is (application_name) "Firefox")
            (matches (window_name) ".*Mozilla Firefox$")
        )
        (begin
            (unmaximize)
            (geometry "+1400+0")
            (maximize)
        )
)
```

---

### Post by gen.alcazar on 2008-09-06
Bump!

---

