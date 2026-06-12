---
title: "find out which driver im using"
date: 2008-07-10
forum: General Help
---

### Post by funnypanks on 2008-07-10
i installed archlinux but the video doesnt work well
in ubuntu my video works perfectly, but when i look in xorg.conf but it says configured device. is there a way to find out which driver is being used and with which options?

---

### Post by carcdrcdr on 2008-07-10
To show all installed packages: 
dpkg --get-selections | grep packagename

To show more info about the package:
dpkg -L packagename

---

### Post by funnypanks on 2008-07-11
well both intel and i810 drivers are installed
im just as confused as before

---

### Post by rogier.de.groot on 2008-07-11
Check the /var/log/X.org.log file, it should give you lots and lots of details about everything X does...
EDIT: Alternatively, "lsmod" may also list your video driver... maybe

---

### Post by funnypanks on 2008-07-11
> **rogier.de.groot said:**
> Check the /var/log/X.org.log file, it should give you lots and lots of details about everything X does...
EDIT: Alternatively, "lsmod" may also list your video driver... maybe

thanks for the reply but the log file is empty

---

### Post by rogier.de.groot on 2008-07-12
Make that /var/log/Xorg.0.log and it pretty much can't be empty - unless X hasn't started or something...

---

### Post by funnypanks on 2008-07-15
thanks rogier. but in the end i just gave up. i looked at the logs and they match up almost perfectly in the 2 os's and arch is faster, but i just don;t have the time to keep tweaking it

---

