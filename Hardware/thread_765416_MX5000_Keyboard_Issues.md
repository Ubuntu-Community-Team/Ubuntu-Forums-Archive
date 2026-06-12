---
title: "MX5000 Keyboard Issues"
date: 2008-04-24
forum: Hardware
---

### Post by skywalker61490 on 2008-04-24
Alright, so I recently purchased a Logitech MX5000 keyboard and an MX1000 mouse. After many how-to's and X crashes, I finally configured them correctly to work with bluetooth and not USB emulation. My extra buttons worked (for the most part) and i used xbindkeys to map the mouse. However, after I came back to the computer this morning my mouse and keyboard had dropped. I reset X and it crashed, so i reverted all changes i had made to xorg.conf and started over. Only thing is, this time after i got it all working (with some tweaks to the mouse) a window popped up saying the following:

[B]The X system keyboard settings differ from your current GNOME keyboard settings.

Expected was model "evdev", layout "us" and no options, but the the following settings were found: model "pc105", layout "us" and no options.[/B]

Then it asks if you would like to keep the X keyboard settings or the gnome keyboard settings. Regardless of which one i picked (i did it twice), my keyboard layout has a seizure and drops function for the arrow keys, delete, home, page up/down, etc. Now, pressing up arrow brings up the "save screenshot" window, for example.

The weirdest thing of all is that the changes i made worked the first time, yesterday. I haven't updated Xorg or anything since then, and i didn't configure the keyboard any differently the second time. Also, i've had a PS/2 keyboard connected the entire time just in case, and that keyboard works perfectly. I'm getting the impression that it's evdev's doing, but i don't know how to correct it.

Help?

---

### Post by dbd on 2008-11-16
This started happening to me today. A quick search found this thread:
[http://ubuntuforums.org/showthread.php?t=29114&highlight=save+screenshot+arrow](http://ubuntuforums.org/showthread.php?t=29114&highlight=save+screenshot+arrow)

With this solution:
> 
System -> Preferences -> Keyboard Shortcuts

Then either disable the two "Take a screenshot" items, or set them to something else. I have mine at Shift F3 & Shift F4


---

