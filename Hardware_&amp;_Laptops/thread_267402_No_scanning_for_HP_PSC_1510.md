---
title: "No scanning for HP PSC 1510"
date: 2006-09-28
forum: Hardware &amp; Laptops
---

### Post by cicoandcico on 2006-09-28
I have successfully installed this printer with the gnome wizard and printing works fine.
However, if i start xsane, it reports that "**no device is available**". according to linuxprinting, this device should **work perfectly**.
this is partly true: if i boot dapper live cd xsane works, but in my installation it does not.

**there is another issue** (maybe related?): if i start hp-toolbox i get this:
```
cicoandcico@cico-desktop:~$ hp-toolbox

 HP Linux Imaging and Printing System (ver. 0.9.7)
 HP Device Manager ver. 6.0

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

 [ERROR]: Unable to connect to HPLIP I/O. Check and make sure HPLIP is running.
 [ERROR]: Aborting.

```

is there a way to "reset" xsane? i tried to purge and reinstall the packages, but that's the same.

---

### Post by Matmas on 2006-09-28
Check (ps aux | grep hp) and make sure (sudo /etc/init.d/hplip start) HPLIP is running.

Hope it helps.

---

### Post by cicoandcico on 2006-09-29
wow, that solved my problem! thanks, really. however, i had to add manually the service at startup, with:
```
# update-rc.d hplip defaults
```


i also managed to start hp-toolbox following these instructions:

[http://ubuntuforums.org/showthread.php?t=95329](http://ubuntuforums.org/showthread.php?t=95329)

the problem of that user was the same of mine.

---

