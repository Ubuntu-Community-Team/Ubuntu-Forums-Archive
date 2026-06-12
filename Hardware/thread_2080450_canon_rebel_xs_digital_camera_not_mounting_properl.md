---
title: "canon rebel xs digital camera not mounting properly ubuntu 12.10"
date: 2012-11-04
forum: Hardware
---

### Post by paridoth on 2012-11-04
So i plug in my digital camera, the icon pops up on the side bar, and i get the "what do you want to do message?" I open the folder, and i can see the folders it makes the and the filenames of the .jpg's inside, but the previews wont load and i cant copy them anywhere or open them in the camera.
 everything just hangs.
 it was just working in ubuntu 12.04 that i installed over. help?

edit: I am having the same error when i atach my zen mosiac player as well.

---

### Post by dgharmon on 2012-11-14
> **paridoth said:**
> So i plug in my digital camera .. and i cant copy them .. it was just working in ubuntu 12.04 that i installed over. help?

This works .. as root ...

$gphoto2 --auto-detect
$gphoto2 --get-all-files

It may be a [Missing udev rule]("https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/72553") ...

---

