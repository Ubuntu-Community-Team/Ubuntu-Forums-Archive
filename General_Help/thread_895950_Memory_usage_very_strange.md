---
title: "Memory usage very strange"
date: 2008-08-20
forum: General Help
---

### Post by MatthijsL on 2008-08-20
Running Ubuntu hardy Heron on a pentium Dual Core 2.8 ghz packardbell box with GNOME, compiz, emerald. Onboard video. i have the tracker applet disabled a friend told me this drains resources.

I've been monitoring my memory usage just for the fun of it but suddenly discovered something im not liking.. that being.. 

at boot i start pidgin and check systemmonitor for the memory usage.

memory usage is 210 mb of 756mb (ddr2 ram) and no swap usage.
then withing 2 minutes without doing anything else then just watching the counter it goes up too a wopping 450 mb out of 756mb. and no swap usage.

then after about 15 minutes or so it drops down by about a 100 mb before rising up to 450 again fast.

what the hell is happening ? does anyone have experience with this?

---

### Post by tuxxy on 2008-08-20
Whats using all the memory pidgin? im not so sure as I dont use, maybe think about a replacement app see if it alters anything?

---

### Post by mb_webguy on 2008-08-20
Rather than using System Monitor, try typing "top" in the command line, and then type ">" once to move the sort field to the %MEM column (or "h" to view the various other commands).  Watch for any unusually high values and make a note of which processes are responsible.  This should give you a more reliable picture of what's going on with your system than System Monitor.

---

### Post by MatthijsL on 2008-08-21
> **tuxxy said:**
> Whats using all the memory pidgin? im not so sure as I dont use, maybe think about a replacement app see if it alters anything?

at processes pidgin just stays at a 27.1 mb value just like all the other programs...

---

