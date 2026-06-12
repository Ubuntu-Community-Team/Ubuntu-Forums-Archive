---
title: "can't switch workspace"
date: 2008-11-14
forum: General Help
---

### Post by Kinetic Being on 2008-11-14
For some reason, I can't switch between workspaces (desktops). I know its there, because I moved a window over there to see if I could get there if something was there, but I can't get over there. I can hear the window playing sound, so I know its still alive over there, but I can't do anything about it. I tried adding a new workspace-switcher to the gnome-panel, tried changing the position of the screens on the workspace-switcher (I had it so there was two rows and only once column, so I though that might be the problem, but its not, as I now have it back to default (1 row, 2 columns) and it still doesn't work.) I tried adding keyboard shortcuts (CTRL+ALT+1/2) but that doesn't work either. 

Any help is appreciated,
Thanks,

Kinetic Being.

---

### Post by drs305 on 2008-11-14
Does the following list more than one workspace:
```
gconf-editor /apps/metacity/general/num_workspaces
```

Do you use compiz and have you checked the Desktop and Window Management settings?

---

### Post by Kinetic Being on 2008-11-14
Well, I just set some options in compiz for shortcuts for some desktop-switching effects, and I got it working. GNOME's workspace-switcher panel applet stopped working when I upgraded to Intrepid.

---

### Post by mordantae on 2009-01-06
i have the exact same problem.
i have hardy installed on my home pc and my setup there works fine, i run intrepid on my laptop (dell xps m1530) and i had this same functionality break for me after a few tweaks in compiz.

ie: The usual ctrl+alt+right arrow will not take me to the next workspace to the right. Neither will the mouse wheel on the desktop, nor will adding an applet to the task-bar. The only way for me to get to the next workspace is to ctrl+e (expose) and then select the next workspace with the mouse or the directional buttons and pressing enter.

Also, whenever i install some form of linux that uses GUI, i create a keyboard shortcut [CTRL + q] that will bring up the terminal application (or terminator when it is available)

this has never ever failed me, i've created this keyboard shortcut on several different linux distributions and it's never given me an ounce of hassle, but this time it's broken, and when the combination actually does something, it brings up multiple instances of the terminal. 

Its completely random though, i even tried pressing the keyboard shortcut let's say five times and then wait for a response but as many as twelve instances of the terminal applicaition can suddenly appear without warning. 

Just thought i'd throw it in there because it's making me wonder whether there are any other users of Intrepid out there having wacky stuff like this happen to them.


Sorry i can't contribute towards the solving of this problem, but i will be back with any info if i manage to solve it :)


Thanks for reading,

:-\"

---

### Post by ramanabv on 2009-10-01
hi
I have a similar problem. I had previously disabled compiz after gettign it working. Now when I enable compiz, I can swtich workspaces in any way. ctl-alt-right  or left or even choosing the workspace through mouse. I can get ctl-alt-down to show me all the flalteened workspace. I cant get the cube now .ctl-alt-1 doesnt work
regards
Ramana

---

### Post by mydiamond on 2009-12-17
> **drs305 said:**
> Does the following list more than one workspace:
```
gconf-editor /apps/metacity/general/num_workspaces
```Do you use compiz and have you checked the Desktop and Window Management settings?

thanx...this code did help **solved** my problem...

i install n config compiz....but for when this problem occurred, i uninstalled the campiz....

just try the above code....first i unchecked the "**raise on click**" box...then close all window then rechecked the box.....viola...problem settled....

---

