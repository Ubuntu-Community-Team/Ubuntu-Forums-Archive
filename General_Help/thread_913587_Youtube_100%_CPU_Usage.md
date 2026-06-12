---
title: "Youtube 100% CPU Usage"
date: 2008-09-07
forum: General Help
---

### Post by solarwind on 2008-09-07
While watching flash videos fully maximized (example Youtube, Megavideo), my CPU goes up 100%. I'm on a laptop with a pentium m 1.86 GHz processor and 1 GB RAM. I'm using macromedia flash plugin on firefox.

Does anyone know how to fix this? My battery wont last long and my processor heats up and causes the fan to spin up fast and gets very noisy.

Note: Not using Compiz Fusion or compositing/desktop effects. Have ATI mobility radeon X300 with drivers installed.

---

### Post by tuxxy on 2008-09-07
Is this problem constantly there or does the browser function correctly sometimes?

---

### Post by solarwind on 2008-09-07
> **tuxxy said:**
> Is this problem constantly there or does the browser function correctly sometimes?
Constantly.

---

### Post by mb_webguy on 2008-09-07
What version of the Flash plugin are you using?  If it's Flash 9 from the multiverse repository, you might want to install Flash 10 from the backports repository and see if you get better performance.

---

### Post by solarwind on 2008-09-07
> **mb_webguy said:**
> What version of the Flash plugin are you using?  If it's Flash 9 from the multiverse repository, you might want to install Flash 10 from the backports repository and see if you get better performance.

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

And how do I install flash 10?

EDIT: Nevermind, I first installed flashplugin-nonfree from the repositories but videos were choppy so I switched back to version 9 from the adobe website.

EDIT: Do you think Gnash would be better?

---

### Post by mb_webguy on 2008-09-07
> EDIT: Do you think Gnash would be better?No, but Flash 10 might be.

Open System->Administration->Software Sources, go to the Updates tab, and check "Unsupported updates (hardy backports)".  Now exit and update your sources.  You should now have several updates available.  Uncheck everything except for flashplugin-nonfree (or leave them checked, if you like), and update your system.  You should now have Flash 10 installed.  If you don't want to have further backported packages included in your updates, go back to Software Sources and uncheck the backports repository.

---

### Post by solarwind on 2008-09-07
> **mb_webguy said:**
> No, but Flash 10 might be.

Open System->Administration->Software Sources, go to the Updates tab, and check "Unsupported updates (hardy backports)".  Now exit and update your sources.  You should now have several updates available.  Uncheck everything except for flashplugin-nonfree (or leave them checked, if you like), and update your system.  You should now have Flash 10 installed.  If you don't want to have further backported packages included in your updates, go back to Software Sources and uncheck the backports repository.

Already tried Flash 10. Same issue.

---

### Post by tuxxy on 2008-09-08
Could be an ATI issue, I had trouble with videos on an ATI card, not overloading like yours, just choppy output and like it struggling to play a simple youtube.

---

### Post by solarwind on 2008-09-08
> **tuxxy said:**
> Could be an ATI issue, I had trouble with videos on an ATI card, not overloading like yours, just choppy output and like it struggling to play a simple youtube.

Update: Getting 100% CPU usage on windows as well (but I'm using an ATI driver that's from 2005 from Dell's driver site). For some reason, official ati driver wont install on windows.

---

### Post by Neo4 on 2008-12-04
Same 100% problem where with a thoshiba with 1.86 centrino 1gb ram and ati x700.

I have an 1000H too and it don't have this problem :S

I guess that is an ati problem :S

If anyone could help it would be great :S movies constantly break with cpu at 100%.

ATI is out of my choice for Graphic cards!

---

### Post by RomanIvanov on 2009-08-22
the same problem for Atlon 1000Mhz, NViDIA GeForce4MX 440, NVidia drivers are installed ver 96.43.10. Sound play fine, but images are slowed. Does anybody cope the problem ?

---

