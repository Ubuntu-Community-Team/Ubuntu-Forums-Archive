---
title: "I broke Xorg, any suggestions?"
date: 2011-07-09
forum: Hardware
---

### Post by Carl Foxmarten on 2011-07-09
I was cleaning out my Ubuntu Natty install and told Synaptic to remove *all* unused configuration files.

Next time I booted the system, the screen started flashing and the graphical login never showed up.

If I'm not using the restricted ATI drivers for my ATI Radeon HD 4350, I can use the text consoles to have a look at the error logs, otherwise I have to use another Ubuntu box to SSH in to have a look.

I can start Xorg from the text consoles, and it'll work just fine, but it will NOT automatically start on boot-up.

Any suggestions as to how I should fix this?
(I also don't know what logs and messages to put here, [aside from the Xorg log file](http://pastebin.com/3mPyrnZi), so please let me know what you want to see so you can help me)

---

### Post by Carl Foxmarten on 2011-07-09
Never mind, I figured out (from [this thread]()) that there was a missing "user" for GDM and that reinstalling the gdm package was enough to fix it.

The following line will fix this issue:
```
$ sudo apt-get install --reinstall gdm
```

---

