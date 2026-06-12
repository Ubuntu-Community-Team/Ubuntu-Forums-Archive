---
title: "[SOLVED] guest-session fails"
date: 2008-11-07
forum: General Help
---

### Post by loko on 2008-11-07
hello,

after some updates, the guest-session now failes when i try to start it.

this is the error-message:

```
/etc/gdm/Xsession: Beginning session setup...
xrdb: Permission denied
xrdb: Can't open display ':20'
Can't create dir /tmp/guest-home.T13885/Desktop
...
...
...
Setting IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
mkdtemp: private socket dir: Permission denied
```

I've set /tmp to 1777 or even 777 but this does not work.

Is somebody experiencing the same problems with the guest-session?
And is there a solution for the problem?

---

### Post by loko on 2008-11-09
Solved the problem.

The reason was that i linked /tmp to /home/tmp with a symlink.

After linking /tmp to /home/tmp with mount -o bind /home/tmp /tmp everything works now.

---

