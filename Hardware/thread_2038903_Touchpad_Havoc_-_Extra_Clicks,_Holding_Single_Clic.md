---
title: "Touchpad Havoc - Extra Clicks, Holding Single Click Too Long"
date: 2012-08-07
forum: Hardware
---

### Post by wyth on 2012-08-07
For some time -- a few versions, going back to at least 10.10 -- I've had some maddening issues with my synaptics touchpad. At seeming random moments, but most definitely after coming out of a blank screen, the touchpad stops registering clicks/taps correctly. 

The following occurs:

[LIST]
[*]Single left-clicks will sometimes not register at all on the first, second, third, or fourth (or more) click/s, and then seems to register a few of them at once, thus creating general havoc. This is especially maddening when trying to simply select some media -- video or audio -- by left-clicking and dragging over the file/s and then releasing, and a split second later the machine decides I clicked on the file/s and opens them up.  

[*]At other times, single left-clicks will result in several rapid clicks at once, which often messes up the window/application being single-clicked on, and creating more havoc. 

[*]Sometimes single left-clicks (and occasional taps) result in the machine thinking I'm holding the button down, and instead of registering the click, it moves the window (as if I were hold the alt key and then left-clicking to move  a window -- but it's just a left-click)

[*]Sometimes just tapping the touchpad itself -- which should just register a single left-click -- brings up the menu that a right-click brings up.
[/LIST]

I've searched on and off for a couple years now for an answer to this issue, and it didn't get any easier with the transition to Unity and the new config files. What I can confirm is:

[LIST]
[*]Disabling and re-enabling psmouse doesn't seem to make a difference.

[*]It works fine in Windows XP. There are never any click issues, and the touchpad is far more responsive and accurate.

[*]After a while -- 20 minutes, 2 hours, half a day, it isn't consistent -- the touchpad will start to work normally again. But after the screen goes to sleep, most likely the problems will begin again.

[*]If I use a usb mouse, the problems are less consistent, but still occur -- left-click havoc.
[/LIST]

I've looked through my xinput and synclient options, and that's all well and good, but I can't find any info on what to adjust in order to get things working right. (Finding what the different options do is no easy task, either). I can't even find info on if I can clear any of those settings out and if the OS will simply reset things. 

All I want is my touchpad to work as well on my shmancy 12.04 setup as it does in my rickety 10-year-old virtual machine XP setup.

EDIT: This happens in Gnome as well, but not quite as much, and never as long as it lasts in Unity.

---

### Post by wyth on 2012-08-08
bump

---

### Post by wyth on 2012-08-10
'nother bump

---

