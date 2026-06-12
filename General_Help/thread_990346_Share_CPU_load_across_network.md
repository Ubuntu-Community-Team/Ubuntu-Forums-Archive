---
title: "Share CPU load across network"
date: 2008-11-22
forum: General Help
---

### Post by kev717 on 2008-11-22
Every computer I have on my network is running Linux (two ubuntu, one fedora).  I was wondering if there was a way to share the load on my main machine (2.5GHz single core computer with 512MB ram) with the rest of the machines on my network.  In other words... I want my machine to send the processor commands over to my idle computer to get it to process the command and leave my main machine free to do other stuff.  Is this possible?

Basically I'm just doing some heavy rendering of 3D models and stuff like that.  I'm hoping to get the time it takes to render one model to under 2 hours

---

### Post by jyaan on 2008-11-22
I'm not sure if this will work how you want, but you can forward X over ssh or the like. Just start ssh with the -X flag. The DISPLAY variable needs to be correct also, but it should set automatically.
```
ssh -X username@serverip
```

This way, the X server runs the process on the main computer (server)  that you want to spend resources on, and the X client that runs on the desktop PC will just draw the window. 

Since this is using CLI, it's not a nice interface, but it is simple enough for me. Screen can be helpful if the connection breaks, as it will continue to run processes inside it without interruption. There may be some kind of GUI to assist you, but I haven't looked for one since this suits my needs.

Hopefully this is what you're looking for.

If you're trying to set up a rendering farm with all of the other PC's, that is beyond what I know. Sorry. =/

---

