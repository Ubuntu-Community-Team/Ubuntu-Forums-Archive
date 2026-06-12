---
title: "Problem after Wubi unistallation"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by applecake on 2009-05-05
Hiya!
I installed Ubuntu 9.04 via Wubi. Then I uninstalled it via "Add/ programs" in the control panel in Windows Xp, and I've also checked that there no longer is a map called "ubuntu" on my HDD. Still the boot chooser, where you choose between Windows and Ubuntu(is it called GRUB?), shows up at boot. Why does the list still show up?
(I also tested to choose Ubuntu, but that doesnt work. It says some file is gone, or something like that..)

Tanks in advance.

---

### Post by Partyboi2 on 2009-05-05
Hi, check your C:\boot.ini file that the entry for Ubuntu has been removed.

---

### Post by applecake on 2009-05-05
Strange.. Seems like I dont have that file.. I searched the whole C: for files with "boot" in the name. Found 22, but none of them were directly on C:, and everyone had more than boot in the filename, e.g. bootstat. But it feels like I've seen it before.
Maybe it did go away in the unistallation of Ubuntu? :(
Can it reappear if I reinstall via Wubi?

---

### Post by Partyboi2 on 2009-05-05
Try another way, right click on "My Computer" then select  the "Advanced" tab and under "Startup and Recovery" select "Settings" then under "System Startup" press "edit" and check if the entry for ubuntu has been removed.

---

### Post by Cyberhwk on 2009-05-07
I have this same problem, my boot.ini file looks like...

> [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"


Do I just delete "C:\wubildr.mbr = "Ubuntu"?

---

### Post by Partyboi2 on 2009-05-07
Yes, that is correct.

---

### Post by applecake on 2009-05-07
Tanks for the help! :)

---

### Post by Cyberhwk on 2009-05-07
Yeah, sorry to hijack **AppleCake**'s thread.  But this worked for me too.  Thank you.

Maybe someday I'll come over to Linux, but it'd just be a little too much at the moment.

---

