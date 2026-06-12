---
title: "this is gonna sound real dumb but ...."
date: 2005-01-27
forum: Installation &amp; Upgrades
---

### Post by nastic on 2005-01-27
so i installed a lovely fresh copy on a lovely fresh hdd. i get distracted during install and just enter the first thing that comes into my mind as username and password during install.(both users) so now when i get to login screen i cannot even remember the username.(stupid stupid stupid!) i have already tried to set the root password using the boot kernel and bash command. i try to logon with that password but cannot remember the arbitrary username i chose.(again...stupid stupid stupid!) is there any way i can access without reinstalling? please help cos i am truly stuck.

ta!

---

### Post by jakeslife on 2005-01-27
Yes, that is a dumb thing to do. Not that I've never done that as well.....

If you seriously want help with the issue, post the thread with a better title.

---

### Post by jdodson on 2005-01-27
[QUOTE=nastic]so i installed a lovely fresh copy on a lovely fresh hdd. i get distracted during install and just enter the first thing that comes into my mind as username and password during install.(both users) so now when i get to login screen i cannot even remember the username.(stupid stupid stupid!) i have already tried to set the root password using the boot kernel and bash command. i try to logon with that password but cannot remember the arbitrary username i chose.(again...stupid stupid stupid!) is there any way i can access without reinstalling? please help cos i am truly stuck.

ta![/QUOTE]


if you forgot the root password you can't really do much that is non-trivial to get it working without reinstalling.  my suggestion is reinstall but this time write down the username/pass.  its a short 30 min install anyway.

there is always single user mode, but that requires a root password.  you coudl use a livecd to get info off the machine if you had any, though doesnt sound like you did.

---

### Post by nastic on 2005-01-31
well thanks anyway....
donde` est el installation cd?

---

### Post by Buffalo Soldier on 2005-01-31
[http://ubuntuguide.org/#rescuemode](http://ubuntuguide.org/#rescuemode)

It has:
- How to gain root user access without login?
- How to modify kernel boot-up arguments, to gain root user access?
- How to use Ubuntu Installation CD, to gain root user access?
- How to change root user/main user password if forgotten?

---

### Post by az on 2005-01-31
You do not need to reinstall, just follow the instructions above.  (init=/bin/bash)

Use a live cd to look in /home.  Your user has a directory there by his name.  Maybe that will jog your memory.

You can then do 

passwd (nameofyouruserhtatyouforgot)

CTRL-ATL-DEL to reboot.

---

