---
title: "using sudo prevents login"
date: 2005-11-20
forum: General Help
---

### Post by cran on 2005-11-20
Anyone encountered this?

When I use sudo to run a program like, say, kwrite, it will change ownership on the file .ICEauthority to root:root.

Next time you try to login the following will happen, depending on if the desktop you're trying to start is gnome or kde:

 gnome: X/kdm restarts with no further information about the error
 kde: A warning message saying the file .ICEauthority can not be written to.

I don't know what program needs to write to .ICEauthority but I guess it's some part of Xorg. However, what should be done in such a case?

A similar things happens when you run aptitude with sudo, it will chown your .aptitude directory to root:root.

---

### Post by aysiu on 2005-11-20
I don't know if this helps, but you may want to try:
[http://ubuntuforums.org/showthread.php?t=1583](http://ubuntuforums.org/showthread.php?t=1583)

Also, why are you doing ```
sudo kwrite
``` on files that don't already belong to root? If they belong to you, cran, you can just do an ordinary (non-sudo) kwrite.

---

### Post by Seth on 2005-11-20
[QUOTE=aysiu]I don't know if this helps, but you may want to try:
[http://ubuntuforums.org/showthread.php?t=1583](http://ubuntuforums.org/showthread.php?t=1583)

Also, why are you doing ```
sudo kwrite
``` on files that don't already belong to root? If they belong to you, cran, you can just do an ordinary (non-sudo) kwrite.[/QUOTE]
When using KDE apps, you must use kdesu.
```
kdesu kwrite
```
And I'd assume he's doing that so he can edit files that belong to root, like xorg.conf.

---

### Post by aysiu on 2005-11-20
[QUOTE=Seth]When using KDE apps, you must use kdesu.
```
kdesu kwrite
```[/quote] That's the way it should be done, but sudo kwrite should still work.

> 
And I'd assume he's doing that so he can edit files that belong to root, like xorg.conf. That was my question. cran said > When I use sudo to run a program like, say, kwrite, it will change ownership on the file .ICEauthority to root:root. Why would cran have a complaint? If xorg.conf "changed" to root:root... well, it already belonged to root to begin with.

---

### Post by Seth on 2005-11-20
No, the file **.ICEauthority** is changing to root:root; read his post again. .ICEauthority is needed for proper logging in and if it gets owned to root, which happens when you run KDE apps with sudo, things break. sudo kwrite may **appear** to work, but it breaks things terribly and should NEVER be used, so don't tell people that it "should still work". Even Riddell will come after you for using sudo + a KDE app.

---

### Post by aysiu on 2005-11-20
Whoops.

---

