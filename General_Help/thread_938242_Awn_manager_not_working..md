---
title: "Awn manager not working."
date: 2008-10-04
forum: General Help
---

### Post by xxarthur33xx on 2008-10-04
I installed Awn about 5 times now, and I can't seem to get the manager to work. I got it to the point where It will show on the dock, but then just disappear. Does anyone know what the problem is?

---

### Post by xxarthur33xx on 2008-10-04
Anyone?

---

### Post by Dj Melik on 2008-10-04
Hey there, I had a similar problem earlier. Try the following:

1. Open terminal.
2. Type avant-window-navigator
3. That should run the AWN, then try to open up manager.. it should work.

Post your results, and I'll get more in depth if needed. I'm more than positive that, that should fix it.

---

### Post by xxarthur33xx on 2008-10-04
Screen is composited.
LOADED : /usr/share/applications/gimp.desktop
LOADED : /usr/share/applications/scite.desktop
LOADED : /usr/share/applications/synaptic.desktop
LOADED : /usr/share/applications/audacious.desktop
APPLET : /usr/share/avant-window-navigator/applets/taskman.desktop
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 200, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 101, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 165, in __init__
    self.setup_color(TITLE_BACKGROUND, self.wTree.get_widget("backgroundcolor"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 181, in setup_color
    color, alpha = make_color(self.client.get_string(key))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 65, in make_color
    color = gtk.gdk.color_parse('#' + hexi[:6])
ValueError: unable to parse colour specification

---

### Post by Dj Melik on 2008-10-04
Seems like something is wrong in the compilation. 

Try uninstalling the program completely, then remove all user set preferences located in

/home/xxx/.config/awn/

Then re-install the program.

Then I suppose you can follow the instruction in the previous post after re-installation:

"1. Open terminal.
2. Type avant-window-navigator
3. That should run the AWN, then try to open up manager.. it should work."

---

### Post by xxarthur33xx on 2008-10-04
wow..I fixed it...I had a bad color, was 6 characters instead of 8...The thing that stuck out to me was the last 3 lines 
"File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 65, in make_color
color = gtk.gdk.color_parse('#' + hexi[:6])
ValueError: unable to parse colour specification"

---

### Post by Dj Melik on 2008-10-04
I'm not that good at Linux, sorry tried my best though :). Glad you fixed it!

---

### Post by xxarthur33xx on 2008-10-04
I'm not good either. Thanks for your help though, if you didn't tell me to run it in terminal, I wouldn't have found out the hex was wrong. :D

---

### Post by shogunmidas on 2008-12-16
when i do

1. Open terminal.
2. Type avant-window-navigator

it opens fine... it runs, but the second i close the terminal, it disappears. why??? i like it and im trying to make it run even without the terminal open...

---

### Post by Izek on 2008-12-16
> **shogunmidas said:**
> when i do

1. Open terminal.
2. Type avant-window-navigator

it opens fine... it runs, but the second i close the terminal, it disappears. why??? i like it and im trying to make it run even without the terminal open...

ALT+F2 and type into the box avant-window-navigator

make sure run in terminal is unchecked.

If you want it to start up when you start Ubuntu, then you need to go into System > Preferences > Sessions and add avant-window navigator as a new command.

---

