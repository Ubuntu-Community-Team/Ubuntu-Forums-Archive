---
title: "Does Console Boot Faster? How To Boot It?"
date: 2008-07-18
forum: General Help
---

### Post by ForksHolder on 2008-07-18
Hello,

I heard that booting to console is faster. if it does, how can i do it?


Thanks,
~ForksHolder.

---

### Post by hal8000 on 2008-07-18
> **ForksHolder said:**
> Hello,

I heard that booting to console is faster. if it does, how can i do it?


Thanks,
~ForksHolder.


Yes booting to init 2 is faster because you dont have to load the X window system; however Hardy for me loads in 26 seconds so its quite fast.
You can install
sudo apt-get install sysv-rc-conf

to remove unneccessary startup services, or remove gdm from runlevel 5, then the system will boot into console mode.

If you dont know what youre doing then stop, as you can make your system unusuable.
Alternatively you can modify /etc/inittab and change the default run level to 2.

---

### Post by fsmithred on 2008-07-18
I thought ubuntu had the same runlevel scheme as debian - gdm starts in runlevel 2, which is the default. Removing gdm from runlevel 2 will result in booting to console, but it doesn't really make anything happen faster - it just stops doing stuff sooner. Any time you save will be added back in when you start the desktop.

You can do it with sysv-rc-conf or on command line:
[http://ubuntuforums.org/showthread.php?t=803939](http://ubuntuforums.org/showthread.php?t=803939)

---

### Post by bodhi.zazen on 2008-07-18
> **hal8000 said:**
> Yes booting to init 2 is faster because you dont have to load the X window system; however Hardy for me loads in 26 seconds so its quite fast.
You can install
sudo apt-get install sysv-rc-conf

to remove unneccessary startup services, or remove gdm from runlevel 5, then the system will boot into console mode.

If you dont know what youre doing then stop, as you can make your system unusuable.
Alternatively you can modify /etc/inittab and change the default run level to 2.

I see you come from a RPM based system or Slackware.

Ubuntu uses upstart and what is left of run levels, all run levels are now the same.

The default "run level" in Ubuntu is 2. Os you can :

```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/s30gdm
```

---

