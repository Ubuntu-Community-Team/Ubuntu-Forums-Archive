---
title: "compiz problem"
date: 2008-07-22
forum: General Help
---

### Post by infiniah on 2008-07-22
I'm trying to run compiz so I can set up my desktop effects...
```
infinia@infinia-linux:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0622 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.




```

That is the error I receive, I am clueless as to how to fix it.

---

### Post by infiniah on 2008-07-22
bump

---

### Post by northern lights on 2008-07-22
Run ```
gconf-editor
``` and navigate to the path listed in the error message, i.e. ```
/apps/compiz/plugins/scale/allscreens/options/initiate_edge
``` and remove the value.

This error is common after an upgrade of compiz from version without to version with the image of the screen to set the mouse binding. A distribution upgrade from Gutsy to Hardy may have the same effect.

---

### Post by knutschr on 2008-07-22
I have in terminal too, when installing compiz-icon been asked to go there, but I don't even have /apps :-(

---

### Post by northern lights on 2008-07-22
@knutschr:
I'm not sure you're indeed having the same problem, but in case you do, it's first off /apps, not /apts and foremost that is not a directory in your filesystem, but a path within "gconf-editor"...

---

### Post by knutschr on 2008-07-22
Thanks for your answer!
I have /apps/compiz/plugins/scale, but there is no allscreen there :-(

---

### Post by northern lights on 2008-07-22
You don't have the path but the exact path appears in _your_ error message?

Would leave me clueless.

--> Completely remove compiz and reinstall. Best Bet, then.

---

### Post by infiniah on 2008-07-23
There is no value I don't think...
[IMG]http://img.photobucket.com/albums/v651/tristanbuke121/Screenshot.png[/IMG]

When I right click and go edit value there isn't any.
Okay so i decided to add a "1" as a value and it doesn't give me the previous error anymore.
I get this now:
```

infinia@infinia-linux:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0622 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```

All I want to do is go to Advanced Desktop Settings... This is such a hassle...

---

### Post by northern lights on 2008-07-23
Can't you set it to "Disabled"?

---

### Post by infiniah on 2008-07-23
I can but It keeps the error message.

---

### Post by infiniah on 2008-07-23
Nevermind,
I set it to disabled.
But I'm still getting the other error...
```

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

### Post by infiniah on 2008-07-23
bump...

---

### Post by northern lights on 2008-07-23
```
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```is a warning, not an error.

It means Xorg does not support alpha-only GLX visuals so if you use the mplayer patch to make it use the compiz video plugin mplayer has to convert the video to RGB before handing it to compiz. (Amaranth)

Your compiz should work...

Try enabling desktop effects from the "System > Preferences > Appearance" menu ("Visual Effects" tab) or press "Alt+F2" and run compiz from there.

---

### Post by infiniah on 2008-07-23
... Guess what, compizconfig-settings-manager was not installed... that is strange because this is the first time I installed ubuntu without it already on?

---

### Post by northern lights on 2008-07-23
> **infiniah said:**
> ... Guess what, compizconfig-settings-manager was not installed... that is strange because this is the first time I installed ubuntu without it already on?

Might be so - dunno what sort of distro you used previously. However, in general, ccsm is not installed after a fresh setup...

---

