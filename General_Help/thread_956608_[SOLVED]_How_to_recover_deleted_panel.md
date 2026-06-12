---
title: "[SOLVED] How to recover deleted panel"
date: 2008-10-23
forum: General Help
---

### Post by rmcellig on 2008-10-23
I was playing around with Ubuntu and deleted the default Panel at the bottom of the desktop. How exactly can I recreate the default bottom panel?

Is there a way to put the Applications, Places and System items that are on the top panel? I couldn't figure out how to do this when selecting the Add to Panel option.

---

### Post by beno1990 on 2008-10-23
Right-click on the panel you have left and choose new panel, it should let you configure its position and such afterwards.

To get the menu you want (Applications, Places, System), go to add to panel and choose "Main Menu".

---

### Post by rmcellig on 2008-10-23
Thanks for the info but I can't remember what the default bottom panel had on it.

---

### Post by sethvath on 2008-10-23
workspace switcher, trashcan

You can always add more when you have a need for them.

---

### Post by drs305 on 2008-10-23
One of the most popular items on the bottom panel is "Window List", which displays open apps.

Here's a technique for the next time it happens: Save it beforehand.

To save the panel settings (example to file ~/Desktop/panels):
```
gconftool-2 --dump /apps/panel > **~/Desktop/panels**
```

To restore saved panel settings and refresh the panel (example from file ~/Desktop/panels) :
```
gconftool-2 --load **~/Desktop/panels** && killall gnome-panel
```

---

### Post by rmcellig on 2008-10-23
I never thought that Ubuntu would be so flexible and fun to get to know. After using Macs and PC's for years, I have to say that Linux is pretty cool. Now I have to find out if there are equivalent apps that I have been using on the Mac side that are available in Ubuntu.

I have a feeling I will be spending a lot of time on this forum. :)

---

### Post by dr_smit on 2009-10-21
[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

open Terminal

Open up a Terminal window, by clicking on Applications  \ Accessories \ Terminal. Or, if you deleted the top panel and cannot access the menus, just press ALT+F2 and in the run dialog box, type gnome-terminal then click on Run.

You can also browse for applications, such as Terminal from the Run window, by clicking on the arrow icon next to 'Show list of known applications" and browse for Terminal.

Try these steps in terminal:

[COLOR="Blue"]gconftool-2 - -shutdown

gconftool - -recursive-unset /apps/panel

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
[/COLOR]

---

### Post by eosinophil on 2011-09-04
Thank you very much dr_smit !!!

---

