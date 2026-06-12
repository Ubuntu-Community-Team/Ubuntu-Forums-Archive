---
title: "[SOLVED] Top panel issues"
date: 2008-08-01
forum: General Help
---

### Post by SeanLor on 2008-08-01
Good day!

I've encountered an issue with the single surviving panel on my desktop. (If I could find a dock with all of the functions I need, incl a system tray etc, I'd lose it entirely.) I recently updated Compiz to get me some fancy desktop sphere/cylinder action, and after doing so I lost the ability to edit my panel in any way.

I updated Compiz as per posts #4 & #7 of this thread: 

[http://ubuntuforums.org/showthread.php?t=841886&highlight=desktop+sphere](http://ubuntuforums.org/showthread.php?t=841886&highlight=desktop+sphere)

The issue is I can't move or edit the panel; since it's not expanded I can't drag and drop it, and when I right click on the 'move' arrows the only options are 'help' and 'about panels,' no 'preferences' option to be had - I'd usually just expand the panel & drag it wherever. Right clicking things like Stickynotes or the Force Quit icon no longer shows the 'lock to panel,' 'move,' or other options. Argh, I say!

Any suggestions would be greatly appreciated. Thanks!

---

### Post by overdrank on 2008-08-01
Moved to  Desktop Effects & Customization  :)

---

### Post by anotherdisciple on 2008-08-01
Avant window navigator now has an applet that supports a system tray... I use it and it works well... The applet is called Py-not I believe

---

### Post by anotherdisciple on 2008-08-01
Another suggestion... hit Alt+F2 and run gconf-editor

go to applications>panels>levels... or something like that... you may need to navigate the thing to find the options for changing a gnome panel... I will look into it for you and post it...

---

### Post by anotherdisciple on 2008-08-01
okay.. found it... it's apps/panel/toplevels

find your panel... and edit some of the settings from there... let me know if it works this way

---

### Post by SeanLor on 2008-08-01
Most excellent, that's solved enough for the likes of me! Still can't right-click for settings, but gconf-editor allowed me to get it set back up top where it belongs. As for the AWN comment, the last time I tried AWN I found that the system tray & volume control wouldn't work; they showed up as a vertical line. I'd really dig a fully-functional version of Kiba dock with the physics engine, but that's another story for another thread. ;) Thanks for the help!

---

### Post by anotherdisciple on 2008-08-01
No prob ... can you mark this as solved please? Thanks

edit: whoops... you already did!

---

