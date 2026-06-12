---
title: "get default xorg.conf back"
date: 2005-10-07
forum: Hardware &amp; Laptops
---

### Post by snowsquirrel on 2005-10-07
I accidently blew away my xorg.conf.  How can I get it back, or re-run the program which generated it during the install?

---

### Post by markuman on 2005-10-08
dpkg-reconfigure xserver-xorg

---

### Post by codejunkie on 2005-10-08
[QUOTE=snowsquirrel]I accidently blew away my xorg.conf.  How can I get it back, or re-run the program which generated it during the install?[/QUOTE]
If you have customized your /etc/X11/xorg.conf file and you want to try and recover it if possible see #1

If you just wan't to recreate a new default one the way the installer did see #2
---------------------------------------------------------------------------------------------------------
#1 open a terminal go to the /etc/X11 folder with ```
cd /etc/X11
``` and do ```
ls
``` to show the contents of that folder there might be a hidden backup copy of your xorg.conf file it will look like this ```
xorg.conf~
``` if you have a working gui you can switch to that xorg.conf file with this 
```
sudo gedit /etc/X11/xorg.conf~
``` remove the ~ from the end of the file save and exit. if you do not have a working gui then use this command 
```
nano /etc/X11/xorg.conf~
``` hit ctrl o to save remove the ~ from the end of the file hit enter then hit ctrl x to exit nano then reboot.
---------------------------------------------------------------------------------------------------------
#2 run this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

