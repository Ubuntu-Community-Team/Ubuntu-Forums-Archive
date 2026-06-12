---
title: "No GUI after install?"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by b//r0k3/n on 2009-11-02
Hey guys, I'm really new to Ubuntu/Unix and just did my first install ever last night. I installed it onto one of my partitions formatted as Ext4 and mounted at / . After that, everything went pretty good, until I actually rebooted my machine to use it. After choosing Ubuntu in GRUB, it started up, flashed the little Ubuntu logo, and then booted into a command prompt/terminal-like mode and asked for my login and password. After entering it, it stayed like that...did I do something wrong during install or what?

Also, please, forgive me if some of the terminology isn't correct/this is just me being stupid as I'm pretty new to this stuff...so...yeah. Thanks guys! :)

---

### Post by ajgreeny on 2009-11-02
Difficult to know what went wrong, but assuming you had a GUI from the live CD, if it was a live CD, try typing ```
startx
```when you have logged in to the command line interface, and if that does not get you running, tell us what error messages appear.

---

### Post by b//r0k3/n on 2009-11-02
> **ajgreeny said:**
> Difficult to know what went wrong, but assuming you had a GUI from the live CD, if it was a live CD, try typing ```
startx
```when you have logged in to the command line interface, and if that does not get you running, tell us what error messages appear.


Didn't work...error as follows:
```
21: /usr/bin/X11/X [0x80719c1]
Saw signal 11: Server aborting.
  ddxSigGiveUp: Closing log
  ddxSigGiveUp: re-raising 11

br0k3n@br0k3n-laptop: ~$

```

---

### Post by b//r0k3/n on 2009-11-02
bump

---

### Post by Raiju on 2009-11-02
do you have two video cards?

---

### Post by b//r0k3/n on 2009-11-02
Nope, I don't.

Integrated graphics on a Toshiba laptop.

---

### Post by b//r0k3/n on 2009-11-02
Here's what's happening: [http://www.youtube.com/watch?v=ARBORK3MBE4](http://www.youtube.com/watch?v=ARBORK3MBE4)

---

### Post by b//r0k3/n on 2009-11-03
Bump? Guys, I really need some help here...

---

