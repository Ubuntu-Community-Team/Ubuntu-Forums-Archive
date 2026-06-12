---
title: "xinitrc ignored when using GDM"
date: 2005-12-05
forum: General Help
---

### Post by bananana on 2005-12-05
I just realized my previous two posts were in the wrong forum. Sorry. This one is more appropriate. I've installed ubuntu on this old laptop that has broken mouse buttons, so I've mapped the mouse buttons onto the "windows" and "menu" keys. It all works fine, except I can't get it to load automatically when I log in. I have to open I terminal and run my .xinitrc manually. I'm giving this 'puter to a friend, so this isn't acceptable. 

I've tried a few things, none of which has worked:
1) run the script from the /etc/X11/xinit/xinitrc file
2) put the script into /etc/X11/Xsession.d/
3) run the script from /etc/gdm/PostLogin/Default
4) run the script from /etc/gdm/Init/Default

As far as I can tell, 1 and 2 should definitely have worked, and 3 probably should have worked. But I can't tell for sure, because I don't know how to trace the execution. /var/log/gdm/\:0.log and /var/log/Xorg.0.log had no useful information.

---

### Post by bananana on 2005-12-05
I just tried putting it into /etc/gdm/PostSession/Default too with no luck.

---

### Post by schdefan on 2005-12-05
if you want to use the xinitrc for autostart purpose don't select gnome as session. You have to choose the terminal default session. I can't exactly remember the name in the session menu.
Look also [here]("http://www.gnome.org/projects/gdm/docs/2.8/configuration.html") the gdm documentation.


schdefan

---

### Post by bananana on 2005-12-07
Thanks for your reply. I tried using the failsafe terminal session, and found that it did run my .xinitrc. So that's a great first step, but I still need gnome. I noticed two interesting things:

1) when exiting from the failsafe terminal session, gdm retains my mousekey settings! This is interesting not only because I eventually want to get the mousekeys setup for gdm too, but also because this does not happen when exiting out of gnome.

2) if I add gnome-session to my .xinitrc, it doesn't run. I still get the failsafe-terminal session. this is unacceptable, because like I said, this computer is for a friend, and its his first linux experience. the broken mouse buttons are already pushing his envelope.

---

### Post by artships on 2005-12-07
I vaguely recall that my window manager, fvwm2, reads ~/.xinitrc but gnome reads ~/.xsession, so if you have one but not the other, symlink the other to the one.  In my case,  ln -s .xinitrc .xsession

Or does this have anyting to do with your question?

---

### Post by schdefan on 2005-12-08
login into a normal gnome session.
In Gnome Control Center->Session->Startup Programs you can add programs or scripts to run when Gnome starts, like your mousekey settings for
instance. Setting the priority will assign when the start up
sequence is loaded.


schdefan

---

