---
title: "How to get back the bottom panel?"
date: 2008-11-21
forum: General Help
---

### Post by trendyabinash on 2008-11-21
I want to remove my panel that is at the bottom, but I am afraid to do so as I can't use my system without a taskbar.

So i tried to create a panel just to learn how to make it a taskbar, but fail to do so.

Can anyone guide me with the steps that I have to follow when I remove the bottom panel and try to get it back?

---

### Post by Izek on 2008-11-21
1. Right-click an existing panel you have (you shouldn't remove both, which I call panel-suicide) go to properties and hit the big "+" button. Panel 2 should suddenly appear in the dropdown menu. After that, make sure it's set to expand the full width of the screen (can't remember which setting.)

To get back the buttons, etc. on the bottom panel...

2a. Right-Click (a blank space), Add to panel... then in order:

2b. Show Desktop (repeat 2a after)
2c. Task List (repeat 2a after)
2d. Pager/Workspace Switcher (repeat 2a after)
2e. Trash Applet

You may need to move them around to get them to look how they were (Right-click one of them, and select Move.) Once done moving, right-click them, and select Lock to panel.

---

### Post by trendyabinash on 2008-11-22
task list is not available when I am creating a new panel(while having both default panels). Does task list can be added to single panel???

---

### Post by eternalnewbee on 2008-11-22
> task list is not available when I am creating a new panel(while having both default panels). Does task list can be added to single panel???
Hope this screenshot helps you (notice the bottom panel):

---

### Post by jayson.rowe on 2008-11-22
The "Task List" is an applet that has to be added to a "virgin" panel. See the screenshot that eternalnewbee posted for you, once you click that "Add to Panel" scroll down and look for "Window List" - that's your "taskbar".

BTW, if you want just one panel, you can right-click the little "groove" to the left of your current task-bar, and click "move" and move the "taskbar" part of that bottom panel up to the top panel before you delete the bottom panel as well, so you won't be "without" it.

HTH, and doesn't confuse you more :-)

---

### Post by eternalnewbee on 2008-11-23
> BTW, if you want just one panel, you can right-click the little "groove" to the left of your current task-bar, and click "move" and move the "taskbar" part of that bottom panel up to the top panel
Indeed, and you could also keep left-click pressed, while on the panel, and drag it up.

---

### Post by trendyabinash on 2008-11-23
> **eternalnewbee said:**
> Hope this screenshot helps you (notice the bottom panel):
Man your theme is looking COOL

can you give me the link of the theme???

---

### Post by cdtech on 2008-11-23
You could copy the "~/.gconf/apps/panel" to a backup directory just in case you need to restore it back.

You can see my post on restoring to default here:
[http://ubuntuforums.org/showthread.php?t=983507](http://ubuntuforums.org/showthread.php?t=983507)

Hope this helps ya......

---

### Post by loomsen on 2008-11-23
Just get gnome-do and start kickin it ;)

Add a panel with gnome-do:
Hit Super+Space, to bring gnome-do up, then type run, gnome-panel :)

Next time you wanna use gnome-do for the panel, should be enough to type r to get proposed a "run". You'll like it I'm sure.

Btw, what about the compiz-deskmenu?

[[img]http://www.ubuntu-pics.de/thumb/6245/screenshot_06_l037cO.png[/img]](http://www.ubuntu-pics.de/bild/6245/screenshot_06_l037cO.png)

Nothing easier actually...

---

### Post by loomsen on 2008-11-23
> **cdtech said:**
> You could copy the "~/.gconf/apps/panel" to a backup directory just in case you need to restore it back.

You can see my post on restoring to default here:
[http://ubuntuforums.org/showthread.php?t=983507](http://ubuntuforums.org/showthread.php?t=983507)

Hope this helps ya......

OOOOOOPS

In case he want's to restore the settings only! Should mention that, the binary is in /usr/bin... as usual.

---

### Post by cdtech on 2008-11-23
> **loomsen said:**
> OOOOOOPS

In case he want's to restore the settings only! Should mention that, the binary is in /usr/bin... as usual.

cool, thanks......

---

### Post by trendyabinash on 2008-11-23
> **loomsen said:**
> Just get gnome-do and start kickin it ;)

Add a panel with gnome-do:
Hit Super+Space, to bring gnome-do up, then type run, gnome-panel :)

Next time you wanna use gnome-do for the panel, should be enough to type r to get proposed a "run". You'll like it I'm sure.

Btw, what about the compiz-deskmenu?

[[img]http://www.ubuntu-pics.de/thumb/6245/screenshot_06_l037cO.png[/img]](http://www.ubuntu-pics.de/bild/6245/screenshot_06_l037cO.png)

Nothing easier actually...
Man that gnome-do is really something I need help with
whenever I am pressing super+space a screen is appearing asking me to search but I don't wanna search for anything.


And Loomsen in your screen shot that Application launcher is written in white color font how do you change the fonr color?? or is it a theme?

---

### Post by trendyabinash on 2008-11-23
Look at my desktop

at the top panel all the menu font color is BLACK, I want to change it.
How it is done???

---

### Post by cdtech on 2008-11-23
Install the gnome color chooser:
```
sudo apt-get install gnome-color-chooser
```
This will allow you to change your color.

---

### Post by trendyabinash on 2008-11-23
> **cdtech said:**
> Install the gnome color chooser:
```
sudo apt-get install gnome-color-chooser
```
This will allow you to change your color.
hey thanks
my desktop looks much better now

---

### Post by eternalnewbee on 2008-11-23
> Man your theme is looking COOL

can you give me the link of the theme???
Sorry for the late reply trendyabinash. Here's the link to the Emerald Theme:
[http://www.gnome-look.org/content/show.php/New+Wave+Rounded+Emerald?content=88517](http://www.gnome-look.org/content/show.php/New+Wave+Rounded+Emerald?content=88517)
Here's the link to the GTK Theme:
[http://www.compiz-themes.org/content/show.php/Ubuntu+Dust+theme?content=91219](http://www.compiz-themes.org/content/show.php/Ubuntu+Dust+theme?content=91219)
And here's the link for the desktop background:
[http://images.google.co.uk/images?hl=en&q=dual%20neuron&um=1&ie=UTF-8&sa=N&tab=wi](http://images.google.co.uk/images?hl=en&q=dual%20neuron&um=1&ie=UTF-8&sa=N&tab=wi)

---

