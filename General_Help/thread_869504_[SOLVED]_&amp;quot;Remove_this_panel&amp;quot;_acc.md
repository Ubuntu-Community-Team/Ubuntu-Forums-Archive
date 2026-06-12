---
title: "[SOLVED] &amp;quot;Remove this panel&amp;quot; accident"
date: 2008-07-24
forum: General Help
---

### Post by Thrasonic on 2008-07-24
Hi again everyone.  So I accidentally got rid of the area of the task bar near the "Start" button where program windows appear so you can click on them to minimize them or bring them back up.  Using alt+tab doesn't seem to work at, either, and they're not on the other desktop available, either.

How I screwed this up was by right-clicking on a program window on the taskbar and accidentally choosing "Remove this panel" or something like that.  I've rebooted and the panel hasn't come back.  So the desktops, system tray and clock are all the way to the left by the "Start" button.  I'm trying to find out how to fix this.  Any help?

---

### Post by tamoneya on 2008-07-24
assuming that you still have the other panel right click on it and select "new panel".  Then reposition it and reconfigure it with right click -> add to panel.

---

### Post by drs305 on 2008-07-24
I have these on my bottom panel but I think what you are referring to is "Window List" which shows opened apps. To get this into a panel, right click, Add to Panel, 'Window List'.

---

### Post by Thrasonic on 2008-07-25
Hello to the both of you.  Thanks for the replies.  I apologize it's been about 24 hours since you posted and I'm just now getting to this, but I literally just sat down at my computer and this is the first place I came to.

Okay, I do have the other panel (I guess that's what it's called) showing.  In Windows I would call this the system tray.  It's where the clock is and any apps you have running that would show up next to it.  I also have my two desktop buttons I can click on to go between desktop 1 and 2.

Did I mention I'm running KDE 4?  When I right-click anywhere on the panel I don't find an option to add a panel.  I've included some snapshots I took with Ksnapshot so you can see what I mean.  Going into Panel Settings on any of these right-clicks gives me snapshot number 3.  It's very irritating not to have that area where the application windows are visible when minimized.  Alt+Tab does work to bring them back, but still...

Any other ideas?

---

### Post by Thrasonic on 2008-07-26
Bump

---

### Post by benerivo on 2008-07-26
First, make sure that widgets are 'unlocked' by right clicking on the desktop. Then, on any existing panel, right click and go to 'Add Widgets'. This should bring up a list. Choose 'Task Manager'.

I think the position of the widgets on the panel, is only changeable in kde4.1 (currently only available as a release candidate, and should be part of ubuntu in early august). In kde4.0, i think you have to remove all widgets (ie. have an empty panel) and add the widgets in the order that you want to have them.

---

### Post by Thrasonic on 2008-07-26
benerivo, you are a genius!  That did it.  Thanks a ton.

---

