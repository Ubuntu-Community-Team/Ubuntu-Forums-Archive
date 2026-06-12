---
title: "photoprint doesn't work, shows segmentation fault"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by fenario on 2009-01-03
Dear penguins

I installed photoprint, using the latest deb. It doesn't open from the icon in the applications menu. In the terminal it shows:

rolf@rolf-laptop:~$ photoprint
Photoprint starting...
Initialized Gutenprint
Setting up gettext... photoprint, /usr/share/locale
In LayoutDB constructor
In PrintOutput constructor...
Getting name for queue 0
Queue: X5100-Series
Done...
Creating PathDBHandler...
Setting default filename
State created...
Set initial filename
Settings directory: /home/rolf/.photoprint
Created fresh stp_vars
Segmentation fault

I don't know what segmentation fault means. I made sure the permissions are in my name with the .photoprinter folder in my home folder.
I'd appreciate to get this working as it can do multiple images on one page. A nifty application.

happy new year to all Linux users

Rolf :(

---

### Post by MighMoS on 2009-01-03
A segmentation fault happens when a program does something it shouldn't, and then crashes. If this happens, you can try moving your program's settings to a temporary directory, and trying from a "clean" install. If that doesn't work, file a launchpad bug.

---

### Post by fenario on 2009-01-14
Thank you kindly Mighty MoS

Nothing helped. It used to work fine in ubuntu 7. I still have the same computer, the climate is a bit hotter, my temper also hotter....but ubuntu 8.10 seems to be the trouble. Other things are worse too now. I may revert to Ububtu 7 again! New is not always better (see Vista).

Anyway, ink cartridges are too expensive and work is not easy to come by here down under, so I can't do any printing at the moment. I'll see what the gimp can do.

A happy new year to you and your people.

Rolf

---

### Post by fenario on 2009-01-14
Ok all good now. I don't give up easily. I found this link on the forum [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1150417.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1150417.html)
and downloaded this new deb file: [http://launchpadlibrarian.net/19642102/photoprint_0.3.9-0ubuntu1_i386.deb](http://launchpadlibrarian.net/19642102/photoprint_0.3.9-0ubuntu1_i386.deb)
and that seems to do the job. It now opens the program properly. Yet to be tested.

---

