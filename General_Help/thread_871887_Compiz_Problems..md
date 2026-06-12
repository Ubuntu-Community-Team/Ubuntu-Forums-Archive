---
title: "Compiz Problems."
date: 2008-07-27
forum: General Help
---

### Post by Bruce-Wayne on 2008-07-27
Right, I am having problems getting Compiz to run on Ubuntu 8.04.
When I put 'compiz' into the terminal I get this:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27ae (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
```

The graphics chip in my laptop is an Intel 945GME, which might be of some significance.
I have tried everything I can think of, which isn't much, since I don't really know what I'm doing. So I would really appreciate some help.
Thanks.

---

### Post by cdtech on 2008-07-27
Check out this thread:
[[COLOR="DarkRed"]compiz-check[/COLOR]]("http://ubuntuforums.org/showthread.php?t=799070&highlight=compiz-check")

Hope this helps......

---

### Post by Bruce-Wayne on 2008-07-27
Well, now I know that Compiz *should* run properly...
Yet it doesn't...
I did however do some research, and apparently my graphics chip (Intel 945GME) is blacklisted somewhere. Any pointers?

---

