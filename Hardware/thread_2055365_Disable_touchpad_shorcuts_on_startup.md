---
title: "Disable touchpad shorcuts on startup"
date: 2012-09-09
forum: Hardware
---

### Post by Jigsaw52 on 2012-09-09
Hi

I have Xubuntu 12.04 and a synaptics touchpad on a Acer laptop.
I'm trying to disable the paste shortcut (tap in top right corner) when Xubuntu starts.
synclient RTCornerButton=0 disables it, but doesn't work when running at startup.

I tried:
 - synclient RTCornerButton=0 in Applications>Settings>Settings Manager>Autostarted apps
 - bash -c "synclient RTCornerButton=0" in Applications>Settings>Settings Manager>Autostarted apps
 - synclient RTCornerButton=0 in .profile

Nothing has worked. How can I disable this shortcut automatically at startup?

---

### Post by Toz on 2012-09-09
Hello and welcome to the forums.

Perhaps its not working because the command is being executed before the X session is ready. Try delaying the execution of the command to see if that helps:
```
bash -c "sleep 5s; synclient RTCornerButton=0"
```
...adjust 5s (5 seconds) as needed.

---

### Post by Jigsaw52 on 2012-09-10
That solved it. Thanks!

---

