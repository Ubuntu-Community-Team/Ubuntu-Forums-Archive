---
title: "How to run gnome-terminal without window border?"
date: 2008-11-16
forum: General Help
---

### Post by eydaimon on 2008-11-16
Is it possible to run gnome-terminal without a window border? I've managed to turn off the menubar and scrollbar through the normal terminal settings, but I can't find a place to turn off the window border.

Eterm had a --borderless option which was great. I've seen compiz has a way to turn off borders, but I believed that turned off borders for all windows.

---

### Post by eydaimon on 2008-11-16
I managed to accomplish this with "alltray"

However, notice how the Eterm window to the left is shadowed. Would this be possible with gnome-terminal?

[IMG]http://http://plasmon.rghost.ru/54012.image[/IMG]

---

### Post by eydaimon on 2008-11-16
Here the drop-shadow of Eterm is very visible. Eterm is the left window sitting above the big terminal window. ( I removed the original images. )

[http://rghost.ru/54026.image](http://rghost.ru/54026.image)

---

### Post by eydaimon on 2008-11-16
hm, seems I can use transset to set transparancy to the eterm window... maybe I'll do that. Wish transset was documented somewhere. It will suck to have to transset on every window I've got :/

---

### Post by eydaimon on 2008-11-16
[http://rghost.ru/54234.image](http://rghost.ru/54234.image)

I got it working here, but I have to run transset on the windows individually which kindof sucks. Let me know if anyone has a better idea.

Also note here that Eterm provides dropdown shadow for the font itself too :)

---

