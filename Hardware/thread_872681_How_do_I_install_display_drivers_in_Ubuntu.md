---
title: "How do I install display drivers in Ubuntu?"
date: 2008-07-28
forum: Hardware
---

### Post by jdenicholls on 2008-07-28
I've downloaded a display driver for my graphics card from the NVIDIA website and saved it in a file of the right format. I need to get my graphics card working so I can play Valve games in WINE. How do I install the display driver?

---

### Post by tuxxy on 2008-07-28
System > Administration > Hardware Drivers

There should be one listed for you to enable there.

If its not listed you could try an app named Envy, search for it the repos.

---

### Post by jdenicholls on 2008-07-28
It comes back with "No propriety drivers in use on this system". Does that mean I need to go look for some?

Sorry for my noobishness.

---

### Post by tuxxy on 2008-07-28
Try an install them via Envyng now, search for it in the repos or install from terminal by typing;

```
sudo apt-get install envyng-gtk
```

Now run it from your maiun menu,

Good Luck

---

### Post by jdenicholls on 2008-07-28
I tried that and everytime it prompts me for the password I can't seem to type anything in. Is that normal?

Edit: Don't worry. Got it.

---

### Post by jdenicholls on 2008-07-28
Ok I have a new problem. It appears the drivers installed even though I cannot see them in Hardware Drivers, because the programme Steam prompts me with a warning message saying that the drivers I've installed are outdated.

Continuing anyway I try to load the game Team Fortress 2, but as soon I connect to a server the game crashes with the following "Engine Error"

failed to lock vertex buffer in CMeshDX8::Lock Vertex Buffer

Any suggestions? Thanks for your help so far.

---

