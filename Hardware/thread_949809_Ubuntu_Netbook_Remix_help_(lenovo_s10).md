---
title: "Ubuntu Netbook Remix help (lenovo s10)"
date: 2008-10-16
forum: Hardware
---

### Post by flammenwurfer on 2008-10-16
Has anybody installed the netbook remix packages and gotten them working correctly?  I followed the instructions [https://launchpad.net/netbook-remix]("https://launchpad.net/netbook-remix")and it sort of works, but when I'm at the main netbook remix screen the top panel disappears, but parts will reappear if I move the mouse over them.  Also, when I start an application most of the application screen is missing except for parts that will reappear when I move the mouse over them or click on something.  

Is this a driver issue?  Anybody else experiencing similar behavior?

PS.  I really like the netbook remix interface.  The parts of it that work anyways.

---

### Post by njpatel on 2008-10-17
Hi, this sounds almost certainly to be an issue because you have Compiz or Metacity-composited running. Intel video cards can't composite opengl windows, so you get both the compositor and the open gl window fighting to draw on the screen :-).

Switching off Visual Effects from Preferences->Appearance->Visual Effects should fix the problem for you.

---

### Post by flammenwurfer on 2008-10-17
Interesting.  Are the visual effects turned on by default?  Because I didn't turn them on.  Oh well, I'll give that a try.  Thanks.

---

### Post by njpatel on 2008-10-18
No problem :-). I think that Ubuntu enables them if it thinks your graphics card can handle it on the initial log-in, as most people wouldn't find it otherwise.

---

