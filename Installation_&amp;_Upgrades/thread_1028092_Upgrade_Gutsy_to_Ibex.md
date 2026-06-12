---
title: "Upgrade Gutsy to Ibex?"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by pgmer6809 on 2009-01-02
Hi, I am currently running Gutsy. I tried Hardy but it was slow and broke many things so I stuck to Gutsy.
Is it possible to upgrade directly from Gutsy to Ibex or must I go through Hardy first?

Thanks,
pgmer6809

---

### Post by cdtech on 2009-01-02
Run this in a terminal and see if it will allow you to do so:
```
gksudo "update-manager -c -d"
```

---

### Post by tommcd on 2009-01-02
> **pgmer6809 said:**
> 
Is it possible to upgrade directly from Gutsy to Ibex or must I go through Hardy first?


Skipping versions is not recommended. You must upgrade in sequence. That is, Gutsy > Hardy > Intrepid. See this:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
Since you said you had problems with upgrading to Hardy I would think the best option would be to do a clean install of Intrepid. If you have a separate /home partition all of your data will be safe. If you don't have a separate home partition, then now is a good time to back up, repartition, and create a separate home partition and install Intrepid.

---

### Post by pgmer6809 on 2009-01-02
THank you for the info.
I do have a separate /home partition, but most of the work I have put into the system involves finding packages and installing them.
Those are not in the /home partition.
If I were to do a clean install, I would have to redo all those package installs as well.
SOme of them are windoze programs under crossover office.
all in all not something i want to be spending time on.

pgmer6809

---

### Post by Sef on 2009-01-02
> If I were to do a clean install, I would have to redo all those package installs as well.

Yes, a clean install wipes out all the packages that have been installed on root.

**Back up** your files before you either upgrade or do a clean install.

---

### Post by albinootje on 2009-01-02
> **pgmer6809 said:**
> THank you for the info.
I do have a separate /home partition, but most of the work I have put into the system involves finding packages and installing them.

Okay, valid point.

Just for your information.
During the graphical dist-upgrade all non default Ubuntu repositories are normally disabled.
This means for example that if - you use VirtualBox PUEL (not OSE) via VirtualBox repositories - you will need to upgrade those later yourself.

> 
Those are not in the /home partition.
If I were to do a clean install, I would have to redo all those package installs as well.
SOme of them are windoze programs under crossover office.
all in all not something i want to be spending time on.


CrossOverLinux (Before CrossOverOffice) has the option to "archive bottles", which can be restored later or elsewhere.

And all of your installations done with CrossOverLinux should normally be in your home dir, I think it's in .cxoffice/ iirc.

If I were you, I would :
0) Test first how well Intrepid works on your machine using the 
   "live session" of the installation cdrom.
1) Make a good backup of your whole installation.
2) Start upgrading to Hardy, then to Intrepid.

---

