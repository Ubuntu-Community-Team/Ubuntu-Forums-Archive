---
title: "Middle mouse working incorrectly 20.04"
date: 2021-04-07
forum: Hardware
---

### Post by silliewous on 2021-04-07
On my Lenovo Thinkpad P51s, running 20.04 the middle mouse is working strange.
A middle mouse click is only registered when releasing the button. The left and right buttons function normally, so the click is registered as soon as I press it down and released when I release it.

The way it is functioning right now doesn't allow me to pan around in FreeCAD and KiCAD, which is normally done by pressing and holding the middle mouse button.

---

### Post by TheFu on 2021-04-09
Sounds like there are different clipboard tools fighting with each other.
KDE has a clipboard, GTK has a clipboard and the X/Server has a copy butter.  For my needs, I prefer the X/Server copy buffer, but it isn't a stack that copies can be added onto then pulled off in reverse order (a stack).  It only has 1 set of text inside it at a time ... or it is empty.  The X/buffer is a select/paste operation - the selection alone puts the text into the buffer and the middle mouse button will paste it ... on the release (up) action.

---

