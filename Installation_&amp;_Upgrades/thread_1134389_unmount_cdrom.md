---
title: "unmount cdrom"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by davebridges on 2009-04-23
I am trying to do a clean install from a iso image burned to a partition.  I get to the installer but after the section on setting up partitions, i get an error that the cdrom is mounted and i need to unmout it.  The cdrom is not mounted (via sudo umount /dev/cdrom).  any idea to get through this?

---

### Post by davebridges on 2009-04-23
the actual error message is:

The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/cdrom

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?

no matter whether i click go back or continue it resets back to the original partitions and goes to the partition set up page

---

### Post by Coimbra on 2009-04-25
I've the same problem. How can we fix that?

---

### Post by mickey12gauge on 2009-04-29
Same issue here as well :(

---

### Post by VladNistor on 2009-05-15
yup, me too. This sucks since I'm not actually modifying the partition table but the installer thinks I am.

---

### Post by Szise on 2009-06-05
Help, me too :( Anyone is going to help us ???

---

### Post by blejach on 2009-06-07
same probleem here... although kubuntu 9.04 installs with no problems.

---

### Post by TheBigDogTCS on 2009-06-07
Same problem. Need a fix.

---

### Post by tascar on 2009-06-08
Same problem here as well, not been able to fix it yet, any help out there?

---

### Post by TheBigDogTCS on 2009-06-09
I made progress suing the search pane.... [http://ubuntuforums.org/showthread.php?t=1152319](http://ubuntuforums.org/showthread.php?t=1152319) I am at the same point as post #7.... But progress none the less... For refrence im trying to load Xubuntu from a USB drive on a tablet for my 2nd ever install of a NOT Windows OS>.....

---

### Post by bacchusmarsh on 2010-04-19
try work around 
[http://ubuntuforums.org/showthread.php?t=1237721&highlight=the+installer+needs+to+commit+changes]("http://ubuntuforums.org/showthread.php?t=1237721&highlight=the+installer+needs+to+commit+changes")

---

