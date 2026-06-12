---
title: "[SOLVED] disabling compiz by default?"
date: 2008-11-02
forum: General Help
---

### Post by echostorm on 2008-11-02
I am running Intrepid with an Nvidia 7900 GTO. (single core socket 939 AMD 4400+ in a biostar mobo, 1024mb RAM)  I am having alot of problems with fullscreen flash, odd menubar problems, excessive cpu in fullscreen video, etc. 
I installed compiz fusion icon and switched to metacity... my problems seem to be (mostly) resolved. CPU usage has dropped considerably and framerates have gone up so that flash seems generally watchable.

Is there a command to make this change happen by default on startup? I will go back to compiz in another release or two, but functionality is much more important to me right now.

---

### Post by loomsen on 2008-11-02
So what do you want to disable now?
Compiz from starting up?

Well, if so, most likely you specified how it shall start up, didn't u? Do the opposite of that.

Either Preferences->sessions and remove fusion-icon or whichever cmd you have there(if you have one)

Or go to the folder ~/.config/autostart and remove it from there, if there's such a starter.

But actually you should know this don't you think ^^

---

### Post by echostorm on 2008-11-02
actually, you are right - I was being retarded. For some reason I never paid attention to the fact that it doesn't auto-start UNLESS you have effects enabled. 
HUR

problem obviously solved.

---

