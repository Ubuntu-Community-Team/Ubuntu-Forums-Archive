---
title: "Updating Intel Mobile Driver 945GM for dummies?"
date: 2009-12-08
forum: Hardware
---

### Post by Charkel on 2009-12-08
Hello. I believe I have to update my drivers to get OpenGL 2 since I get this error when running a game:
> Fatal Error: OpenGL 2.0 not available.


I've tried to find info on my own on how to update but it seems very advanced. Can anyone please help me how to do it.
I looked at this [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html) and found this: [http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html) - Is there really no easier way? :(

This my my GFX info:
> VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)


Thank you.

EDIT:
Seems like there is no openGL 2 drivers for linux and intel. Is this true? :'( If so I have to go back to windows :(

---

### Post by triplesick on 2009-12-08
if you want to try updating your driver to an unstable but newer one, use this guy; very simple process but risky.
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

i don't really know about opengl versions; what are you trying to play?  i am able to get Quake 3 arena to run on my intel card (unplayable, but it runs nonetheless), which is definitely an opengl game, but i'm not sure if it's 2.0.

generally speaking though, windows is a better bet for games :( for intel cards, the linux drivers get about 1/4 the performance that the windows drivers get.

---

### Post by Charkel on 2009-12-18
> **triplesick said:**
> if you want to try updating your driver to an unstable but newer one, use this guy; very simple process but risky.
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

i don't really know about opengl versions; what are you trying to play?  i am able to get Quake 3 arena to run on my intel card (unplayable, but it runs nonetheless), which is definitely an opengl game, but i'm not sure if it's 2.0.

generally speaking though, windows is a better bet for games :( for intel cards, the linux drivers get about 1/4 the performance that the windows drivers get.

Tried to play Heroes Of Newerth. Managed to get it to run by installing mesa. I managed to start it but the lag was so heavy i couln't do anything. My card can handle it in Windows. But I guess there isn't enough drivers made for Linux yet :(

---

