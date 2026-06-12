---
title: "Force disable touchpad (mouse) when typing....on all-in-one device."
date: 2011-07-11
forum: Hardware
---

### Post by thegoonden on 2011-07-11
Hi, I am currently using a Keysonic wireless combination keyboard and touchpad (basically the front panel of a laptop with a wireless interface).

The standard "disable touchpad while typing" option is not available, nor are any solutions involving syndaemon.

the "touchpad" appears to be /dev/psaux

(certainly cat /dev/psaux generates much output when the touchad is touched)

Attempting to manually run syndaemon at all, says there is no synaptic device attached.


So, I assume what I really need here is a way to disable the mouse while typing in the same way as one would do for a touchpad (even though it IS a touchpad LOL).


Any ideas?
All answers much appreciated folks.


System is Natty, but "fault" has persisted since Karmic

---

### Post by ajgreeny on 2011-07-11
Have you looked at synclient?  Use the command ```
synclient -l
``` to show all the levels of options set at the moment, and ```
man synaptics
``` to give details of those options available to you.

It might give you some clues.

---

### Post by smurphy_it on 2011-07-11
You can't double or triple-click the top corner (left of right) of the synaptics mouse pad to disable it ?

No disable button for it on your keyboard ?  (Such as a media bar top of keyboard ? )

---

### Post by thegoonden on 2011-07-11
Can't double or triple click to disable, and it's not really a good solution anyway, since I switch between keys and pad anyway.......what I really need is the auto-disable functionality, thanks nonetheless.

The problem with synclient, syndaemon etc is that as far as Ubuntu is concerned, it's a mouse not a touchpad. Those programs both simply say, no such device and quit. But again, thanks.

Maybe what I need to ask is..... "How to disable mouse when typing"?

---

