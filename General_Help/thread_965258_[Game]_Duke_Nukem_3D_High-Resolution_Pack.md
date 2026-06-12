---
title: "[Game] Duke Nukem 3D High-Resolution Pack"
date: 2008-10-31
forum: General Help
---

### Post by kakyoism on 2008-10-31
Hi,

Remember the best FPS of all-time? I want to compile eDuke+HRP on Hardy, but never succeeded.
Anybody had a better luck?

Thx!

---

### Post by geirha on 2008-10-31
This one? [http://wiki.eduke32.com/stuff/source_code/](http://wiki.eduke32.com/stuff/source_code/)

I downloaded and built it just now to test. Built fine, but I'm unable to run it, as I apparently need some data files.

What errors are you getting?

---

### Post by kakyoism on 2008-10-31
ok, I tried the 20081014 one and it compiled. 
But there isn't a "make install" command available.
How do I install and run it? I have the game data, but can't 
find instructions in README.

---

### Post by geirha on 2008-10-31
Guess they just haven't bothered to provide a way to install it. I ran it from the same directory as I ran make, and it seemed ok with that.

---

### Post by kakyoism on 2008-10-31
do you mean you just copy game data to the same directory and run it?
I remember it was a windows appliacation, so how do I run it anyway?
Thanks a million~

---

### Post by geirha on 2008-10-31
Seems to be documented at their wiki [http://wiki.eduke32.com/wiki/Building_EDuke32_on_Linux](http://wiki.eduke32.com/wiki/Building_EDuke32_on_Linux)

---

### Post by regor210 on 2008-11-01
I just played the best looking Duke Nukem 3D ever via Wine and jfduke3d.

[http://www.jonof.id.au/index.php?p=downloads&cat=1](http://www.jonof.id.au/index.php?p=downloads&cat=1)

jfduke3d ports Duke3D to Windows and worked well with Wine. Can someone else try it and see if works as well for you as it did for me?

Im using AMD 64 X2 dual core  2G  GeForce 8400 GS 512mb Hardy Wine 1.1.7

---

### Post by porcho on 2009-05-19
Just tried to use JFDuke3D port today, and everything works fine, except the music! Almost shed a tear of emotion here! :-)

I've downloaded the JFDuke3D (installer package) from here: [http://www.jonof.id.au/downloads?cat=1](http://www.jonof.id.au/downloads?cat=1). Then I runned it with Wine and pointed to a directory containing the duke3d.cfg file.

I'll try the HRP now!

Cheers,

---

### Post by Volt9000 on 2009-05-19
JFDuke3D ran well under WINE, except for a few things:

- A few of the textures are messed up. For example, the racks in the porno shop in Red Light District are all stretched, and some of the animated water textures look completely messed up.
- Enemy animations are strange-- when a trooper or pigcop is walking, the animation will momentarily switch to the frame when they're frozen. A bit annoying.

The problem is I can't play EDuke32 at all under WINE. With mouselook the mouse constantly "snaps back" to the origin so I can't aim with it.

---

### Post by porcho on 2009-05-20
> The problem is I can't play EDuke32 at all under WINE. With mouselook the mouse constantly "snaps back" to the origin so I can't aim with it. 

I'm facing the same problem. Everything seems fine, except the mouse!

---

### Post by tallquasimodo on 2009-07-13
Having the same problem, permanent lookspring.  Can't think of a way out of it, and I've messed with the cfg files until I couldn't see straight.

---

### Post by kakyoism on 2009-07-13
Hey, this problem is solved.
Just make sure you have all the original GRP files, configs, HRP textures, and/or custom maps under $HOME/.eduke32/

and run:

$PATH_TO_EDUKE32/eduke32 /gsd_duke.grp /gsd_duke.grp

---

