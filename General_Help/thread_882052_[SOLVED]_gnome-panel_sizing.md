---
title: "[SOLVED] gnome-panel sizing"
date: 2008-08-06
forum: General Help
---

### Post by the real omni on 2008-08-06
Is it possible to set gnome-panel so that it doesn't occupy the entire length of the screen? The only thing I use in my gnome-panel is the system tray so about 80% of the gnome-panel is taking up real-estate that could be better used.

Any help on this would be great.

I've tried having a look at stalonetray as a stand-alone alternative but when I install stalonetray all I get is a grey box with no tray icons in it...

UPDATE:
Ok I'm partway to where I want to be. Right-click on the panel and select "Properties" - that brings up the dialog where I selected "Show hide buttons" and one of the options I didn't notice before is "Expand". When I de-select "Expand" the bar shrinks to just the size of the system tray with the two hide/show buttons.

So it's the right size now, but it centers itself on the middle of the screen. (My gnome-panel hugs the right side of the screen, and with "Expand" de-selected, the gnome-panel is vertically centered while still hugging the right side of the screen.)

I'd like it to hug the bottom-right corner instead of being vertically-centered. Is that possible?

UPDATE 2:
Ok I've solved the centering issue. To center the gnome-panel if "Expand" is de-selected, follow these steps:

1) Hit <ALT>F2 and run 'gconf-editor'

2) In the gconf-editor window, navigate to apps->panel->toplevels->top_panel_screen0

3) In the right-hand pane, scroll down to the entry titled 'y_centered' and de-select the check-box beside it. (For people using horizontal gnome-panel alignment, replace'y_centered' with 'x_centered')

Voila!

---

### Post by the real omni on 2008-08-06
Further update: de-selecting "Expand" has caused some more troubles.

When I log out then back in, the gnome-panel is no longer hugging the right side of the screen. Sometimes it's hugging the left, sometimes it's just floating about an inch away from the right... However it's not floating - I can't drag it anywhere. I can click the "hide" button in which case it scoots down to the bottom of the screen but still doesn't hug the right side.

The only way I can get it back to where it's supposed to be is by right-clicking the panel, choosing 'properties', selecting "Expand" and then de-selecting it again.

---

### Post by drs305 on 2008-08-06
Here are a couple of answers:

1. Gnome-panel size: you can make a shortcut on the panel and set the size with this command (or via terminal):
```
gnome-terminal --geometry 146x45+30+50
```
Width, lines, offset from left edge, offset from top.

2. The behavior of the panels is controlled by gconf-editor and, I believe, has more options than those available by selecting Properties with a right click. Run it in terminal, then navigate to Apps, Panel, toplevels, then top or bottom panel.  The 'expand' setting is the one that stretches the panel across the entire top or bottom. There is an *orientation* setting but it sets the side of the screen the panel is on, not left/right on the top or bottom. :-(  There are x and y settings in the same section that may let you position the panels to your liking. :-)

---

### Post by the real omni on 2008-08-06
> **the real omni said:**
> The only way I can get it back to where it's supposed to be is by right-clicking the panel, choosing 'properties', selecting "Expand" and then de-selecting it again.

Woot! Figured this bitch out too!

Again, the solution is in gconf-editor in the apps->panel->toplevels->top_panel_screen0 section.

I set the following values:

x : 1253  // my screen res is 1280x800 so I just used (x_res) - (panel_size) - 2 as the formula. Change this to 0 if you want your panel to hug the left edge of the screen.

x_right: 0

y: 800  // change this to 0 if you want your panel to hug the top or (y_res) - (panel_size) - 2 to hug the bottom.

y_bottom: 0

Works like a charm now, even through reboots.

---

