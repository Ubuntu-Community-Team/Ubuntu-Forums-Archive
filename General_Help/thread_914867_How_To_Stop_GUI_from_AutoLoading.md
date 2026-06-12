---
title: "How To Stop GUI from AutoLoading??"
date: 2008-09-09
forum: General Help
---

### Post by matey3 on 2008-09-09
Hi All:

I know I have seen the answer here a while back but my machine crashed and with new installation I lost all my notes/files etc...
I would like to know how I could get g d m from loading at startup?
There was a line of code that some body posted here b4 but I just cant remember...

Thanks so much!

---

### Post by fsmithred on 2008-09-09
If you want to boot into multi-user cli, then you need to create a multi-user, non-graphical runlevel. Just turn off gdm in runlevel 2. You can use update-rc.d to do this, or you can do it manually:
Code:

sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K70gdm

and to reverse that:
Code:

sudo mv /etc/rc2.d/K70gdm /etc/rc2.d/S30gdm

---

### Post by HermanAB on 2008-09-09
Switching runlevels:
init 3
init 5

The default is in /etc/inittab.  Look in there and change the 5 to a 3.

Cheers,

Herman

---

### Post by matey3 on 2008-09-09
Thank You!
it is not the same one but I guess this will also work fine!
thanks very much!
regards;

OH I found it (on this site but via google?) I did a search here before I posted this thread but the search has changed here since a few months ago? It used to work better and at the start of a thread would show you many similar posts? Now it is manual but does not work so accurately?

[http://ubuntuforums.org/showthread.php?t=254540](http://ubuntuforums.org/showthread.php?t=254540)

any ways the command I was looking for is:
update-rc.d -f dgm remove 
and of course gdm or kdm defaults (to put it back in the startup)!


Thanks a lot!

---

### Post by fsmithred on 2008-09-09
> **HermanAB said:**
> Switching runlevels:
init 3
init 5

The default is in /etc/inittab.  Look in there and change the 5 to a 3.

Cheers,

Herman

In ubuntu and debian, the default runlevel is 2. Runlevels 2-5 are all the same - multi-user, graphical. And /etc/inittab has been gone since Feisty or earlier. I don't remember the name of the file that replaced it.

If you just change runlevel 2 to be non-graphical, then you can either use startx to get the desktop, or you can do 'sudo init 3' (or 4 or 5, since they're still the same). If you just use startx, you may have to drop back to cli to reboot or halt. (Not sure if ubuntu is the same as debian on that last point.)

---

### Post by oldos2er on 2008-09-09
> **HermanAB said:**
> Switching runlevels:
init 3
init 5

The default is in /etc/inittab.  Look in there and change the 5 to a 3.

Cheers,

Herman

 Ubuntu has no inittab file.

---

