---
title: "Screensaver password rejected"
date: 2008-10-05
forum: General Help
---

### Post by squee on 2008-10-05
Hi,

I was trying to get an ext3 partition to auto mount (i failed). I have my screensaver set to start as soon as the desktop loads. It now wont recognise my password. It still works on the login screen (which is skipped by default, i access it via switch-user).

I have to use Vista now :-(
I could probably try to get a commandline but i dont know what to do from there.

Ideas?

Thanks!

edit: Live CD?

---

### Post by tonybaqain on 2008-10-05
when your login window appear press **CTRL+ALT+F1** it will bring you back to a black command line screen asking for username, login through your username and remove the screensaver from running once the desktop loads, once you finish just **/etc/init.d/gdm restart**, and you'll be taken to your desktop without having screensaver to run.


have fun :)

---

### Post by squee on 2008-10-05
Great Thanks, but how do i stop the screen saver from loading from the commandline? Or will can I just do it from the GUI?

Ok didnt work. Even after logging in via CLI it took me back to the screensaver which still doesnt recognise my password. Im using the Live CD now, to back up some stuff just in case I have to do a fresh install. I have been tempted to go to Ibex. I know its early days yet so im relucant.

Any more advice?

---

