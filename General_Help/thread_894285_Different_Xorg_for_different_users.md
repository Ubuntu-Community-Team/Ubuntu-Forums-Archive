---
title: "Different Xorg for different users?"
date: 2008-08-19
forum: General Help
---

### Post by Paqman on 2008-08-19
Does anyone know if it's possible to specify a different Xorg config for different users?

Basically, I have a TV and a monitor plugged into my desktop. I'd like an easy way of switching from one to the other without fiddling about in nvidia-settings. If I could simply set up an extra user configured to user the TV instead of the monitor that would be an easy win.

Is there some subtlety to Xorg that i'm missing that would allow this?

---

### Post by LateNiteTV on 2008-08-22
have the user run xorgconfig under their account. it should write the xorg.conf file to their home dir and use that one upon starting X.

---

### Post by Paqman on 2008-10-30
No such command as xorgconfig, apparently.

Saving a xorg.conf to the user's home from the Nvidia X panel doesn't work either.

---

### Post by x1a4 on 2008-10-30
> **Paqman said:**
> Saving a xorg.conf to the user's home from the Nvidia X panel doesn't work either.

Can't you just copy it normally?  
```
cp /etc/X11/xorg.conf ~
```

---

### Post by Paqman on 2008-10-30
> **x1a4 said:**
> Can't you just copy it normally?  
```
cp /etc/X11/xorg.conf ~
```

It's not that it doesn't save, it just doesn't use that copy when I log in. It defaults to the one in /etc/X11. How do I point it to the one in /home?

---

### Post by syxbit on 2008-10-30
the benefits to this would be huge (AFAIK it's not yet possible)

you could log in as one user to use integrated graphics
and log in as another to use dedicated graphics

my laptop has both, and vista would let you switch, but not linux

---

