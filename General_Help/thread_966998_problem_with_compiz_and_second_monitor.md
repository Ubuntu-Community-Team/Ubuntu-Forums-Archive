---
title: "problem with compiz and second monitor"
date: 2008-11-01
forum: General Help
---

### Post by lugburz on 2008-11-01
I'm trying to setup the external monitor of my laptop (model sony sz1) but when I use the display property applet I have to restart the X server and if the external LCD monitor is attached the X-server starts showing only a part of the desktop. 

The external LCD monitor is a wide-screen display and is recognized as a 4:3 screen.

The new configuration to attempt to use both monitors enlarge also the virtual size, this disables the compiz effect.

These are three different bugs but both connect with a screen configuration proble, anyone knows how to manage them?

thanks, in advance

---

### Post by loomsen on 2008-11-01
[Why these bugs aren't bugs](http://ubuntuforums.org/showthread.php?p=6070424#post6070424)
And also what you can do against.

If you can't follow me, maybe try and read 
[this for a simple approach to what X is and what X does.](http://ubuntuforums.org/showpost.php?p=5939543&postcount=6)

If you can follow me, you'll see that these "bugs" are actually in the nature of things.

---

### Post by lugburz on 2008-11-01
Well OK they are not bugs of the X server but gnome-display-properties is doing something wrong. Accordinng the first of your two links I'm in the first condition but I don't understand:

1. How to set the otuput TV-LCD monitor to work at 144x900

2. That this external screen is not the one has to contain the gnome bars

These are not bugs but important limitation.

PS the xorg.conf file I'm using is this:

```
Section "Screen"
        Identifier      "Configured Screen Device"
        Device  "Configured Video Device"
        SubSection "Display"
                Virtual 2640 800
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

```

---

