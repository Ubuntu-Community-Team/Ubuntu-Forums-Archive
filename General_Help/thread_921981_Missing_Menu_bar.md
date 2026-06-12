---
title: "Missing Menu bar"
date: 2008-09-16
forum: General Help
---

### Post by darki3lade on 2008-09-16
Hey, I just finished watching a movie on my computer in fullscreen, and when I went back to desktop, my bottom bar was missing! I've googled for help and couldn't find anything. I know perfectly well how to use the top bar and how to make a new one and stuff, but I'd like my OLD bar back. Also, I've tried making a new one, and when I set the orientation to bottom, it just move my current application up a little bit and theres still EMPTY space under it, If I right click on it, it's just like right clicking on the desktop. I'm not sure what I've done, I've tried messing around with "gnome-taskbar" and stuff and I've reset my top one, but the bottom is still missing! any help?

---

### Post by darki3lade on 2008-09-16
Hey guys, I don't like bumping, but I kinda need help here...

---

### Post by frankleeee on 2008-09-17
Have you tried a restart.

---

### Post by mb_webguy on 2008-09-17
What happens when you open a terminal and type "killall gnome-panel"?

---

### Post by darki3lade on 2008-09-17
Well, I ended up restarting. That finally reloaded my bottom bar, but I had to redo both my top and bottom ones to get them back the way they were. When I tried to use killall it would reload my top bar, and put a space on the bottom where the bottom bar SHOULD have been. I don't know what was going on, but this isn't the first time it's happened. If anybody has a solution other than restarting, it would be greatly appreciated.

---

### Post by y-lee on 2008-09-17
Sometimes the configuration data for panels gets mess up. While your panels are properly working open the Configuration editor, it should be in your menu somewhere or try in a terminal

```
gconf-editor
```

Now find your panel information and see what it is supposed to look like. In my case the bottom panel data was found at **apps**->**panel**->**toplevels**->**bottom_panel_screen0**, note the data found there. (your bottom panel may be stored in a slightly different location in gconfig-editor, just look around in that case untill you find it).

Now the next time your panel is messed up open gconf-editor and see if the data is still the same. If not change it back to the correct values.

This may or may not help.
Good luck and peace.

---

