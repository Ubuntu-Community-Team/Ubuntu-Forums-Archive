---
title: "DCOP - wtf?"
date: 2005-12-01
forum: General Help
---

### Post by chimera on 2005-12-01
OK, I'm currently using the fluxbox desktop, but I have kubuntu and ubuntu desktops installed. When I try to open konqueror, I get this error:

There was an error setting up inter-procces communications for KDE. The message returned by the system was:

Could not read network connection list.
/home/chimera/.DCOPserver_ubuntu__0

Please check that the "dcopserver" program is running.

(dcopserver is running according to gnome system monitor)

So I click OK, it lets me in konqueror, but when I click home, it says:

Protocol not supported

File

and that's it.


HELP

---

### Post by adrianhensler on 2005-12-01
I may be offbase here; but I seem to recall having a problem like this where I had to:
chown -R myusername:myusername /home/myusername/*

I can't remember if that was the same scenario or not. Root had ended up owning a bunch of ./kde files; so the user was not getting correct access.

---

### Post by chimera on 2005-12-01
Still the same problem as before

---

### Post by claydoh on 2005-12-01
try deleting/renaming .DCOPserver_ubuntu__0 (its a hidden file), then try logging back in to kde.

---

### Post by chimera on 2005-12-02
still won't let me use konqueror,and won't let me login to kde...

---

### Post by adrianhensler on 2005-12-02
Sorry, my command as given wouldn't have hit the hidden ( . ) files. Try:

sudo chown -R myusername:myusername /home/myusername/.*

Hope this works for you. 
(edit - forgot the '-R' ...)

---

