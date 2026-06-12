---
title: "Acer TravelMate 2319NLCi -- Video Problems"
date: 2008-05-06
forum: Hardware
---

### Post by eric_son on 2008-05-06
Hi,

My friend's laptop crashed.  I managed to get my friend to agree to let me install Ubuntu on the laptop.  My friend agrees to keep the Linux installation and dump XP if things turn out well.

I eagerly bring home the laptop and start installing Hardy.

As expected, the modem didn't work.  But I managed to get the drivers from Linuxant.com. :)

Now, everything works...almost.

The video display intermittently goes bonkers.  Sometimes, when I boot up, the displays just weird vertical lines.  The closest description I can give is that it looks like what would happen to a CRT monitor when you set a video resolution or Vert/Horiz rate that the monitor does not support.

Even if I use the xfix utility from the recovery mode, it still doesn't work.  I'd have to keep rebooting and hope the correct display pops up.

Has anybody encountered something like this before?  What other stuff can I do or try to fix this?

The video hardware for the notebook is a SiS661.

Help!  Here's my chance to win over another Windows user.

---

### Post by eric_son on 2008-05-06
Update:

IF I boot up and the screen display is broken, I can get it back to normal by hitting CTRL-ALT-F1 to get to the text prompt.

Then I stop Gnome (gdm -stop).
...and of course I restart Gnome (gtm -start).

After that, I get the normal display back.

Even weirder is --- restarting Gnome via gdm -restart doesn't work.  It has to be gdm -stop followed by gdm -start.

---

