---
title: "Ubuntu Freezes After Login"
date: 2005-11-13
forum: General Help
---

### Post by MrSnazzy on 2005-11-13
I just installed Ubuntu (I use Windows XP on the same computer). Every time I try to log in, it takes me to a brown screen with the Ubuntu logo and immediately freezes. I've been checking the Ubuntu site and forum for a solution for a few hours but couldn't find anything.

---

### Post by Juzz on 2005-11-13
Do you get an error message?
If so, what does it say?

---

### Post by Lambert on 2005-11-13
before you log in hit ctrl+alt+F1 and try to log in. It will be completely text based.

then type 

```
cat /var/log/syslog
and
cat /var/log/Xorg.0.log
``` 
See if there are any errors there.

Also maybe try

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by ssam on 2005-11-15
maybe this [https://wiki.ubuntu.com/UbuntuDateBug](https://wiki.ubuntu.com/UbuntuDateBug)

---

