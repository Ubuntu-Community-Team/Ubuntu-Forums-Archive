---
title: "Ubuntu upgrade (8.04 -&gt; 8.10) broke OpenGL/SDL/something"
date: 2008-11-11
forum: General Help
---

### Post by Sydius on 2008-11-11
I upgraded my laptop from Ubuntu 8.04 to 8.10 via the update manager while working on a project of mine.  It is a game that uses OpenGL, SDL, and CEGUI.  It was working fine before and during the first half of the upgrade.  While installing software, however, the graphics suddenly went odd (I was running the game at the time).  I wrote it off as a fluke, but ever since, it has continued to be odd on this laptop.  I have recompiled the game many times, recompiled all of the supporting libraries that I installed from source (CEGUI, boost), but nothing makes any difference.

It looks right when the program first starts, but quickly degrades.  Some of the textures become corrupt looking while others don't seem to draw at all.  Oddly, the interface provided by CEGUI doesn't seem to ever be affected.  Also, when I click on the game with the mouse, it flickers black for a moment.

None of that happened before upgrading.  None of the code changed.  In fact, it works fine on three other computers I've tested it on, all running Ubuntu 8.10 (all upgraded in the same way).  Two have nicer hardware, another worse, but none have this problem.

I'll post a comparison screen shot.  Does anyone have any hints as to what I might do to fix it? Reinstall something, maybe? Hopefully not the whole OS...

The way it is supposed to look can be seen at [http://code.google.com/p/odysi](http://code.google.com/p/odysi)

The broken graphics are OpenGL quads.

The laptop is a Lenovo Thinkpad X60s.

---

### Post by Neo_The_User on 2008-11-11
Playing a game while updating mesa, OpenGL libraries, gnome and all that stuff (the 8.04 to 8.10 upgrade) is not a good idea. You can try launching this command in recovery mode (resume normal boot NOT fix X)

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

Restart your computer

```

sudo shutdown -r now

```

Boot into the normal kernel (not recovery) and see if that works. If it doesn't keep me posted. btw, what GPU do you use?

---

### Post by Sydius on 2008-11-11
I did what you suggested and it didn't make a difference.  I should note that it's only the game that has any problems.  Nothing else seems to, other than the "Suspend" icon being missing.

Is there a way to reinstall the OpenGL libraries?

---

### Post by Sydius on 2008-11-11
The textures are definitely loading correctly because they display correctly for the first second or so.  They're loaded and turned into OpenGL textures, so they should be sitting in OpenGL's memory.  After a couple seconds, they all become corrupted in one way or another.  Given that they are already under OpenGL's control, that leads me to believe it must be the Mesa 3D driver's fault.  I was able to reproduce it with another crappy integrated video laptop by upgrading to Ubuntu 8.10.

Is there a way to revert to older Mesa drivers?

---

### Post by Sydius on 2008-11-11
Definitely Mesa.  I installed Mesa 6.5.x (software rendering) and it works fine.

---

### Post by Sydius on 2008-11-12
I filed a bug report here: [https://bugs.freedesktop.org/show_bug.cgi?id=18508](https://bugs.freedesktop.org/show_bug.cgi?id=18508)

---

### Post by paulcrisafulli on 2008-11-23
I upgraded to 8.10 but now my wireless card isn't working and i cant get the driver for it what should i do?

---

