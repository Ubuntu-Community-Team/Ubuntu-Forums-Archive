---
title: "[SOLVED] Animations Affect Screensaver"
date: 2008-08-17
forum: General Help
---

### Post by KeybladeSephi on 2008-08-17
Hey, everyone. I have been modifying the Animations category in the Compiz Custom Settings Manager, and I have noticed that my "Open Animation" preferences also affect the way my screensaver opens. Is there any way to exclude my screensaver from the animations? All of the animations have their default settings regarding what things they affect. If anyone knows how, please tell me. Thanks

---

### Post by Genius314 on 2008-08-17
Yeah, this annoyed me, because exiting the screensaver made my whole screen burst into flames. :lolflag:

Just add something like this to the end of the window match tag:

> & !(name=gnome-screensaver)

So the whole thing should look something like this:

> (type=Normal | Dialog | ModalDialog | Unknown) & !(name=gnome-screensaver)

(Although I don't know exactly what the default was. There might be more or less "types" in the first group.)

---

### Post by KeybladeSephi on 2008-08-17
Haha thank you so much =]. Also, what do you put to get rid of the animations affecting the little zoom type effect when you click on a launcher in your panel?

---

### Post by Genius314 on 2008-08-17
Well, I don't know about the zoom effect, but you can get rid of the animation that happens to it by adding:

>  & (!type=Dock & !class=Gnome-panel)

That will make the zoom effect not have any extra animations added to it.
I think the zoom is part of Gnome, enabled automatically when a compositing Window manager (such as Compiz) is detected.

EDIT: Okay, figured it out.

Open a terminal or press Alt-F2 and type:
> gconf-editor

Go to /apps/panel/global and uncheck "enable_animations"
Now go to /apps/panel/toplevels/panel_X/ and uncheck "enable_animations" (replace panel_X with whatever panel it is. You'll have to figure that out, there should be two of them, unless you added or removed any)

You shouldn't have to do anything in compiz if you do this. (In other words, ignore everything that I typed above "EDIT:")

---

### Post by KeybladeSephi on 2008-08-18
Again, thank you soooooooooooo much =]

---

### Post by HuaiDan on 2010-05-03
edit

---

