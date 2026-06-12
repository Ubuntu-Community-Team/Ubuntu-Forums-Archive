---
title: "installed as server, need to install X, fluxbox"
date: 2005-12-17
forum: Installation &amp; Upgrades
---

### Post by talz13 on 2005-12-17
I installed ubuntu as a server last night in order to get a nice and clean install without extraneous gui apps and whatnot (for my headless server).  I also plan on using vnc to remotely administer the box mainly (as I will be using a couple gui apps), but I need to add an X server, vnc, and fluxbox.

I didn't think about the X server part, and went ahead and apt-get install'ed fluxbox.  When I tried to start it, I got the error: Can not connect to X server, because, obviously, I don't have an X server running.

How do I install an X server, and get it to boot fluxbox?

---

### Post by dcast on 2005-12-17
i dont know about installing x but to boot fluxbox you need to edit .xinitrc to say "exec fluxbox"

so 

gedit ./xinitrc 

exec fluxbox

then save it

---

### Post by talz13 on 2005-12-17
thanks for that reply, it'll get me started after X gets installed

---

### Post by talz13 on 2005-12-17
so nobody knows what the X package is called or how to install it?

---

### Post by afhp on 2005-12-17
```
sudo apt-get install xserver-xorg
```

---

### Post by talz13 on 2005-12-18
Ok, in the process of getting X set up, but it's not running just yet.  I installed xserver-xorg, and x-window-system-core, but am still getting the "user not authorized to run the X server, aborting" errors.  I have checked the ownership of my .Xauthority file, and added rw permissions (which got rid of the "error in locking authority file" error, apparently), but am still getting "Couldn't get a file descriptor referring to the console" error.

I've looked around, and the main thing I found was checking that the Xwrapper.config is set for allowed_users=console already

What should I check next?


(when I start a vncserver and connect to it, it tells me about not having a .xsession file, no .Xsession file, no session managers, no window m... terminal emluators found; aborting)

---

### Post by hagen00 on 2006-03-30
It sounds like you wanted to exactly what i needed to do...

Check this out. [http://ubuntuforums.org/showthread.php?t=151703]("http://ubuntuforums.org/showthread.php?t=151703") Instead of using twm you can then just use fluxbox i would think..

---

