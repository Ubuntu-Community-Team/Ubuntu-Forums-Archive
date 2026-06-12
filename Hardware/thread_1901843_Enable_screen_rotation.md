---
title: "Enable screen rotation"
date: 2011-12-29
forum: Hardware
---

### Post by natman on 2011-12-29
Hi,
I am using a HP Elite book, one of those laptops where you can rotate the screen and use it as a tablet, In windows the when i rotate the screen the orientation changes, how do i enable this on ubuntu?

---

### Post by Favux on 2011-12-29
Hi natman,

Magick Rotation:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)
Rotation HOW TO:  [http://ubuntuforums.org/showpost.php?p=6274392&postcount=1](http://ubuntuforums.org/showpost.php?p=6274392&postcount=1)

---

### Post by natman on 2011-12-31
Wow thanks, magick rotation does the job almost there is a mix up with the mouse after rotation, but was able to fix it using this ( comment #3 )
[https://bugs.launchpad.net/magick-rotation/+bug/744274](https://bugs.launchpad.net/magick-rotation/+bug/744274)

Thanks:

---

### Post by Favux on 2011-12-31
Great!  Natty and Oneiric have a version of xf86-input-wacom where a bug causes left and right Portrait orientation to be swapped for the stylus, etc.  There is a FAQ for updating xf86-input-wacom so you get the cw and ccw swap bug fix.

---

