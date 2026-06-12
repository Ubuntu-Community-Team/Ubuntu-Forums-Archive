---
title: "make command problems"
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by xander848 on 2006-04-30
Hey I followed the how-to to set up the wireless with ipw2200 but got stuck at one point.  When i type the make command it says:

alex@Ubuntu:~/ieee80211-1.0.3$ make
Checking in /lib/modules/2.6.12-9-386/build/ for ieee80211 components...

/lib/modules/2.6.12-9-386/build/include/config/ieee80211

Above files found.  Remove? [y],n y

 Old ieee80211 references found.  In order to build the ieee80211
 subsystem, prior versions must first be removed.  You can perform
 this task by running this makefile as root via:

        % sudo make check_old

 and answering Y to remove the file references.

 Aborting make.

make: *** [check_old] Error 1

I have tried using sudo make check_old as it says but it still does not work.  I am new to linux so if you could please tell me what i need to type in terminal that wouldbe great. Thanks in advance

---

### Post by nilezon on 2006-05-05
Download latest version of IEEE80211:
[http://ieee80211.sourceforge.net/downloads.php]("http://ieee80211.sourceforge.net/downloads.php")

---

