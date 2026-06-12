---
title: "Compiz won't start with External Monitor"
date: 2009-03-30
forum: Hardware
---

### Post by christophski on 2009-03-30
Just got a secondhand monitor to use as an external monitor for my laptop. Got it all working through the screen resolution program but now when I log in compiz won't start. If I run it from the termional with "compiz --replace" I get an error:
```

christie@christie-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 
```
I went through compiz settings manager but couldn't find an option for maximum 3d texture :s I tried putting the texture filter to "fast" but that didn't help.
Does anybody know what the problem is?

---

### Post by christophski on 2009-04-03
I found away around this, by setting the "screen resolution" app to put one monitor on top of the other instead of side-by-side. But this really isn't optimal and it doesn't change back to one desktop when I unplug the monitor, I have to log out and then log back in.

---

