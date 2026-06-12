---
title: "Default or Realtek sound drivers?"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by Ub1476 on 2007-06-06
I could hear sound with the default drivers, but could not make it lower or higher. Neither the volume control or sound wheel worked. Well, I tried to install the Realtek drivers but then I got this error: 

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp

/etc/gdm/PreSession/Default. runnning: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0,Xservers" -h " " -l ":0" "myusername"

/etc/gdm/Xsession: Beginning session setup

gnome-session: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory
```

Which were fixed by reinstalling libasound2. Upon installing the drivers manually (auto did not work), I got several errors, like directory not found etc, so it kinda installed unsuccessfully.. First of I want to reinstall the default drivers, cause right now I have no sound at all. Secondly I might try to look at the Realtek drivers again, and see if I figure out the problem.. 

So, I suppose there's a simple code out there to reinstall default drivers..?
For further helping I got a Realtek High Definition audio card.

Thanks in advance, Ub:p

---

### Post by Ub1476 on 2007-06-06
bump

---

### Post by Ub1476 on 2007-06-07
Bump

---

### Post by Ub1476 on 2007-06-07
Bumpetibump

---

### Post by Ub1476 on 2007-06-07
Bump

..............

Last bump.................
..

---

### Post by si_harp on 2007-06-13
Hi, I'm having a similar problem...

[http://ubuntuforums.org/showthread.php?t=470589](http://ubuntuforums.org/showthread.php?t=470589)

Anyone have any suggestions?

Thanks. si

---

### Post by si_harp on 2007-06-15
Anyone? Bump

---

### Post by si_harp on 2007-06-15
FIXED!  :D

Found this thread [http://ubuntuforums.org/showthread.php?t=461894](http://ubuntuforums.org/showthread.php?t=461894) 

With thanks to engla who suggested trying...
[B]
*apt-get install --reinstall libasound2*[/B]

Fixed the problem, didn't even need to reboot to log on properley!  

Hope this helps someone. Si

---

