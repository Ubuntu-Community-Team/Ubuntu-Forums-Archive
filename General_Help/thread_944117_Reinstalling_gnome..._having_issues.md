---
title: "Reinstalling gnome... having issues"
date: 2008-10-11
forum: General Help
---

### Post by SunnyRabbiera on 2008-10-11
Hey I was having issues with gnome and I decided to remove it and use KDE3 for a little bit.
But I want Gnome back, unfortunately I cannot install it as the gnome desktop package depends on gnome keyring manager and I see it has been removed from the repositories.
So how the @#$%^& am I supposed to reinstall gnome now?

---

### Post by nikgare on 2008-10-11
It hasn't been removed!
Are you sure your repositores are in order  - check that /etc/apt/sources.list has the correct lines, and do an **apt-get update**

---

### Post by Yellow Pasque on 2008-10-11
gnome-keyring replaces gnome-keyring-manager.

The best way to get gnome is:
```
sudo apt-get install gnome-desktop-environment
```

---

### Post by Murdoc_of_puts on 2008-10-19
I also am having issues with gnome...I tried to apt-get update  - and am still having the same problem with the key ring app.  I also tried to terminal install it, and the same problem is occuring.  What Repo lists should I have, or is there something else that I'm missing?  Please help.

---

### Post by Murdoc_of_puts on 2008-10-29
Rabbit- try using this link, it helped me out.  Also this guy says to try to use aptitude instead of apt-get, and I'm not having the keyring problem so far. So that might be a work arround.  Also- you might just want to wait until the new Ubuntu comes out, and snatch that up as it uses gnome by default.  Hope this helped.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

