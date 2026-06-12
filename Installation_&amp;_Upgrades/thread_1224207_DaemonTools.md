---
title: "DaemonTools"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by Dreygz on 2009-07-27
I'm pretty much a complete noob so I could really use the help... 
when I try to install new games that I have downloaded on-line all the guides say to use daemon tools (because I don't know how to manually mount the ISO image onto a drive or w/e it is I'm supposed to do)... but every time I try to install daemon tools it pops up with an error message... is there any way someone can explain to me how to get this working in a language I can understand?... also if there is any alternative to DT that will work easier? thanks.

---

### Post by Bucky Ball on 2009-07-27
The error message it is throwing would help. :)

---

### Post by Dreygz on 2009-07-27
Internal setup error. Error Code:256. Contact support.
and the same error message appears no matter which version I try to install. tried opening it with wine and I tried opening w/o wine same problem.

---

### Post by vinutux on 2009-07-27
Deamontools are used for mounting iso and nrg images to hard disk instead of burn a cd and run from it (a method of visualization)....

deamontools is windows app not native ubder linux...use **[COLOR="DarkGreen"]gdiskiso[/COLOR]** instead of mounting images here (mounting is so simple here under terminal..but recommended gui way)

install gmountiso ```
sudo apt-get install gmountiso
```

---

### Post by shiroyoshida on 2009-07-27
gmountiso is great! 

Thank you for the suggestion vinutux! I've been looking for something like this for the last four hours...

---

### Post by Dreygz on 2009-07-27
when I try to mount it to my CD-ROM or CD-ROM0 it goes into the home folder into media and then tells me that these folders are not empty and wont mount it. Also when i try to open up oblivion it says we do not detect a cd/dvdrom drive on this computer? i have one... so i dont quite understand...

---

### Post by vinutux on 2009-07-27
yeh...there is some problem related to some type of cds

```
sudo mount /dev/cdrom /media/cdrom
```

---

### Post by Dreygz on 2009-07-28
for some reason it keeps popping up the same issue...i mounter the iso to both the cdrom and the cdrom0 and it says unable to find cdrom/dvd drive on your computer could this possibly be a hardware issue wires not connected right? also "disk" that it uses is usually a dvd... if that changes anything.

---

### Post by vinutux on 2009-07-28
> **Dreygz said:**
> for some reason it keeps popping up the same issue...i mounter the iso to both the cdrom and the cdrom0 and it says unable to find cdrom/dvd drive on your computer could this possibly be a hardware issue wires not connected right? also "disk" that it uses is usually a dvd... if that changes anything.

Put disk in the drive and hit this command
```
sudo fdisk -l
```

It list all partions...check there is your cd/dvd

and use [COLOR="Red"]/dev/sdb or /dev/scd[/COLOR] instead of /dev/cdrom

---

