---
title: "Compiz q's"
date: 2008-07-17
forum: General Help
---

### Post by pudgy parrot on 2008-07-17
Yesterday, I was able to use compiz to do some cool effects.  It got late, I shut down.

Today, when I went to start my Xubuntu, it hung up.  I rebooted, the machine started fine, and now cant start up compiz.  I've tried reinstalling, and all sorts of other things.  Can anyone shed any light on this?  

I really liked those effects.

---

### Post by Locutus_of_Borg on 2008-07-17
```
compiz --replace
```

what is the output?

---

### Post by tuxxy on 2008-07-17
Wwhats the output of compiz in the terminal

---

### Post by pudgy parrot on 2008-07-17
-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:29c2 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'dbus'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'place'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'move'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'resize'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'decoration'
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/libpng.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'png'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'svg'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'imgjpeg'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'text'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'neg'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'video'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'wall'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'snap'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'animation'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'scale'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'scaleaddon'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'scalefilter'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'expo'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'switcher'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'regex'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'resizeinfo'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'workarounds'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ezoom'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'vpswitch'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'extrawm'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'fade'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'session'

---

### Post by tuxxy on 2008-07-17
[http://ubuntuforums.org/archive/index.php/t-770846.html](http://ubuntuforums.org/archive/index.php/t-770846.html)

could be either wrong driver or compiz version

---

### Post by Locutus_of_Borg on 2008-07-17
What driver do you use?

```
 cat /etc/X11/xorg.conf | grep Driver 
```

---

### Post by pudgy parrot on 2008-07-17
cat /etc/X11/xorg.conf | grep Driver
	Driver		"kbd"
	Driver		"mouse"

---

### Post by tuxxy on 2008-07-17
I the output you should have one labelled nVidia, try
```

 glxinfo | grep 'OpenGL vendor'
```

If nothin oin nVidia try re-installing your nVidia driver,

```
sudo jockey-gtk
```

---

### Post by pudgy parrot on 2008-07-17
The output I get re: Nvidia is:

OpenGL vendor string: Tungsten Graphics, Inc


Will downloading the new driver affect any of my windows programs or solely my Ubuntu?

---

### Post by Vadi on 2008-07-17
It'll be purely Ubuntu.

---

### Post by pudgy parrot on 2008-07-17
Thanks, I'll download that driver later when I get home.  Will I have to install all of the plugins after that too?

---

### Post by Vadi on 2008-07-17
Nah, I don't think you'd need to.

---

### Post by pudgy parrot on 2008-07-17
> **tuxxy said:**
> I the output you should have one labelled nVidia, try
```

 glxinfo | grep 'OpenGL vendor'
```

If nothin oin nVidia try re-installing your nVidia driver,

```
sudo jockey-gtk
```

When I run the second code, I get a message stating that "no propietary drivers are in use on this system".

I have an integrated Intel Graphics Media Accelerater 3100 Card, shouldn't I download some Intel driver instead?  If not, can you be more specific which nVidia driver I would download?

---

