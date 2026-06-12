---
title: "Don't think this exists, but...advanced power management"
date: 2008-09-11
forum: General Help
---

### Post by JustGus on 2008-09-11
I've been knocking my head against a wall to try and get WOL to work once my machine's gone into hibernation and noticed that one thing that seems missing is a really fully featured power management app.  The one I've currently got allows for a very ltd number of variables to be changed, and nothing that allows you to select "shutdown" (rather than sleep) after the machine's been idle for a set period.  I've had a trawl through the various power management offerings and can't seem to find any "do-it-all" Swiss Army knife type power mgmt app.  Does anyone know of one?

---

### Post by Shazaam on 2008-09-11
I found this....
[http://www.tuxonice.net/](http://www.tuxonice.net/)
Google cache (real address pops up a certificate warning) of a page where they delve into the guts of power management. It may not apply to you but it might give you hints on configuring apm....
[http://64.233.169.104/search?q=cache:r-LpUBxjl3QJ:https://wiki.inf.ed.ac.uk/DICE/MPUPowerDiary+linux+%22power+management+gui%22&hl=en&ct=clnk&cd=10&gl=us](http://64.233.169.104/search?q=cache:r-LpUBxjl3QJ:https://wiki.inf.ed.ac.uk/DICE/MPUPowerDiary+linux+%22power+management+gui%22&hl=en&ct=clnk&cd=10&gl=us)
Also look in ~/gconf/apps/gnome-power-manager.

---

### Post by JustGus on 2008-09-14
Thanks for the tip.  Came across that and was going to try it out, but thought if I could find a "one stop power management shop" that would be a better option I'd give that a go (seems tuxonice focuses on hibernate).  In the absence of that, I will give tuxonice a go (can't over the next couple days).  Fingers crossed and thanks again.

---

### Post by p_quarles on 2008-09-14
If you don't mind getting into the OS's guts and learning how power management is done at the most basic level, I'd suggest vor's tutorial:
[http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)

Much of this stuff is from
[http://lesswatts.org](http://lesswatts.org)

Basically, it's pretty easy to configure a script (that can optionally be auto-run on ac/battery events) to save a pretty dramatic amount of power.

---

