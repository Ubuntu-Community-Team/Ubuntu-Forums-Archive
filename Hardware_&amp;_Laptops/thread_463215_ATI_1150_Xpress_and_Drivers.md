---
title: "ATI 1150 Xpress and Drivers"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by lsutiger on 2007-06-03
I have tried several tutorials and Envy to get this to work, but I keep failing.
I am attaching a screen shot of the restricted drivers says "Not in use".
And the terminal Output:
```
sudo glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

When I tried to do a manual install following instructions [from this site]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide"), I get an error from the module assistant during ```
sudo module-assistant build fglrx
```. 
Any help would be apprciated!

---

### Post by lsutiger on 2007-06-04
Bump

---

### Post by bone43 on 2007-06-04
Take a look at this one..

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

This should work but if you are trying to get beryl to work with the ATI X series you will need to run a XGL session in Gnome or KDE along with doing a few some other things.

---

### Post by lsutiger on 2007-06-04
Nah, didn't work...still the same. But thanx for the input

---

### Post by lsutiger on 2007-06-06
Bump

---

