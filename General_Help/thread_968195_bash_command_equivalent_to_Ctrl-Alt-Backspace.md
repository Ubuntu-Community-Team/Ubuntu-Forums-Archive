---
title: "bash command equivalent to Ctrl-Alt-Backspace"
date: 2008-11-02
forum: General Help
---

### Post by Birdy1982 on 2008-11-02
In reply to the read-only thread:
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=574243[/COLOR]]("http://ubuntuforums.org/showthread.php?t=574243") started by RyanGT on October 12th, 2007.

There is a way to restart the x server, RyanGT and eurgain were so close:
>  Re: bash command equivalent to Ctrl-Alt-Backspace
The sudo kill `cat /tmp/.X0-lock` command kills X, but does not restart it. I tried adding startx to my script, but it doesn't work. So, right now the script stops X, but I need to manually restart it.

This is my current script:

#!/bin/bash
sudo cp /etc/X11/xorg.conf.projector /etc/X11/xorg.conf
cp ~/.ipython/ipythonrc.class ~/.ipython/ipythonrc
sudo kill `cat /tmp/.X0-lock`
startx

I would like it to make my changes and automatically stop and restart x in one clean shot. Can this work?

Thanks,

Ryan

When this script is executed using the **nohup** command, the script is not stopped after the kill of the x server.

Best regards,
Birdy

---

### Post by cmnorton on 2008-11-05
Some interesting comments:

[http://www.linuxforums.org/forum/suse-linux-help/11882-stopping-x-server.html](http://www.linuxforums.org/forum/suse-linux-help/11882-stopping-x-server.html)

---

### Post by Slim Odds on 2008-11-05
The proper way to restart the server is to restart the server.

For GNOME:```
sudo /etc/init.d/gdm restart
```For KDE:```
/etc/init.d/kdm restart
```Also, maybe:```
/etc/init.d/xdm restart
```It all depends on which X Display Manager you're using.

Also note that this should NOT be done from an xterm within X.

---

### Post by geirha on 2008-11-07
```
gnome-session-save --silent --kill
``` is the equivalent of clicking log out in gnome.

---

### Post by Slim Odds on 2008-11-08
> **geirha said:**
> ```
gnome-session-save --silent --kill
``` is the equivalent of clicking log out in gnome.

He was asking about restarting the X server.

---

### Post by geirha on 2008-11-08
> **Slim Odds said:**
> He was asking about restarting the X server.

Ah, I see now that the fact that X restarts when I logout is a [bug](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/149330), not a feature as I had assumed. Perhaps it's fixed in Intrepid ...

---

