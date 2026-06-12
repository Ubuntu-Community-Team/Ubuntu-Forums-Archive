---
title: "Missing the task icons on status bar"
date: 2008-10-07
forum: General Help
---

### Post by ilantal on 2008-10-07
I have an Ubuntu machine set up for a friend with several users.
One user has difficulty with his eye sight so we set it up at 800*600. That turned out to be not enough to fit the application on the screen, so we increased the resolution a bit. Enough to fit the application, but still big enough so he could see it.

In this process the list of open applications on the bottom task bar seems to have disappeared. For other users, it still works normally, but the user with poor eye sight has a problem.

I tried adding things to the taskbar, but I couldn't find anything which would show open tasks, allowing the user to click on them to switch between applications.
Any ideas how to restore this feature?
Thanks,
Ilan

---

### Post by Pelham123 on 2008-10-07
It is possible to 'hide' the taskbar within the config menu, but it should re-appear if you hover the mouse over the bottom edge of the screen. So, are we thinking that the change in resolution has hidden the task bar below the screen level? In which case some monitors have an 'auto-adjust' that re-centers the display when resolutions change.

There are a number of work-arounds if the monitor wont behave. You could swap the resolution so the bar does re-appear and adjust all fonts to a bigger size? The menu bar can be placed to the left or right side of the screen. The height of the bar can be adjusted if it is hidden below.

In the interim, I dont know if you are aware of 'Alt-Tab' shortcut? Hold down Alt and tap Tab to cycle through open Apps.

---

### Post by ilantal on 2008-10-07
Thanks for your reply and your effort to help.
The user has very limited knowledge of the system and we are trying to make it as user friendly as possible. Making it 800*600 was something we did to help his poor eye sight.
I wanted to show him the open applications on the taskbar when I discovered they weren't there.
I see what you mean about the Autohide in the properties, but that isn't it. I can see the trash bin and the icon to hide all windows and show the desktop. However no open applications appear in the taskbar.
I see that I can delete the taskbar and then make a new one. I don't know if this would help. What is the magic which tells an open application to appear in the task bar? There must be something which marks the lower taskbar as special: that is the place to put open application. Apparently that magic is missing.
Ilan

---

### Post by geirha on 2008-10-07
Sounds like that panel app has either been moved to a position where it's hardly visible, or removed completely from the panel. Right click the panel, select "Add to panel", then add the "Window list" applet (Not sure if Window list is the actual name in english, but it should be named something similar)

Use the middle mouse button to drag it around to the proper place, then right click it and lock it in place.

---

### Post by ilantal on 2008-10-07
Thanks. Window list is exactly what I'm looking for.
Sorry that I didn't see it, but I indeed missed it.

The switch to 800*600 was traumatic as it lost the "Applications, Places System" from the upper bar as well. That one I managed to find by myself, but the Windows list I missed.

Now I can put it back and explain to him how to use it.

---

### Post by geirha on 2008-10-07
If you feel you've messed too much around with the panels, you can also reset the panels to default by typing the following in a terminal:
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

