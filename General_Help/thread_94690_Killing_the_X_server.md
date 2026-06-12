---
title: "Killing the X server"
date: 2005-11-24
forum: General Help
---

### Post by Aber_Adrian on 2005-11-24
I tried ctrl-alt-F1, logged on as root, typed *init 3*, and nothing happened (except that it told me it was entering runlevel 3). The X server was still running when I went back to ctrl-alt-F7. The command "runlevel" reports 2 3 which of course should be right, but obviously isn't.

ctrl-alt-backspace just restarts the X server, so that's no good either.

Adrian

---

### Post by kairu0 on 2005-11-24
Ctrl-Alt-Bksp doesn't work because GDM will always regenerate X.

You should log-out (to the GDM screen), switch to a console, and "sudo killall gdm"

---

### Post by sapo on 2005-11-24
simply type:


sudo /etc/init.d/gmd stop

---

### Post by Randy Sparks on 2005-11-24
Under Ubunu run levels 2-5 are all identical and all run GDM (which kicks off the GUI). So switching to run level three won't do anything at all.

---

### Post by Aber_Adrian on 2005-11-24
[QUOTE=Randy Sparks]Under Ubunu run levels 2-5 are all identical and all run GDM (which kicks off the GUI). So switching to run level three won't do anything at all.[/QUOTE]

OK thanks - that explains it.

Adrian

---

### Post by Aber_Adrian on 2005-11-24
[QUOTE=sapo]simply type:


sudo /etc/init.d/gmd stop[/QUOTE]

Thanks. Assume that was a typo for sudo /etc/init.d/gdm stop

Adrian

---

### Post by nonewmsgs on 2007-09-13
is it a typo? which one is the correct one?

also shouldn't this be stickied since it will prevent unnecessary hard rebooting?

---

### Post by bodhi.zazen on 2007-09-14
LOL , this is an old thread indeed ....

The correct command is :```
sudo /etc/init.d/gdm stop
```

use sudo /etc/init.d/gdm start

to restart.

---

