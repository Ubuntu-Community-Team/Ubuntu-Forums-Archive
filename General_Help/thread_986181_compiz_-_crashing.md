---
title: "compiz - crashing"
date: 2008-11-18
forum: General Help
---

### Post by greenmanu on 2008-11-18
Hi, Loving Ubuntu, well I was untill I crashed compiz when playing arround with 3d effects settings.when I login I am getting that screen where it looks like the refresh rate is set too high.
and it just crashes out.:shock:

I have tried 
recovery mode choose the option Fix xserver but had no joy

How can I reset my compiz default settings. from the Terminal.

Thanks All

---

### Post by cdaringe on 2008-11-18
hhmmm...
maybe by turning metacity on...
```

metacity --replace 

```
you can go back into your compiz settings and set them to default graphically?

you could even install kde-core, log into a kde session, and then browse to your compiz settings...but that would be a verrrrry roundabout method :)
```

sudo apt-get install kde-core

```

im sure one of these fellers will have a more solid solution, but try the first one...if that doesn't work...try the second!

---

### Post by prshah on 2008-11-18
> **greenmanu said:**
> 
How can I reset my compiz default settings. from the Terminal.


If you can see the login screen, press F10 _before_ entering your username and/or password, then choose "Failsafe session"; once you are logged in, make changes to your resolution using System-Preferences-Screen Resolution, then log out and log back in with a regular gnome session. 

Post back if you still have troubles.

---

