---
title: "Easiest way to stop gdm?"
date: 2006-02-10
forum: Installation &amp; Upgrades
---

### Post by orev on 2006-02-10
What is the easiest way to stop the display manager and go to the command line if your display drivers are not working?

I am trying to help here:

[http://ubuntuforums.org/showthread.php?t=127829](http://ubuntuforums.org/showthread.php?t=127829)

---

### Post by aysiu on 2006-02-10
[QUOTE=orev]What is the easiest way to stop the display manager and go to the command line if your display drivers are not working?[/quote] Control-Alt-F1. That'll take you to a terminal. Control-Alt-F7 will take you back to the graphical screen.

---

### Post by orev on 2006-02-10
thanks....:D

---

### Post by angkor on 2006-02-10
Ctrl+Alt-F1 doesn't stop X from running.

After going to the terminal with Ctrl+Alt+F1, you need to enter: 

```
sudo /etc/init.d/gdm stop
```

to stop X.

reconfigure X or your xorg.conf

```
sudo /etc/init.d/gdm start
```

to restart X.

---

### Post by orev on 2006-02-10
[QUOTE=angkor]Ctrl+Alt-F1 doesn't stop X from running.

After going to the terminal with Ctrl+Alt+F1, you need to enter: 

```
sudo /etc/init.d/gdm stop
```

to stop X.

reconfigure X or your xorg.conf

```
sudo /etc/init.d/gdm start
```

to restart X.[/QUOTE]

Thanks.  I got the info for my post above from another post....

UPDATE:  HEY.  NUTS.  I JUST POSTED TO THE WRONG THREAD. :p

---

