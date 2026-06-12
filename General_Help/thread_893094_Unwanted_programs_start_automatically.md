---
title: "Unwanted programs start automatically"
date: 2008-08-17
forum: General Help
---

### Post by zephyrus17 on 2008-08-17
I'm running Openbox/Gnome, and whenever I log in from a reboot, a fresh startup, or a logout/login, firefox, and gedit will start up by themselves. I've checked System > Preferences > Sessions, and they're not there. what's going on?

---

### Post by quibbler on 2008-08-18
> **zephyrus17 said:**
> I'm running Openbox/Gnome, and whenever I log in from a reboot, a fresh startup, or a logout/login, firefox, and gedit will start up by themselves. I've checked System > Preferences > Sessions, and they're not there. what's going on?
Go to: System - Preferences - Sessions - Session Options

and unticked automatic remember

then logout and see if that works.

Regards quibbler

---

### Post by zephyrus17 on 2008-08-18
Gedit doesn't open anymore, but firefox still does.

---

### Post by MatthewPlanchard on 2008-08-20
You could try this:

```
gedit ~/.gnome2/session 
```

Look for anything in there that mentions firefox and delete the line.

Make sure to renumber the num_clients line to the correct number.

---

### Post by Cheesehead on 2008-08-20
If you have the option to 'save session' on logout, you may have saved your session with them open once long ago.

Simply shut down all your apps, and then save session (logout) to eliminate them.

---

### Post by zephyrus17 on 2008-09-03
> **MatthewPlanchard said:**
> You could try this:

```
gedit ~/.gnome2/session 
```

Look for anything in there that mentions firefox and delete the line.

Make sure to renumber the num_clients line to the correct number.
Ooo! This worked! Thanks!

---

