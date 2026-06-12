---
title: "Found a Workaround for Vaio's brightness problem."
date: 2010-05-20
forum: Hardware
---

### Post by jorgecarrillo150990 on 2010-05-20
First, make sure you have "smartdimmer" installed on your PC.

Go to System> Preferences> Keyboard Shortcuts

Click "Add"

On "Name" put: Decrease Brightness
On Command put: smartdimmer -d
Click "Apply".

Now click on the Shortcut column next to the newly created command and press "Fn + F5" 


Repeat the same process but now put:
Increase Brightness
smartdimmer -i
Fn + F6

Now, the increase brightness didn't work for me. So instead of putting "smartdimmer -i", I put "smartdimmer --set 100". (This incrases the brightness all the way to the Max.

NOTES:
This is a simple workaround, not a fix.

This workaround WON'T use the notify-osd bubbles to show the brightness.

If this has been posted, I apologize!

Hope this works for you!

---

