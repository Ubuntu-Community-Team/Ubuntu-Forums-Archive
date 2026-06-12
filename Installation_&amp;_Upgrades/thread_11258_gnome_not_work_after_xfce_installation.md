---
title: "gnome not work after xfce installation"
date: 2005-01-15
forum: Installation &amp; Upgrades
---

### Post by lizardking on 2005-01-15
I have a problem with gnome: i was with gnome then i have install by synaptic, XFCE.
 **I try it  then i return to gnome but when I make the login the splash doesn't start and I cannot log in  with my normal user** . Only root can do this.any error is printed to video.
some help?????? :-(

---

### Post by lizardking on 2005-01-15
**Sorry I have resolved the problem doing:** ```
root@iac chown <user> -R -v /home/<user>
```

---

