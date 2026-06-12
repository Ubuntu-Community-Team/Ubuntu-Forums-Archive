---
title: "quake4-smp (1.4.2) crashes when entering level, 8.04"
date: 2008-08-04
forum: General Help
---

### Post by Dacobi on 2008-08-04
Hello All

I Just installed Quake 4 on my brand new Core 2 Quad.
enabled smp and ran quake4-smp.

It loads and runs in the menu and also loads the levels but crashes when trying to enter the level:

It gives the following error:
---------------------------------------------
-------- idSoundCache::EndLevelLoad ---------
1.43 seconds to expand oggs
17978k referenced
    0k purged
---------------------------------------------
---------------------------------------------
 26720 msec to load game/airdefense2
idRenderWorld::GenerateAllInteractions, msec = 0, staticAllocCount = 0.
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
------------ Game Map Shutdown --------------
---------------------------------------------
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
double fault Segmentation fault, bailing out
shutdown terminal support
:~$

Does anyone know how to fix this?

/Dacobi

---

### Post by Brebs on 2008-08-04
Nvidia card? See [NoFlip xorg option](http://forums.gentoo.org/viewtopic-t-535450.html).

---

### Post by Dacobi on 2008-08-04
It's a Radeon HD4870..

---

### Post by Dacobi on 2008-08-04
*bump*

Anyone?

It will also run the intro up to the point where you enter the ship and then crash.

Running smooth with SMP disabled..

/Dacobi

---

### Post by Reugen on 2008-09-08
Do you have AA set? If so try resetting to defaults then upping the settings again without AA, worked for me.

found that here:
[http://www.rage3d.com/board/showthread.php?t=33929548](http://www.rage3d.com/board/showthread.php?t=33929548)

---

