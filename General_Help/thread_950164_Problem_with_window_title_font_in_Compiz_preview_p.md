---
title: "Problem with window title font in Compiz preview plugin"
date: 2008-10-16
forum: General Help
---

### Post by Greg T. on 2008-10-16
I'm using the "Window Preview" plugin for Compiz (up-to-date Hardy), but when I turn on the option for displaying window titles, the font that is displayed is blocky and unreadable. This happens regardless of the font size I select. I do not have this problem in other Compiz plugins that may display the window title (such as Scale); it seemingly only happens in the Preview plugin. I've attached a screenshot. Any suggestions?

---

### Post by Greg T. on 2008-10-16
I've isolated the problem to an extent. If I make the font white, it appears, but the spaces in the letters are black. This means I need a black background for the display to work correctly, but unfortunately there is no option for this in Window Preview. In other contexts (such as Scale), this is possible. It's a workaround, though. The problem is that the text is not displaying properly.

The screenshot shows the problem better than I can describe it. Again, this is after I turned the font to white, compared with black in the previous screenshot.

---

### Post by Greg T. on 2008-10-17
This appears to be due a bug in libcairo:

[INDENT][https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/145604](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/145604)[/INDENT]

"The bug reveals itself if sub-pixel rendering is enabled and rgba_order 'VRGB' is selected." This is the case with my rotated monitor.

The issue may be fixed in Intepid, due to recent patches in libcairo:

[INDENT][https://launchpad.net/ubuntu/+source/cairo](https://launchpad.net/ubuntu/+source/cairo)
[/INDENT]
Guess I'll find out in a couple weeks...

---

