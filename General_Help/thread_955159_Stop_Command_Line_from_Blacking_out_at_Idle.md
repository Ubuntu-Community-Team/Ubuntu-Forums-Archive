---
title: "Stop Command Line from Blacking out at Idle"
date: 2008-10-21
forum: General Help
---

### Post by awells527 on 2008-10-21
I'm guessing that the terminal session on my server installation is going black as a screen saver of sorts, but I am running server installations in a VMWare session, so there is no reason for it to be blacking out.  Is there a way to disable this?

I have seen other solutions that involve editing the xorg.conf file, but this is not a GUI installation.

---

### Post by spiderbatdad on 2008-10-22
not sure but this seems like a power management issue...apparently acpi is one type of power management, used by the bios. If you have this, it can be turned off with the kernel option acpi=off. Apm, advanced power management, is run by a daemon located in /etc/init.d/apmd. These two methods of power management may only apply to laptop...again, not sure. Good luck.

---

### Post by jerome1232 on 2008-10-22
I remember seeing this pop in a thread or two, I found one hopefully one  of it's solutions will get you on track (see post number 4 I think that's the answer)

[http://ubuntuforums.org/showthread.php?p=5520101](http://ubuntuforums.org/showthread.php?p=5520101)

> ```
setterm -blank 0
or
setterm -powersave off
or
setterm -blank 0 -powersave off

"man setterm" for more info
```

---

### Post by spiderbatdad on 2008-10-22
good call...this looks correct, especially as -blank is used to set blanking of virtual terminals.

---

### Post by awells527 on 2008-10-22
Thanks guys for your responses.  jerome1232's solution worked like a charm. :)

---

