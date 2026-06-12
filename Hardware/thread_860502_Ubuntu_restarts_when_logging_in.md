---
title: "Ubuntu restarts when logging in"
date: 2008-07-15
forum: Hardware
---

### Post by Bishop Hill on 2008-07-15
I'm currently running ubuntu on a HP laptop, and everything was working like a charm until a couple of weeks ago.

The problem is that, when logging in, the screen gives a white background and then restarts X, which brings me back to the loginscreen.

I'm suspecting that a process is not doing it's thang, but what should I do?

---

### Post by mr_manny on 2008-07-15
this is essentially what happened to me when I was playing w/my daughter's laptop last week.
She wanted me to load a bunch of themes, and I inadvertently installed an xorg-server-xvf or something similar (can review the history, currently at wrk).

logged out, logged in as a test....and created your problem.
I think I remember an error message before it kicked me out on my login attempts.

Could you post your xorg packages?

hth,
manny

---

### Post by markbuntu on 2008-07-15
Can you login in gnome safe mode?
There is a little icon in the bottom left corner of the login screen.

---

### Post by Bishop Hill on 2008-07-16
Mr manny

Where do I get the info about those?

markubuntu

Yes, actually I can. I cant use a gnome-session, but I can login using failsafe gnome.

---

### Post by markbuntu on 2008-07-16
Ok. look in your logs for some "authentication failure" or gdm message about login failure either in 

messages 

or

syslog 

or 

auth.log. 

You can find these in System/Adminstration/System Log. If any particular one is not shown you can get it from there with File/Open.

You can also try setting up timed login in System/Administration/login Window. I do not really reccomend automatic login because if you are having problems with your session, there is no way short of recovery mode to get away from it.

---

### Post by Bishop Hill on 2008-07-19
markbuntu

The logs showed an authentication failure, I changed the password and everything went back to normal!

Thanks!

---

