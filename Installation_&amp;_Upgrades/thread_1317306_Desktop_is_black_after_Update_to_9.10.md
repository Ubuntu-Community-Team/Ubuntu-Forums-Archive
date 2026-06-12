---
title: "Desktop is black after Update to 9.10"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by gmw on 2009-11-06
Good evening. I have just updated to Ubuntu 9.10. For a moment it all looked pretty good. Started up, programs are running fine, but - why is my background picture gone? I tried to set a new wallpaper - nothing, the background remains black. Even if I am only using one color for the desktop, nothing changes.  
 

 Also, the icons and programs that I had on the desktop do no longer appear. The files in ~ / desktop are definitely there and can be opened if I am in this folder. Just the desktop remains dark. The panels are working fine, both the top and bottom one work as it should be.  
 

 I already deleted .gconf * and .gnome2 * which has not helped. I start Ubuntu in safe mode and the wallpaper and desktop icons are there. Even if I add a new user everything is all right. So this must be a problem with my user. But where? Help urgently required...

---

### Post by coffeecat on 2009-11-06
You've got an ATI card and you've enabled compiz. Am I right? :wink: This has come up before. I believe it only affects some ATI cards, but you'll have to disable compiz or live with a black desktop.

Or buy a nvidia card. :)

---

### Post by gmw on 2009-11-06
Hmmmpf. Haven't found a thread about that here. But you are absolutely right. Not the best news. Will try to disable compiz tomorrow. Thank you for the reply.

---

### Post by coffeecat on 2009-11-06
> **gmw said:**
> Haven't found a thread about that here.

You're right - they're not easy to find. I learnt about this issue from [this thread](http://ubuntuforums.org/showthread.php?t=1302069).

---

### Post by gmw on 2009-11-07
Disabling all desktop effects finally helped, my desktop is back. Thank you coffeecat for the tip.

I just do not understand why a new created user works without disabling this effects? Can't remind to have changed anything here.

---

### Post by kmunro on 2009-11-08
Has anyone come up with a solution to this problem rather than just living without Compiz? It worked perfectly on my machine under 9.04.

---

### Post by coffeecat on 2009-11-08
**gmw**, I know you've marked this thread as solved, and I hope you've subscribed to a notification on this thread so that you see this because I saw a better fix in another thread. Have a look here at Tholley's post #9:

[http://ubuntuforums.org/showthread.php?t=1316902](http://ubuntuforums.org/showthread.php?t=1316902)

I don't understand how a new user would not be affected - that's odd - because the posted fix in that thread involves a system-wide change that would affect all users.

Interesting.

---

