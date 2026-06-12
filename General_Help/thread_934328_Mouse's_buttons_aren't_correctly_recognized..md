---
title: "Mouse's buttons aren't correctly recognized."
date: 2008-09-30
forum: General Help
---

### Post by jokermatt999 on 2008-09-30
Hi, I have a Logitech MX 600 mouse, and despite attempting to set it up with evdev, and later btnx, I still cannot properly get xev to recognize the buttons.

The problem is that some of the buttons are recognized incorrectly. For example, tilting the scroll wheel left is recognized as the same button as back, button 8. Zoom 100% gets itself confused with middle click. Lastly, zoom out isn't even registering at all. 

I've looked at several different guides on how to configure a mouse, but none of them seem to touch on this issue. Its not that I can't remap the controls (I have zoom in set to volume up correctly), its that I can't get btnx to override whatever is settings zoom 100% to middle click, and scroll left to back. Furthermore, nothing I do seems to be able to register zoom out at all, despite it showing up in btnx. xev simply refuses to notice it.

In short, help! :confused:

Edit: I just tried xev again.
Left click = button 1
Middle click = button 2
Right click = button 3
Scroll up = button 4
Scroll down = button 5
Now here's where it gets odd..
Scroll left = button 8 (back, ignores btnx)
Scroll right = (no button output, recognizes it being mapped right in btnx)
Back = button 8
Forward = button 9
Zoom in = (no button output, recognizes it btnx mapping)
Zoom out = (absolutely nothing)
Zoom 100 = button 2 (middle click, ignores btnx)

---

### Post by jokermatt999 on 2008-09-30
Okay, it gets weirder. I found that the zoom 100 button *does* work as mute, and the zoom out does work as volume down...its just not recognized by xev. Wtf.:( Still, zoom 100 still middle clicks, and left scroll works as back...which I don't want.

---

### Post by jokermatt999 on 2008-10-01
Sorry for the triple post, but I think I've found the problem. The physical buttons are handled wrong by X. I've found out how to map physical buttons to logical buttons, but I can't find a way to change the physical mapping. Normally, I'd just say forget it, but I know there must be a way. Why? btnx managed to tell the difference between my back and left scroll/middle click and zoom 100% buttons. The problem is, I can't completely give control over to btnx. When I hit left scroll, xev registers it as button 8 (back), and left. I've tried remapping button 8, but it remaps both!

This makes no sense to me whatsoever anymore. Does anyone out there know how to fix it?

---

