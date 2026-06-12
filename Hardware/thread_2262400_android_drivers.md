---
title: "android drivers"
date: 2015-01-24
forum: Hardware
---

### Post by redhern on 2015-01-24
I have a tablet that I'm having difficulty locating linux drivers for. The manufacturer, Lenovo, provides Android source code for it on their website. Is there a way I can get firmware out of that source code and compile it for my ubuntu setup?

I'm pretty new to linux and most of my searching isn't really helping.

Thank you in advance!

---

### Post by ajgreeny on 2015-01-24
I am not sure what you want to do; are you trying to mount the Android tablet in Ubuntu and allow yourself to move files to and from it, or do you want to do something more that I can not understand from your post.

If all you want to do is mount and view/drag/drop files to and from the Android tablet follow the info at [http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702) which seems to work for many different makes of Android tablet and phone.

---

### Post by redhern on 2015-01-24
Sorry, I should have been more clear.

The tablet originally came with Android installed on it and I formatted it and installed Ubuntu.

The problem is that there are some hardware drivers I cannot locate for Linux, so like my wifi and Bluetooth do not work. 

Lenovo has released the source code for the Android OS that it originally came with, including those drivers. Can I use the Android wifi/Bluetooth drivers in Ubuntu?

---

### Post by ajgreeny on 2015-01-25
I would be surprised if you can use those android drivers in Ubuntu, but I suppose that if you can get the source code of them, you may be able to build them yourself and install them.  Otherwise I have no ideas where else you could go for them; do you even know the wireless chip used; presumably command **lspci** might tell you something.

---

