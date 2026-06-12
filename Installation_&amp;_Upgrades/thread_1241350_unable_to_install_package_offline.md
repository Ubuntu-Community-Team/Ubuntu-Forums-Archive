---
title: "unable to install package offline"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by m42h31 on 2009-08-15
hii all,
i'm trying to install playonlinux with offline deb package to my PC *(not connected to internet)*. the package require python-wxgtk2.8 and python-wxversion. but when i try to install both packages, ubuntu say **"Same version is available in software channel"**
[http://img36.imageshack.us/img36/5020/sameversionavailable.png](http://img36.imageshack.us/img36/5020/sameversionavailable.png)
[[IMG]http://img36.imageshack.us/img36/5020/sameversionavailable.th.png[/IMG]](http://img36.imageshack.us/img36/5020/sameversionavailable.png)
they require to download same package
[http://img199.imageshack.us/img199/8192/tobeinstalled.png](http://img199.imageshack.us/img199/8192/tobeinstalled.png)
[[IMG]http://img199.imageshack.us/img199/8192/tobeinstalled.th.png[/IMG]](http://img199.imageshack.us/img199/8192/tobeinstalled.png)
[http://img36.imageshack.us/img36/6914/downloadpackages.png](http://img36.imageshack.us/img36/6914/downloadpackages.png)
[[IMG]http://img36.imageshack.us/img36/6914/downloadpackages.th.png[/IMG]](http://img36.imageshack.us/img36/6914/downloadpackages.png)

i try install both package in terminal, but i found the same error :
```
root@m42h31-desktop:/home/m42h31/playonlinux# dpkg -i python-wxgtk2.8_2.8.9.1-0ubuntu6_i386.deb 
Selecting previously deselected package python-wxgtk2.8.
(Reading database ... 188472 files and directories currently installed.)
Unpacking python-wxgtk2.8 (from python-wxgtk2.8_2.8.9.1-0ubuntu6_i386.deb) ...
dpkg: dependency problems prevent configuration of python-wxgtk2.8:
 python-wxgtk2.8 depends on python-wxversion (>= 2.8.9.1-0ubuntu6); however:
  Package python-wxversion is not installed.
dpkg: error processing python-wxgtk2.8 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-wxgtk2.8

root@m42h31-desktop:/home/m42h31/playonlinux# dpkg -i python-wxversion_2.8.9.1-0ubuntu6_all.deb 
Selecting previously deselected package python-wxversion.
(Reading database ... 190592 files and directories currently installed.)
Unpacking python-wxversion (from python-wxversion_2.8.9.1-0ubuntu6_all.deb) ...
dpkg: dependency problems prevent configuration of python-wxversion:
 python-wxversion depends on python-wxgtk2.8 (>= 2.8.6.1-0ubuntu2) | python-wxgtk2.6 (>= 2.6.3.2.2-1ubuntu2); however:
  Package python-wxgtk2.8 is not configured yet.
  Package python-wxgtk2.6 is not installed.
dpkg: error processing python-wxversion (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-wxversion

```

somebody have solution for offline package installation? how to turn off automatic download required packages ?

---

### Post by running_rabbit07 on 2009-08-15
Not unless you already have the programs on a disk.

---

### Post by Partyboi2 on 2009-08-15
Hi, to install those packages try
```
sudo dpkg -i python-wxgtk2.8_2.8.9.1-0ubuntu6_i386.deb
sudo dpkg --configure -a
sudo dpkg -i python-wxversion_2.8.9.1-0ubuntu6_all.deb 

```

---

### Post by m42h31 on 2009-08-16
thanks Partyboi2 for help, the problem solved..

---

### Post by ArielEnter on 2009-11-13
Hi.
I was trying to install python-wxgtk and python-wxversion from Ubuntu's desktop environment in an off line computer, by double clicking in each package and following the GDebi package installer instructions, the same thing the person in this thread was trying to do.

For some reason trying to installer from the GDebi package installer in the desktop environment and using dpkg -i from the terminal, gives back differen results. Regardless that both procedures give back and error message regarding to a co dependency between python-wxgtk and python-wxversion, after using the procedure in terminal, the kerix.py gui starts working right away.

My intentions were to try to use the terminal as little as I could. but at the end, one will still have to use the terminal, not only to install the python-wxversion, but also for every update or program you get using Keryx from an on-line computer.

Unfortunately, the Keryx Linux's graphic user interface currently (v. 0.92.3 11/13/09) does not have an option to install the packages brought from an other computer. From the terminal, you got to go to a folder called packages inside the project folder and run:

sudo dpkg -i --force-depends *.deb

Which is not that bad. It can also be use to install python-wxgtk, python-wxversion and all the other Keryx dependencies stored in the same folder. 

The good news is that the Keryx team is planing on implement it in the future, according to post I read made by mac9416, which made me very happy. I really enjoyed getting to know Keryx for a friend without Internet (I'm trying to make him to use Linux jejeje), and I wanted to share my conclusions since it took me some time to come up with them.

I will like to donate some day, but I think that sharing my impressions and tips are also of a little help. 

                                 I read somewhere that if one want to use Linux one has to learn the terminal, but I believe that the only reason so many persons can use the computers today, is because of the gui, and I wish more people could be using Linux.


My friend is one of those persons who don't know a thing about the terminal, so I made the following bash for him:


                                  #!/bin/sh 
gksudo dpkg -i &#8211;force-depends "'${0%/*}/*.deb'"
 
 
It installs all deb packages located in the same folder where its located itself by just dobble clicking. Ofcourese it could be improve a lot, but it worked for us.

P.S. I forgot Keryx's team is also planing to make a Linux binary too, so that it won't be necessary to install python-wxgtk, python-wxversion to get the gui start working right a way. So is just a matter of time. Linux will be growing and growing day by day. Thanks guys.

---

