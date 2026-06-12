---
title: "Breezy on Dell D810 Lattitude eraser mouse problem."
date: 2006-03-11
forum: Hardware &amp; Laptops
---

### Post by supervij on 2006-03-11
Hello All,

I have been using fedora and debian testing/unstable for years and I just finally tried out Ubuntu.  As a community, you guys have done a great job in making Linux extremely user-friendly. After installing Ubuntu on my dell d810 lattitude, I was just amazed that everything worked so perfectly out of the box.  (It usually takes me about a day to download all the updates, etc with fedora and then fix settings, etc).

Currently I have a pretty much up-to-date system running with the i686-linux image.  

I noticed that every other boot (or every two boots) that the touchpad and the mouse buttons below it work while the eraser mouse and it's mouse buttons do not.  What's really weird is that all I need to do is reboot and both mice work again.

Has anyone seen this kind of problem?  


If you guys need more information on my setup, please let me know.

SuperVij

---

### Post by supervij on 2006-03-12
Hello All,

I found a solution to a similar problem here:

[http://www.ubuntuforums.org/archive/index.php/t-77612.html](http://www.ubuntuforums.org/archive/index.php/t-77612.html)

(I forgot that both mice (touchpad and eraser) are both ps2 mice)

The gist of it is, for whatever reason, the psmouse module doesn't find all the mice on my laptop or fails/ignores on one mouse during startup. Apparently, a simple restart of the service was enough to correct the problem.

So this is what I did:

sudo modprobe -r psmouse
sudo modprobe psmouse


Regards,

SuperVij

---

