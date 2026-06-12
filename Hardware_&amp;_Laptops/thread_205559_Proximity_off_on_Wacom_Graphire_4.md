---
title: "Proximity off on Wacom Graphire 4"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by Ertain on 2006-06-28
Hello everyone.  I'm new to the forums so bear with me on this one.

I've checked through *all* of the how-to's and looked on the linux wacom website, but I still can't get my tablet to draw and work properly. ](*,)

When the stylus even comes within a centimeter of the drawing surface it is registered as a button press.  It is suppose to register as a button press when the stylus *touches* the drawing surface.

If anyone wants to know, I'm using the 0.7.4 driver version on a Graphire 4 tablet.

Thank you for your time.

---

### Post by Ertain on 2006-06-29
More on my situation.

Though "/dev/input/event3" is my Wacom tablet, when I use wacdump nothing is shown on it.  I can move the cursor around with my tablet but nothing is recorded by wacdump.

---

### Post by rlaska on 2006-12-29
Sorry I'm reading this late, you might already have it working, or have given up.
But just in case you haven't... have you tried using /dev/input/wacom? I'm using a graphire4 on Edgy.

---

### Post by saxofoner on 2006-12-30
You can use dev/input/wacom if you install wacom-tools.  Google around.  Once you do that, check this page out:
[http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)
And that's wrong, it says it's in some xf86 folder or something it's actually:
sudo gedit /etc/X11/xorg.conf
And you stick all those wacom things in where you see it.  There's also a graphical Wacom config program in the works, it looks quite interesting.

---

