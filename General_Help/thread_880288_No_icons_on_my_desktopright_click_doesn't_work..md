---
title: "No icons on my desktop/right click doesn't work."
date: 2008-08-04
forum: General Help
---

### Post by S3loth on 2008-08-04
I can't remember how this happened, but I think I was trying to hide my icons when it happen, might have been something with Compiz. Anyhow, no icons are showing up on my screen and right click doesn't work. Its like there's some kind of glass between the mouse and desktop.

---

### Post by drs305 on 2008-08-04
If your 'show desktop' setting were turned off, this will restore it:
```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'

```

---

### Post by S3loth on 2008-08-04
Yep! That worked! (Note: I did have to log-out and login for it to take effect)

---

### Post by Sav on 2009-09-02
For me doesn't work.
I first installed ubuntu netbook remix, then I switched to the "standard" ubuntu-desktop.
Now my settings are strange: when I create a new user, the desktop is blocked, still I can create files and folders in it by nautilus, terminal, etc...

---

### Post by drs305 on 2009-09-02
> **Sav said:**
> For me doesn't work.
I first installed ubuntu netbook remix, then I switched to the "standard" ubuntu-desktop.
Now my settings are strange: when I create a new user, the desktop is blocked, still I can create files and folders in it by nautilus, terminal, etc...

Another netbook user and I spent a good bit of time trying to restore the Trash icon on his Ubuntu desktop. It would show on the netbook Desktop but no matter what we tried we couldn't get it to appear when he switched over. There are obviously some things about the netboot/Ubuntu Desktop interface that still need to be worked on it seems.

---

### Post by cowpog on 2012-01-27
I know this is from along time ago and you might not be on this site anymore but what am I supposed to do with that because I have the same problem?

---

### Post by BlinkinCat on 2012-01-27
> **cowpog said:**
> I know this is from along time ago and you might not be on this site anymore but what am I supposed to do with that because I have the same problem?


You're right - this thread is too old - you should start a new one - :)

---

### Post by nothingspecial on 2012-01-27
Please start a new thread giving as much detail of your problem as you can.

Closed.

---

