---
title: "window borders (decorations) are missing"
date: 2008-10-26
forum: General Help
---

### Post by dev.urandom on 2008-10-26
I'm trying out compiz just for the hell of it, but I can't get it working properly. All effects are working correctly, except the window decorations. The plugin is active, according to ccsm, and gtk-window-decorator is running. But there are no borders to be found. No shadows either, which I guess are also drawn by this plugin. So what gives?

I'm running on HH, with the only modification being that I've removed the nvidia drivers, supplied by the repositories, and I've installed the official ones from nvidia. I'm running 177.80.

---

### Post by hictio on 2008-10-26
> 
I'm running on HH, with the only modification being that I've removed the nvidia drivers, supplied by the repositories, and I've installed the official ones from nvidia. I'm running 177.80.


If I might ask, why did you do that?
I don't have top of the line NVIDIA cards (GeForce 7000M on the laptop & GeForce2 MX/MX 400 on an old box) but on both cases the drivers supplied by Ubuntu worked like a champ.
 
If you execute Compiz from a terminal, do you have any output?

---

### Post by dev.urandom on 2008-10-27
I come from slackware, so I've retained my natural instinct to install up-to-date stuff.

Now, regarding the output:
```

$ compiz
Checking for Xgl: not present. 
FATAL: Module battery not found.
Detected PCI ID for VGA: 01:00.0 0300: 10de:0427 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

That's it, compiz starts, no borders though. Other effects are there.

---

### Post by Yashiro on 2008-10-27
Turn off desktop effects totally. Re-enable it.
There's some weirdness in the way the Window Decorator Plug-in works.
(gtk-window-decorator --replace is the string that should be there within that plug ins set-up)

---

### Post by dev.urandom on 2008-10-27
just tried disabling everything, then enabling the decorator, but nothing usual happened. removed .config/compiz and .gconf/apps/compiz, and still nothing. Even running gtk-window-decorator --replace manually after starting a plugin-less compiz didn't show the window borders.

---

### Post by hictio on 2008-10-27
I start Compiz (& Emerald) like this:
```

/usr/bin/compiz --replace ccp & /usr/bin/emerald --replace &

```

Perhaps you can give it a shot?

---

