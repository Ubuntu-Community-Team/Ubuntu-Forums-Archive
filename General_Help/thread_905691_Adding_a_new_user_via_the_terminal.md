---
title: "Adding a new user via the terminal"
date: 2008-08-30
forum: General Help
---

### Post by The TJ on 2008-08-30
I'm sure there is a way.  I installed Ubuntu (via Wubi) on my second computer, and while transferring settings (profiles and the like) from my primary PC (which also has Ubuntu), I accidentally made one too many alterations to my secondary PC via the Gnome Appearance.  The only thing that shows up on my desktop is the background (nothing else).  My question is how do you add a new user via the terminal (I plan on creating a new user and then using the new one to delete the old user)?  I figure that this is much easier than reinstalling the entire system via Wubi.

Thank you for your time.
-TJ

---

### Post by Ryadt on 2008-08-30
```
adduser newuser
```
replace newuser by a username of your choice.```
passwd newuser
``` to assign a password to the user.

---

### Post by Nepherte on 2008-08-30
```
sudo useradd <username>
```

For more specific information, see the manual page:
```
man useradd
```

---

### Post by bodhi.zazen on 2008-08-30
sudo adduser <username> <group>

sudo usermod -G <group> -a <user>

Those commands are so that you may add your new user to additional groups, you may wish to start with the admin group (for sudo access).

---

