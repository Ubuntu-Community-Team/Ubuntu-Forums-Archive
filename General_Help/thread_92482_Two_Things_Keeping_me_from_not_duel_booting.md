---
title: "Two Things Keeping me from not duel booting"
date: 2005-11-19
forum: General Help
---

### Post by Drifter on 2005-11-19
1.  I can't use XDVDShrink or DVDShirk with wine.  I can't get anything to burn a backup copy of my DVD's.  Can't use Rip or anything

2.  I need a program to keep checking account on, like Quicken.  Those two and I will not duel boot anymore.

---

### Post by Zed on 2005-11-19
For #2 try GnuCash from the universe repository.

---

### Post by Drifter on 2005-11-19
Zed, I'm only about 2 to 3 weeks into linux, How do I get that from universe,  Give me a step by step if u don't mind.  Thanks

---

### Post by ofek on 2005-11-19
Adding universe ->[http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")
And for installing the software run synaptics and use the search option to find gnucash.

---

### Post by Drifter on 2005-11-19
OK now where is gnucash after I installed it.  Can't find it.

---

### Post by Drifter on 2005-11-19
I have gnucash and I can now open it but I am having trouble using it.  Also I still can't burn my backup copies of my dvd movie's in linux.  anyone want to try and guide me to the info as to how I can get these two things working.

---

### Post by JurB on 2005-11-20
*Gnucash guide : [http://www.gnucash.org/docs/v1.8/C/gnucash-guide/](http://www.gnucash.org/docs/v1.8/C/gnucash-guide/)

*Use K3b (it's in the repositories) to burn your dvd's... you can't rip them with it tough, it's just a burning application.

---

### Post by kperkins on 2005-11-20
[QUOTE=Drifter]I have gnucash and I can now open it but I am having trouble using it.  Also I still can't burn my backup copies of my dvd movie's in linux.  anyone want to try and guide me to the info as to how I can get these two things working.[/QUOTE]
You might try grisbi instead of gnucash.
As for dvd ripping, have you tried dvdrip, or K3B (both should be in the repositories)
Check out this guide to ripping at linuxquestions.org (linuxquestions.org is your friend :D):
[http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=308](http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=308)

---

### Post by kperkins on 2005-11-20
[QUOTE=JurB]*Gnucash guide : [http://www.gnucash.org/docs/v1.8/C/gnucash-guide/](http://www.gnucash.org/docs/v1.8/C/gnucash-guide/)

*Use K3b (it's in the repositories) to burn your dvd's... you can't rip them with it tough, it's just a burning application.[/QUOTE]
Actually you _can_ rip DVDs with K3b (There's a nice how-to in the K3b help docs)

---

### Post by JurB on 2005-11-21
[QUOTE=kperkins]Actually you _can_ rip DVDs with K3b (There's a nice how-to in the K3b help docs)[/QUOTE]

My bad :rolleyes:

---

### Post by Faerine on 2005-11-21
You can also try Acidrip for DVD ripping. It is also in the repositories.

---

### Post by Drifter on 2005-11-21
OK I now have grisbi and gnucash and now wine with dvdshrink.  I think my problem with all of these is that my drives are not being detected correctly.  In dvdshrink for exsample it thinks my harddrive is cdrom.  The first time I used it, dvdshrink, it started working, but I stopped it and now it will not even start.  I have an icon on the desktop that worked at first and now clicking on it does nothing.  Could someone post how the drives should be, this is probably the why grisbi and gnucash does not see my drives.  If u know of a place that I can read a how to on how to setup the drives I will be glad to read it.  Any help would be appreciated.

---

### Post by Drifter on 2005-11-21
Take a look at this and see if you can help me with the above problem.  I do not know what all this means except that I know it is all of my drives.  Anyone care to to explain how I can fix the problem with the drives not being correct in these programs  above.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

---

