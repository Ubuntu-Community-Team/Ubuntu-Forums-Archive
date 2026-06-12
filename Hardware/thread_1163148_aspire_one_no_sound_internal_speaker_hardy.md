---
title: "aspire one no sound internal speaker hardy"
date: 2009-05-18
forum: Hardware
---

### Post by trikster_x on 2009-05-18
I have an aspire one with 1.5 gb ram and 120 gb hdd and hardy installed.  When I first installed, my internal speakers worked fine, but after plugging in my headphones one time, the internal speakers were completely disabled.  I have full control of the volume and alsamixer, but nothing comes out of the speakers.  I have followed every bit of instructions here:
[https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")
Nothing is solving the problem.  I currently have alsa 1.0.18 installed.  Sound does work fine through my headphones still.

EDIT:
When I unload alsa, I get an error.
```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/alex/.gvfs
      Output information may be incomplete.
```

It isn't fatal, alsa still unloads, but I am wondering if maybe it is part of the problem?

---

### Post by trikster_x on 2009-05-18
Any help at all would be greatly appreciated.

---

### Post by trikster_x on 2009-05-19
gotta be someone who can help...

---

### Post by trikster_x on 2009-05-20
Nobody even has a suggestion?

---

### Post by trikster_x on 2009-05-22
Heh....  I figured it out.  I had my lappy apart to add some ram to it, and I didn't gt the speakers plugged back in all the way.  The plug must have popped out at the same time I plugged my headphones in.  Sorry, but I doubt this fix will help anyone but me.

---

