---
title: "HP deskjet won't print anything"
date: 2005-10-10
forum: Hardware &amp; Laptops
---

### Post by jonim8or on 2005-10-10
I've connected my hp deskjet 520 to my computer, and at System->Administration->Printing I have added a new printer, the HP deskjet 520.
I've restarted the cupsys, and when I send print commands, they are added to the print-queue, but not really printed. Anyone know what might be the problem?

---

### Post by coolclassic on 2005-10-10
In Kde the print manager has a stop/start option sometimes the print manger is lauched in the stop mode.

If you are using gnome I guess it might be the same problem.

---

### Post by David Haas on 2005-10-10
jonim8or--After you selected your printer in the Printer Manager, what PPD file did you select? Ubuntu Hoary has 3 in the HP directory at /usr/share/cups/model/foomatic-ppds/HP. These are:
HP-DeskJet_520-djet500.ppd.gz
HP-DeskJet_520-hpijs.ppd.gz
HP-DeskJet_520-pcl3.ppd.gz
Sometimes one works better than the others. Do you now have an unzipped copy of one of these files in /etc/cups/ppd? When a ppd file is selected, Linux places an unzipped copy in this directory.
David

---

### Post by linhgb on 2005-10-11
Hey do you happen to have an AMD64 system? I've had a similar problem with the HP LaserJet 2100 which has been working fine in various Mandrake distros (from 9.0 to 10.1) until I move to Ubuntu 5.04 on a dual core AMD64 rig. It does the same thing: print goes to queue, finishes OK, logs say everything is kosher but nothing comes out. I've been searching this forum and everytime someone, who has this problem, mentions the system in use, it's AMD64. I haven't found any solution though, mainly because the damn thing doesn't even report an error.

---

### Post by jonim8or on 2005-10-24
In my /etc/cups/ppd I have one entry: Deskjet-520.ppd
I don't have the 64 bits version.

I begin having the same problem with windows, so I guess the problem is the printer after all.

Thanks for the help anyway

---

### Post by linhgb on 2005-10-24
I solved my problem. The printer didn't like ECP on that board for some reason so I switched to EPP (via the BIOS) and it printed fine. Try that maybe.

---

### Post by Hekos on 2005-10-24
I have a similar problem with a HP DeskJet 690C.
it`s detected and the job seems to be in progres, but the printer is not responding and when u open Properties the status is:
"Ready; Parallel port busy; will retry in 30 seconds... "

is this only found on HP printers?

---

### Post by jso on 2005-12-19
[QUOTE=Hekos]I have a similar problem with a HP DeskJet 690C.
it`s detected and the job seems to be in progres, but the printer is not responding and when u open Properties the status is:
"Ready; Parallel port busy; will retry in 30 seconds... "

is this only found on HP printers?[/QUOTE]

I don't know, but I just posted last night on [http://ubuntuforums.org/showthread.php?t=64876](http://ubuntuforums.org/showthread.php?t=64876) about my Deskjet 692c (virtually the same as yours).  I'm having the same problem.  Are you running AMD64?

---

### Post by coolclassic on 2005-12-20
For the deskjet 690c you can try the printer drivers from turboprint I have found them to be very reliable and often give better print out and controll than drivers provided by your distro.

[http://www.turboprint.de/](http://www.turboprint.de/)

---

### Post by www.rzr.online.fr on 2006-05-06
[QUOTE=linhgb]I solved my problem. The printer didn't like ECP on that board for some reason so I switched to EPP (via the BIOS) and it printed fine. Try that maybe.[/QUOTE]

Can you give more reference on what ECP/EPP is ?

---

