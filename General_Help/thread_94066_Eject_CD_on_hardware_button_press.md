---
title: "Eject CD on hardware button press"
date: 2005-11-23
forum: General Help
---

### Post by SirKillalot on 2005-11-23
Hi, is there a way to make my system unmount (if necessary unmount it by force) and eject my cdrom if I press the button on my cdrom drive?
Regards.

---

### Post by frodon on 2005-11-23
If you want to eject the CD, using the button, run this command :  ```
sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'
```If you want to create an icon to eject the cd : [http://ubuntuforums.org/showthread.php?t=52768&highlight=cd+eject](http://ubuntuforums.org/showthread.php?t=52768&highlight=cd+eject)

---

### Post by Sir_Yaro on 2005-11-23
Can You explain how and when it's should work? 
Beacause it's not working for me - none effect...

p.s. I thought this function need a supermount module to be compiled in the kernel...

---

### Post by SirKillalot on 2005-11-23
any other way then?

---

### Post by neighborlee on 2005-12-10
[QUOTE=SirKillalot]Hi, is there a way to make my system unmount (if necessary unmount it by force) and eject my cdrom if I press the button on my cdrom drive?
Regards.[/QUOTE]

You should use this::

[http://bugzilla.ubuntu.com/show_bug.cgi?id=11480](http://bugzilla.ubuntu.com/show_bug.cgi?id=11480)

cheers
neighborlee

---

