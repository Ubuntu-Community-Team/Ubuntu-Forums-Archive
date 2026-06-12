---
title: "Wine/Mono/.NET question"
date: 2008-11-18
forum: General Help
---

### Post by Cracauer on 2008-11-18
I have this application.... OK it's a game.  Anyway, the thing used to work fine in Wine (public version and Cedega), but then the author decided to add some random .net stuff.  In know all the core application is still a C++ binary, but now it won't run in those newer patches.  I have no information about what exactly he's doing in .NET, but as a general question:

How would I go about making Wine .net aware and try to have the .net stuff executed in Mono? If I would just install Mono Wine would never call it, obviously.

Anybody has an idea whether this is even on the horizon of Wine and MONO?

---

### Post by directhex on 2008-11-18
Try installing Mono for Windows, in Wine.

That's the official way to add .NET powers to Wine.

---

### Post by Cracauer on 2008-11-18
> **directhex said:**
> Try installing Mono for Windows, in Wine.  

That's the official way to add .NET powers to Wine.  

They have Mono for Win32? [img]http://www.cons.org/smileys/nuts.gif[/img]  

My brain blew a fuse there for a second, but now it makes perfect sense.  

Thanks, that sounds *exactly* like the bit I was missing.

---

