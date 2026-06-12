---
title: "Some apps don't respond to touchpad tapping"
date: 2005-10-31
forum: Hardware &amp; Laptops
---

### Post by phanboy_iv on 2005-10-31
I actually like the tap-to-click feature of my touchpad. Unfortunately, since I installed Breezy, 
some apps don't respond to the touchpad tapping. I can still use the left button on those apps, 
but I would prefer to use tapping. On all other things besides those few apps, tapping works beautifully. 
All apps recognized tapping in my old Hoary install. 
Can someone tell me if this is possible to fix...?

---

### Post by 23meg on 2005-10-31
That's weird, have you narrowed down the problem to specific apps? Are you sure that it's a problem with specific apps; could it be that you're sometimes tapping at a speed below the minimum tap time threshold? You should be able to set that in your xorg.conf file.

---

### Post by phanboy_iv on 2005-10-31
Anything not Gnome-based usually doesn't respond, for instance, Audacity, Blobwars, ZSNES, and most other games. Stuff like GIMP, Totem, NVU, Rythmbox, OpenOffice, and Firefox work, though. And it's not a tap threshhold problem, 
I've checked.

---

### Post by 23meg on 2005-10-31
Just checked out the Ubuntu build of Audacity and it responds to double taps here. It may have something to with metacity not passing on the double tap event to non-native apps. An idea: maybe you have to map the double tap event of the touchpad to double clicking. Check your touchpad driver documentation to see if there's such an option you can configure in xorg.conf.

---

