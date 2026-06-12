---
title: "SHMCoonfig in Ubuntu 8.10"
date: 2009-03-22
forum: Hardware
---

### Post by Jaded Misanthrope on 2009-03-22
I need to disable the touchpad on my laptop running Ubuntu 8.10, but to do so I need to enable SHMConfig (or something of a similar name) -- how would I do this? I've already tried the FN + F9 combination that is printed on my laptop (made by Toshiba), but that doesn't do anything so I need to enable SHMConfig.

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

