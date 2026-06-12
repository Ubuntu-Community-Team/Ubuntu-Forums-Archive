---
title: "Turning on multithreading"
date: 2004-12-03
forum: Hardware &amp; Laptops
---

### Post by deception on 2004-12-03
Before on Slack, I added hdparm  -c3 -m16 /dev/hda to [b] /etc/rc.d/rc.local but this file does not exist on Ubuntu. Where should I put it?

Many thanks,
deception

---

### Post by cabu on 2004-12-03
You need to edit /etc/hdparm.conf to your needs. This file gets called up by the hdparm script in /etc/rcS.d at boot time.

---

### Post by jdong on 2004-12-03
Not at a ubuntu station right now, but I could swear debian keeps that in **/etc/default/hdparm**... Oh well, could be RedHat sysconfig-itis....

---

### Post by wallijonn on 2004-12-05
Debian keeps it at [COLOR=Green]/etc/default/hdparm[/COLOR] but Ubuntu puts it in [COLOR=Green]/etc/hdparm[/COLOR].

Since you're used to sudo hdparm  -c3 -m16 /dev/hda, when you [COLOR=Red]sudo gedit /etc/hdparm[/COLOR], first make a backup copy of the file, then go to the end of the list, copy the last part which refers to /dev/hda, copy, past to the end, then uncomment the # (delete the #'s). 

Since you are hitting /dev/hda you will be hitting the controller. So be careful if you have two devices on that controller. you may have to apply them separately, one for /dev/hda1 and one for /dev/hda3, for example.

btw, why did you name it "Turning on multithreading"?

---

### Post by cabu on 2004-12-05
[QUOTE=wallijonn]Debian keeps it at [COLOR=Green]/etc/default/hdparm[/COLOR] but Ubuntu puts it in [COLOR=Green]/etc/hdparm[/COLOR].

Since you're used to sudo hdparm  -c3 -m16 /dev/hda, when you [COLOR=Red]sudo gedit /etc/hdparm[/COLOR], first make a backup copy of the file, then go to the end of the list, copy the last part which refers to /dev/hda, copy, past to the end, then uncomment the # (delete the #'s). 

Since you are hitting /dev/hda you will be hitting the controller. So be careful if you have two devices on that controller. you may have to apply them separately, one for /dev/hda1 and one for /dev/hda3, for example.

btw, why did you name it "Turning on multithreading"?[/QUOTE]

How can you have more than one device on /dev/hda? I can see where you could have  multiple partitions on /dev/hda, but not mutliple devices.

---

### Post by wallijonn on 2004-12-06
I have a dual boot W98SE and Ubuntu. My Ubuntu is on hda2. Therefore I can [color=green]sudo hdparm -tT /dev/hda[/color] or [color=green]hdparm -tT /dev/hda2[/color]. The same goes for [color=green]-i, -I, -m16, -c3, -u1, -X69, [/color]etc. Actually X69 won't work for me (ATA100).

---

