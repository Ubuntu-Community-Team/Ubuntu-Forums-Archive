---
title: "Help! Latest 8.04 kernel updates broke X"
date: 2008-12-01
forum: General Help
---

### Post by Phases on 2008-12-01
Ok. So updates were released the other day, a bunch, for the kernel headers or whatever. I ran the updates at home and things did okay. Had to reinstall VirtualBox, that's about it. 

Came into work, and we had the same updates. My coworker ran his first and rebooted - it broke X. So, I nervously ran mine and rebooted too, figuring we can both panic together - and it also broke. We have the same machines.. setup SLIGHTLY different, but mostly the same. Our X breaks in the same fashion. 

Here's what happens. We get to the log in screen and try to log in. It begins to load, but flashes and then goes all white. A couple seconds later it goes all back and the computer is frozen, requiring a hard restart. 

We tried the reconfiguring xorg thinking that would fix it and we would just have to redo our dual monitors, but that didn't help. Same thing happens except now it's obviously cloned on the two screens instead of spanned. 

It seems like X is starting to load and once it tries something it just kicks us out and freezes. But I went through ~/.config/autostart items and disabled them one or two at a time with no luck.

If I try to logon in "failsafe" it bumps me back to the login screen, but doesn't freeze the computer.

Dell GX740
ATI 2400XT
Y splitter on DVI, BIG DESKTOP 

Any ideas where to start? 
Any help appreciated. 

Thanks..

Edit: UPDATE - changing window manager to metacity lets me in.  However putting compiz back as the manager white screens/freezes. Reinstalled everything compiz related but didn't help.

Edit 2: Ok, reinstalled my ATI driver through EnvyNG and all is well. 

**Resolved.**

---

