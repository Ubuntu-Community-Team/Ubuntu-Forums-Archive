---
title: "[SOLVED] cairo-dock High CPU usage"
date: 2008-11-14
forum: General Help
---

### Post by itzame on 2008-11-14
I'm trying to remove the top panel...am using CD and have it set up the way I like, but when I use gconf-editor to "hide" the panel, my CPU goes berserk I change these settings, CPU starts running at 70 to 80% at idle??? Normally idles at 3 4%

What am I doing wrong here? These are what I changed:

auto hide yes
auto hide size to 1
hide delay to 10,000
monitor from 0 to 3
unhide delay to 10,000

X: 10,000
Y: 10,000
what am I missing? Oh BTW running Intrepid, when I run top gnome-panel and gnome-sensors are eatin' my lunch.

---

### Post by loomsen on 2008-11-14
Had a similar issue with kiba-dock. Everything worked fine, gnome-panel replaced by kiba-dock in gconf. But when I logged out and back in I had two instances of kiba running, one of them struggling hard. So I made a script to kill all kiba when I log out.

Now, you're aware that if you hide gnome-panel it will still be there? Have you unchecked lock to panel for each applet prior to removing it from gnome-panel?
There are some possible issues... The notification area, for instance, can only be drawn and handled by one app. Maybe you have a launcher/applet left in your panel and didn't notice? Like, window switcher or sth.

Anyway, if you kicked it from the required-components key in gconf, you can kill it completely. Hiding wouldn't be sth I'd take into consideration, but, if you really wanna keep it like that, kill gnome-panel for troubleshooting at least.

If it gets better, there's the bug.

---

### Post by itzame on 2008-11-14
Thanks for the quick reply loomsen...FWIW I've read your posts, among others, was afraid I would hose somethin' else up, ok killall gnome-panel, guess what? back to 1 2%. So logged out back in and started tweakin my changes in gconf, whenever I changed monitor from the default 0 to 3 thats when it would go thru the roof, left it at 0...I'm golden, BTW when it was at monitor 3 I would lose alt F2, would just stop working, not sure what that monitor setting does but leave it the heck alone! TNX again!

---

### Post by loomsen on 2008-11-14
Alright, you're welcome, please mark thread as solved.

Alt+F2 "issue" here too, tho I didn't use it while it worked neither. Super+Space not only is handier imho, and gnome-do has become one of my required components, for sure! Give it a try, I'm lovin it.

*edit*
Btw, if you're on amd64 too, try and grad 1.6.3.1 from my sig. Quite some nice development has taken place since 1.6.2.3

---

