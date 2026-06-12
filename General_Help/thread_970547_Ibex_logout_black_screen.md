---
title: "Ibex logout black screen"
date: 2008-11-04
forum: General Help
---

### Post by jimdb on 2008-11-04
I did a distribution upgrade from Hardy to Intrepid a few days ago. The hardware is an Acer Aspire 5000 (no fancy graphics hardware).

When I logout, I get a black screen followed by the logout sound. I can log in again (blind) but the screen stays black and I can't get it to come back on. This only affects the Logout function. Suspend, hibernate, restart and shutdown appear to work as advertised, so for now, I restart or hibernate instead of logging out.

Has anyone else seen this problem?

Thanks.

Jim

---

### Post by jimdb on 2008-12-08
I found a few similar bugs, but they referred to the nVidia driver, which my laptop doesn't use. I have a SiS graphics chip. I also found a few black screen problems at x.org, but none seemed to apply to my problem.

I looked through a bunch of log files and didn't find any errors. In fact, it appears that X restarts, but the screen stays black anyway.

Any additional clues about where to look to solve this problem would be greatly appreciated.

Thanks.

Jim

---

### Post by RHTopics on 2008-12-08
Jim,

I get the same happening to me periodically with Hardy on a Gateway laptop that has an ATI graphics chip.

One way I found to bring the login screen back is to do a Ctrl-Alt-F2 key combination which will take you to a text login console.  And then do a Ctrl-Alt-F7 key combination to take you back to the GUI login screen.

That might work for you as well until a better fix is determined.

---

### Post by jimdb on 2008-12-09
This method works fine for now. X is so complicated that it might be a while before anyone finds out what is really going on here. I will keep looking but my last X debugging was X11R4 on Suns so I'm feeling a little obsolete.

Thanks.

Jim

---

