---
title: "Drag and Drop in AWN not working"
date: 2008-09-14
forum: General Help
---

### Post by mmccollum on 2008-09-14
I'm new to linux and I'm trying to get AWN up and running. It works with the basic applets, but I can't seem to set up any launchers. I spent several hours searching and everybody says to just use the drag and drop, but when I try to drop the icon nothing happens. (I've tried dragging many icons, including from the applications menu and /usr/share/applications/ )

I'm running Ubuntu 8.04, and I can't remember exactly where I got the directions to install AWM. Please help.

Here is a copy of the output of running it from the command prompt:

(awn-applets-migration.py:7697): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `AwnConfigClient'
Screen is composited.
APPLET : /usr/share/avant-window-navigator/applets/places.desktop
APPLET : /usr/share/avant-window-navigator/applets/to-do.desktop
APPLET : /usr/share/avant-window-navigator/applets/media-control.desktop
APPLET : /usr/share/avant-window-navigator/applets/tomboy-applet.desktop
APPLET : /usr/share/avant-window-navigator/applets/trash.desktop

** (awn-applet-activation:7700): WARNING **: Places: XDG_DESKTOP_DIR is not set... defaulting to "~/Desktop"

---

### Post by Ub1476 on 2008-09-14
You are to drag it to awn till you see a small "+" icon I believe, then drop it. That's how I've done it in the past at least. But I'm quite sure you can add launchers/apps via AWN manager.

---

### Post by mmccollum on 2008-09-14
Unfortunately, no plus icon appears.

Also, I have tried adding launchers through the AWN manager, and those don't show up in the bar either.

---

### Post by BastardNamban on 2008-11-29
I don't know if you're still having this problem- but I did, until now, and since I don't see any answers for this question, I'm posting the simple solution here.

Drag and drop of launcher icons not natively in AWN works ONLY if you add the "Launcher/Task Manager" applet to the panel bar (it's description is "the main awn launcher/taskmanager applet". It looks like a little blue square with two little switch-like thingies on it at the top, and a triangle arrow pointing up beneath that. 

It seems stupid to add that to the bar itself to enable dragging & dropping of other applets, since you just right click the bar to bring that up normally, but if you add that applet to the bar, you will also enable dragging & dropping of any other items to it as well.

Until now, I refused to use AWN since it would n't let me do that, but now, I'll try it. It seems to only work if you add that applet in the panel too, maybe it's a bug? I hope future versions don't require this, I like as few applets as possible.

---

### Post by snipe76 on 2008-11-30
i have the same problem in ubuntu 8.10
but i see the plus and i drop the icon and nothing happen
...

---

### Post by DarkZatarra on 2010-08-29
> **BastardNamban said:**
> 
Drag and drop of launcher icons not natively in AWN works ONLY if you add the "Launcher/Task Manager" applet to the panel bar (it's description is "the main awn launcher/taskmanager applet". It looks like a little blue square with two little switch-like thingies on it at the top, and a triangle arrow pointing up beneath that. 


That was the solution. Thanks for the help

---

### Post by Tennis on 2011-01-17
> **DarkZatarra said:**
> That was the solution. Thanks for the help


Didn't work for me.

---

### Post by piquat on 2011-01-18
> **Tennis said:**
> Didn't work for me.

Try opening up the dock preferences with a right click and choosing the Task Manager "tab".  The lower half of that window is labeled "Launchers" and I've always been able to drag/drop to it.

---

### Post by themainliner on 2011-03-08
Er...seems to be working after a restart. Nothing.

---

