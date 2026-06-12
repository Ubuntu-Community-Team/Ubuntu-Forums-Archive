---
title: "Giving focus to new windows placed on other workspaces"
date: 2008-08-06
forum: General Help
---

### Post by conundrumx on 2008-08-06
Okay, so that's a long title.  Basically, what I'm trying to do is this: when I spawn a new window (let's say Firefox) I would like it to spawn on a fixed desktop (which is already possible) **and** switch to that desktop without my interaction.

If I'm spawning a new window I most likely want to interact with it, but I would also like to have designated desktops for each application without having to force myself to do it by hand.  I've tried Devilspie and CCSM's Window Placement plugin, and gotten as far as having a window where I want with focus, but out of sight (Firefox on desktop 1 with focus, I'm still staring at desktop 3 where I launched it from).

Any input would be appreciated, I'm not afraid of diving into config files and making some simple scripts but that's where my abilities end.

---

### Post by conundrumx on 2008-08-08
Shamless bump, still trying to figure this out.

---

### Post by conundrumx on 2008-08-09
One last try, guess this is harder to do than I thought it would be.

No one?  :confused:

---

### Post by Pablo Pablovski on 2008-08-11
No help. sorry, but FWIW I'd be interested to know whether this is possible, and, if so , how. 

I've set Compiz to got place windows in defined viewports, but they don't automatically focus - seems it's not a Compiz option. 

Maybe someone can shed a bit of light? There's £5 in it.... :)

---

### Post by conundrumx on 2008-08-11
Well I'm glad at least one other person wants to do this.

There has to be some function in Compiz, or something generic we can call.  It would be silly if there isn't.

---

### Post by conundrumx on 2008-08-12
It looks like this could be accomplished with CCSM, Devilspie and libwnck.  

CCSM for placement (devilspie doesn't quite get it right) with devilspie executing a corresponding perl script (using libgnome2-wnck-perl) on the spawning of a window to properly focus it.

That seems like a crazy amount of effort for what should be a simple task.

P.S.  The environment in question is GNOME with Compiz and Emerald.  Maybe it can be more easily done with another DE.

EDIT:  Looks like devilspie uses libwnck, guess I'll be filing a bug report.

---

