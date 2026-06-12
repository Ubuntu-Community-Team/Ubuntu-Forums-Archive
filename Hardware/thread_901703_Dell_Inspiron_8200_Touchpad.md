---
title: "Dell Inspiron 8200 Touchpad"
date: 2008-08-26
forum: Hardware
---

### Post by madnarg on 2008-08-26
I am running Kubuntu release 3.5.9 on my Dell Inspiron 8200 laptop.  I have a touch pad as well as a "nub" (for lack of a better term) mouse in the middle of the keyboard.  This "nub" is broken and permanently stuck in the down/left position causing my cursor to always be in the bottom left hand corner of the screen.

Going back to my Windows XP days there was a setting in the mouse setup that disabled the "nub".

Does anyone know of such a feature in Kubuntu?

---

### Post by queasy on 2009-03-18
Hello -- New ubuntu user here, with exactly the same problem.  In Windows I can disable the "nub" on my keyboard (Dell Inspiron 8200), using a very basic setting in the driver menu.  In Ubuntu I have found no way to do so, and the mouse pointer constantly drifts around the screen, due to the faulty "nub".  The help menus suggested that the entire touchpad could be disabled, using the "touchpad" tab under the mouse-setting menu.  Even that would be fine, as I could then use a normal mouse and ignore the touchpad entirely, but the touchpad continues to function (including the faulty "nub") even when I set that box to "disable".  Has anyone found a solution to this problem?  Perhaps a driver specific to this touchpad would at least allow the whole thing to be turned off.

---

### Post by Gramps on 2009-03-18
What I did on my Dell Inspiron D600 was to take the keyboard out and unplugged the nub. This stopped my cursor from wandering all over the screen.

---

### Post by queasy on 2009-03-19
Hello Madnarg and Gramps --

I found a workable if not ideal solution to this problem, short of physically removing the "nub".  In the BIOS menus for the Inspiron 8200 (accessible by hitting F2 during the earliest portion of the boot cycle), there is a setting for disabling the touchpad.  This is found on something like the fifth or sixth page of the available menus.  One of the available settings, labeled "PS2/touchpad", causes the entire touchpad to be disabled whenever the computer boots while a mouse is plugged into the PS2 port (I haven't tried a USB mouse yet, nor have I tried a USB mouse plugged into the PS2 port with an adapter, but those will be my next items to test).

If you switch to this setting, you can plug in a mouse before booting to Ubuntu, and the entire touchpad, including the "nub" will be disabled.  You can also do the same in Windows, or you can boot to Windows without a mouse, and use the rest of the touchpad (because you've already disabled the "nub" within Windows, using the settings in the Windows touchpad driver).

It's not an ideal solution, because you lose the entire touchpad whenever you use the mouse, but it requires no surgery.  It works in the 8200, and I suppose it will work in various other laptop models as well.

Happy computing.

---

