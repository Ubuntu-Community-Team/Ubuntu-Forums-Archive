---
title: "Ibex Upgrade -&gt; Compiz dual monitor broken"
date: 2008-10-31
forum: General Help
---

### Post by minime283 on 2008-10-31
Hey guys,
I just upgraded to Ibex and it kind of broke my compiz (I say compiz because the problem seems to only effect 1 monitor and even then it seems to work even though a chunk is missing) I have two monitors: a main monitor 17" 4:3 and a 20" Widescreen. The Widescreen monitor is (after the upgrade) missing a large chunk of screen on the right side (but I can still move my mouse over it as well as the (task bar? program bar?) at the bottom. 

I've attached screenshots. 7600 GT. 

Also the following script happens on bootup, but I tried it with or without and it makes no difference. It fixed a bug in Hardy with slow menus:

#!/bin/bash
DISPLAY=:0.0 compiz --only-current-screen &
DISPLAY=:0.1 compiz --only-current-screen &

---

### Post by loomsen on 2008-10-31
Well, actually that's the way it should be. You may configure your TV completely independent from your LCD.

Just posted sth 2 threads below this one...

Add your xorg anyway tho.

---

### Post by minime283 on 2008-10-31
Hi!
Sorry, my widescreen isn't a TV, it's a monitor connected via DVI. I've attached my xorg, but I don't think it's an issue with that because the issue doesn't happen when compiz is disabled. Also I uninstalled compiz and took out all the settings and reinstalled, and that didn't fix the issue either.

---

### Post by loomsen on 2008-10-31
Just give it a try, and read this Post:

[url=http://ubuntuforums.org/showthread.php?p=6070424#post6070424]I explain the different setups an what is possible with each. Actually, the X-Layout explains it...
[/url]

Edited your xorg. Read through it, I made some comments here n there.

For instance, you should specify your exact widescreen resolution. Don't let nvidia-auto do this for you.

---

### Post by minime283 on 2008-10-31
Alright thanks, I'll give it a try tonight.:) I'm just  a little hesitant to mess around with the xorg cause last time I broke it and I tried for weeks to fix it and eventually just had to reinstall Linux...:(

---

### Post by minime283 on 2008-11-02
Thanks for your help man, but I found out the problem.
I went into my CompizConfig Setting Manager and in the Display Settings tab unchecked "Detect Outputs" And manually set my Screen1 Output to 1680x1050.

---

