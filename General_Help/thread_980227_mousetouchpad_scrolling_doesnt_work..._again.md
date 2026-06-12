---
title: "mouse/touchpad scrolling doesnt work... again"
date: 2008-11-12
forum: General Help
---

### Post by Fittersman on 2008-11-12
I have had this problem a few times already with each ubuntu release, but it never seems to get fixed. Until now I could just go into the xorg.conf file and edit the things i needed to edit to make it work, but it seems Ubuntu (and Fedora 10, which also had scrolling problems) have moved away from the xorg.conf file. Now I'm completely lost and have no idea how to even start working with this problem.

Scrolling doesn't work on the touchpad or my logitech G9 mouse. If anyone has any idea how to get scrolling to work that would be great. One thing I have noticed however, is that if i plug in another generic mouse (it can scroll), then unplug it and plug my G9 mouse back in, I can now scroll with the G9.

Another side problem (if you happen to be in a helpful mood :)) is that none of the "extra" buttons (side buttons, tilt wheel) map properly. They all map to either mouse1, mouse2 or mouse3 (so for example my front side button acts as right click). If you happen to know a fix to this I would like to know it, but really, its not that important to me (scrolling however, is really important).

---

### Post by Fittersman on 2008-11-14
I found something out that may be able to help! My scroll wheel scrolls *horizontally*, not vertically like it should.

Is there any way to swap vertical scrolling with horizontal scrolling?

---

### Post by Fittersman on 2008-11-14
Just in case someone is following this thread and they are having the same problem, I found a fix for it. The fact that horizontal and vertical scrolling were switched lead me to find xinput. This command fixed the G9 mouse (I left the touchpad backwards since i seem to like it that way):

First off type in "xinput list" and locate the mouse's id number, mine was 8
```
$ xinput list
...
"Logitech G9 Laser Mouse"	**id=8**	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
...
```

then type in this command:
```
$ xinput set-button-map **8** 1 2 3 4 5 6 7 8 9
```
where the bold **8** is the id number you found in the previous step.

Basically, for some reason when Ubuntu was first installed, the xmodmap went 1 2 3 6 7 4 5 8 9 for some reason. This changes that to the proper way.


Another thing, if you want the touchpad and the mouse to scroll like they should, just use this command:
```
$ xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9"
```

hope that helps someone else out, took a few hours of googling to come up with a fix for this.

EDIT: It seems that after a logout or restart this fix needs to be reapplied, so to have it applied automatically for you each time you must go to System->Preferences->Sessions then under the "Startup Programs" tab click "Add." Once in the "Add" menu, give it a name (mouseFix for example) then in the command box type whichever command you preferred from above (such as xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9")

---

