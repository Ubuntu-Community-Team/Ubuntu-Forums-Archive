---
title: "Fluxbox no menu?"
date: 2006-01-01
forum: Hardware &amp; Laptops
---

### Post by DoorGunner on 2006-01-01
Hi 

I have a bit of a problem with fluxbox setup. Installed it with apt-get and have the following files.
fbdesk, fbpager, fbconf, fluxbox

However, my menu only says i have the following items. 

Xterm
Restart
Exit

---

### Post by r4ik on 2006-01-01
Perhaps this helps.

[http://www.ubuntuforums.org/showthread.php?t=53181&highlight=Fluxbox](http://www.ubuntuforums.org/showthread.php?t=53181&highlight=Fluxbox)

Good luck.

---

### Post by r4ik on 2006-01-01
Here is a wiki i found.

[https://wiki.ubuntu.com/Fluxbox](https://wiki.ubuntu.com/Fluxbox)

Gonna give it a try myself. :)

---

### Post by DoorGunner on 2006-01-01
I tryed both with no joy.....accept that now i can see all my apps etc in the ~/.fluxbox/menu.....it looks very well layed out. I settled on the second file you sent.....

For some strange reason my menu still has the same three options as i started with and one other thing to add may be an important clue. Fluxbox default menu. So, i have to assume that it is not pointing to the nice ~/.fluxbox/menu that was made from the wiki site you sent. 

I checked the man page and it said to go it will try and find a default in the /usr/share/fluxbox/menu. However it is non existant....I am going to try and copy the ~/.fluxbox/menu there and see what happens.

Edit** nope.... i rebooted and that didnt work.....

---

### Post by r4ik on 2006-01-01
No luck on this side either i got bashed in the terminal getting my sources list (acces denied ??)
Seems whe have to do a little more searching an worky but perhaps someone else reading can help.
First of all i want my sourcis list back. 
Good luck.

---

### Post by DoorGunner on 2006-01-01
I tried using $ fluxbox -i and it shows that my menu default is /etc/X11/fluxbox/fluxbox-menu rather than ~/.fluxbox/menu. 

I rechecked the ~/.fluxbox/init file and it does show that session.menuFile:	is ~/.fluxbox/menu.

I have to assume that there is another file that is overriding the defaults we have set. But where?

---

### Post by r4ik on 2006-01-01
Here is my output.

r4ik@ubuntu:~$ fluxbox -i
Fluxbox version: 0.9.12
Compiled: Jun 28 2005 12:17:32
Compiler: GCC
Compiler version: 4.0.1 20050617 (prerelease) (Debian 4.0.0-9ubuntu2)

Defaults:
    menu: /etc/X11/fluxbox/fluxbox-menu
   style: /usr/share/fluxbox/styles/Clean
    keys: /etc/X11/fluxbox/keys
    init: /etc/X11/fluxbox/init

Compiled options (- => disabled):
-DEBUG
SLIT
TOOLBAR
XPM
IMLIB2
GNOME
KDE
EWMH
REMEMBER
SHAPE
XFT
XMB
-XINERAMA
RENDER

r4ik@ubuntu:~$
compiled options disabled got to enable it (where?)
Havent got a clue.
Gonna read some more let you know asap.

---

### Post by DoorGunner on 2006-01-01
Ok .... I got it to work

what happened was when i went to ~/.fluxbox/menu i origionally saw nothing so i assumed i had to be in root. 

How ever this is not the case. As the instructions mentioned you just use your "user" $ ~/.fluxbox/menu. It will be blank. Then add the following into it. 

[begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)
[end]

I glossed over the instructions too quickly. That will learn me ...LOL

-----------------------------------------------------------------------

for yourself..... mine stated the same....with the compile options being the same as yours etc. 
if you are installing using synaptic try the above and let me know how it works

---

### Post by r4ik on 2006-01-01
Thanks for your reply i am gonna give it a go.

---

### Post by DoorGunner on 2006-01-01
thank you for putting me on the right track..... where are you at??

---

### Post by r4ik on 2006-01-01
Its bashing me around must it because it's way beyond bed time here. Gonna have a fresh look in the morning before i go to work i will get it fixed no worry's.
Thanks !

---

### Post by Ptero-4 on 2006-01-01
The compile options are the common ones given by the ubuntu package maintainers. The disabled options (debug and xinerama) doesn't affect performance or funcionality. Debug is for development (debugging) and xinerama is multi-monitor support (mostly unneded).

---

### Post by r4ik on 2006-01-01
In that case i will leave it as it is.

---

### Post by dmartin on 2006-02-15
[QUOTE=Ptero-4]and xinerama is multi-monitor support (mostly unneded).[/QUOTE]

I ran across this topic because I was looking for how to get Xinerama support in Fluxbox.  To say Xinerama is mostly unneeded, especially on a window manager, is surprising.  If anything in the entire repos needs Xinerama, it's window managers.  And I'd bet you that the percentage of people using dual displays on Linux is relatively high.  Linux and "techie" types go hand in hand, probably even moreso for Fluxbox users.  Dual displays are very good for doing technical things.

Unfortunately, I'm pretty sure I'm going to have to roll my own flux to get Xinerama.

---

