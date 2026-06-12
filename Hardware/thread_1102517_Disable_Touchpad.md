---
title: "Disable Touchpad"
date: 2009-03-21
forum: Hardware
---

### Post by Jaded Misanthrope on 2009-03-21
How would I disable my laptop's touchpad in Ubuntu 8.10? It's ****** up beyond repair and is near constantly right-clicking, making it a nightmare to use, so before I end up putting my foot through this piece of crap how do I disable the damn touchpad?

---

### Post by zacktu on 2009-03-21
You can access touchpad preferences with System/Preferences/Mouse and then select the Touchpad tab.

---

### Post by Jaded Misanthrope on 2009-03-22
> **zacktu said:**
> You can access touchpad preferences with System/Preferences/Mouse and then select the Touchpad tab.

There is no Touchpad tab for me.

---

### Post by hlo on 2009-03-22
Try installing gsynaptics

---

### Post by Jaded Misanthrope on 2009-03-22
Installed the gysynaptics package, but there's still no touchpad tab.

---

### Post by frytek on 2009-03-22
A quick workaround to disabling tapping which moves your cursor to weird places while you type is to use "Pointer Capture Applet".

Just right-click on one of your Gnome panel bars and choose Add. Find the applet and drag it to some convenient position. It looks like a green rectangle. 

Now right-click it and choose "Properties". You can change the size (25 pixels is good enough) and add some keys to be pressed while clicking to release your mouse. 

You must add some hot key that you don't use while typing (like Alt, for instance) because without it, TAPPING alone would release your mouse every time. So check the "Alt".

Now, click your text, and move your pointer to the applet and click it. It becomes red (on my screen is brownish?) and you can type without jumping cursor. 

When you want to release back your mouse, press the key you chose (Alt) and the touchpad button. 

Enjoy. :D

---

