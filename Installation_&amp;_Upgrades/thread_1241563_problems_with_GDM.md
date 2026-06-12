---
title: "problems with GDM"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by bgbnbigben on 2009-08-16
Hey guys,

So yesterday i went on a massive package culling spree, and then had the good sense to restart my computer.
But i think i killed GDM, or one of it's dependencies. Initially it couldnt start GDM, but after 'sudo apt-get purge gdm' and then apt-get install gdm, /etc/init.d/gdm status returns ```
* gdm is running
```.

However, my desktop is still missing quite a few things, namely the task bar down the bottom and the task bar at the top. I've also lost support for alt-f2 and things like that.
Does anyone know what i might have done? I understand that the description above was fairly useless, but i can provide screenshots if necessary :)
It's just a real pain in the butt to have to do everything blindly and access all my programs from /usr/bin.

---

### Post by Partyboi2 on 2009-08-16
Hi, boot to a terminal and
```
sudo apt-get --reinstall install ubuntu-desktop
``` this should pull in any missing packages for the Desktop.

---

### Post by bgbnbigben on 2009-08-16
ahh, that did the trick.
Cheers

---

### Post by junksortie on 2009-08-31
Hi have the same problem, but a little agravated.

I cant even get the login screen and directly goes to prompt.

and while i try to 

sudo gdm stop OR sudo gdm-restart

it says gdm already running!


the above is not helping!

---

