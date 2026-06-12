---
title: "System &quot;reinstall&quot;"
date: 2008-07-12
forum: General Help
---

### Post by Brijamelsh on 2008-07-12
Hello, i have recently started to use ubuntu. In my hours of downloading cool little programs and tweaking i have managed to mess up little things here and there and now linux isnt running its best.

I was wondering if there was a way to restore linux back to "like new" while keeping my appearance setings.

---

### Post by jonlemur on 2008-07-12
Are there specific things you have done that you think have messed up the system, like editing /etc/X11/xorg.conf, or just playing around with Compiz settings?

---

### Post by ChameleonDave on 2008-07-12
> **Brijamelsh said:**
> Hello, i have recently started to use ubuntu. In my hours of downloading cool little programs and tweaking i have managed to mess up little things here and there and now linux isnt running its best.

I was wondering if there was a way to restore linux back to "like new" while keeping my appearance setings.
The contents of /home/ are what govern your personsalisations.  Just back that up, and you should be OK.  When you reinstall, make sure that you also reinstall any software that you installed before.  Then it should be the all the same.

---

### Post by Brijamelsh on 2008-07-12
> **ChameleonDave said:**
> The contents of /home/ are what govern your personsalisations.  Just back that up, and you should be OK.  When you reinstall, make sure that you also reinstall any software that you installed before.  Then it should be the all the same.

thanks, sounds easy enough. I actually have a /home partition (advice i found online), what are the procedures for reinstalling with this.

---

### Post by ChameleonDave on 2008-07-12
> **Brijamelsh said:**
> thanks, sounds easy enough. I actually have a /home partition (advice i found online), what are the procedures for reinstalling with this.
It's actually a little tricky.

This is one way.

Rename the directories inside /home/ so that they will not interfere with the new installation (e.g. change "brijamelsh" to  "brijamelsh-old").

Reinstall Ubuntu, reformatting the root partition, but making absolutely sure that the /home partition is **not** formatted (I slipped up with that once!) and is again mounted at the mountpoint /home.  Set up the same username as before.  It needs to also have the same user number.  It is automatically have the same number if it was the first user set up on the system each time.

Once the new system is up and running, use Synaptic to install whatever software you had before.  

Then you can transfer your old files back.  It's best to do this from the command line.  Copy everything from /home/brijamelsh-old to /home/brijamelsh.  Then log into the desktop environment.  Everything should work.  If it doesn't, then go back to the command line and clear all that stuff out again.  You could then try copying things piecemeal, to see what works.

It's not really that difficult, but there are a few things that could go wrong, and you just need to be savvy enough to resolve them.

Argh, maybe there's a guide out there that explains it better.

---

