---
title: "just copy home?"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by jamesdcarroll on 2009-03-28
i have my desktop machine installed with ibex and just converted my laptop.  can i just copy my home directory from one to the other?  what about things that i have installed on the desktop but haven't on this one yet?


thanks

---

### Post by Hobgoblin on 2009-03-28
The only issue with applications not installed will be desktop or menu shortcuts not working.  Or gnome applets missing.  Otherwise it should be fine.

---

### Post by pytheas22 on 2009-03-28
As the poster above says, it should be fine, except you will need to use Synaptic to install any applications that you have on your desktop but not your laptop.

The only thing I will add is that there could potentially be permissions problems (if you can't log into the desktop after copying the files, this is most likely why).  To solve those, you need to make sure that the files copied into /home on the laptop are owned by the user who will be using them, and that they have at least 744 permissions.  Basically this means running these two commands after you copy the files:
```

sudo chown -R USERNAME\: /home/USERNAME
chmod -R 744 /home/USERNAME
```

Obviously, replace USERNAME as appropriate.

---

