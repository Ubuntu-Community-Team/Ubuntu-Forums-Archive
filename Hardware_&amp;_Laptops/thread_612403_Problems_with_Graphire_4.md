---
title: "Problems with Graphire 4"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by bodhisaxva on 2007-11-13
Hello

I am very new to Linux, in fact, only several days into it ...

So far I am happy, although finding solutions for hardware has been a bit of a frustration.

After finding solutions for my wireless card, I am having troubles with my Graphire 4 tablet. I have tried several suggestions on the forum, but it seems as soon as I change my xorg.conf file, I am no longer able to even reboot my system and have to reinstall linux from scratch. To even change the xorg.conf file and save the changes, I have to log in under "root", which has been a bit of a challenge as well, involving the change of settings to even allow me to log in as a root user, and a warning that I should really not be doing so.

In any case, I have the latest Ubuntu, Gutsy Gibbon, 7.10, I have installed all the wacom-tools and xserver-xorg-input-wacom from the synaptic package manager with no noted change in performance.

I am scared to touch my xorg.conf file again, but I will probably have to ... can any one give me some advice, or perhaps a definitive change to make to xorg.conf given that I have a graphire 4 tablet (USB) and the OS listed above?

Thank you so much!

---

### Post by Scunizi on 2007-11-13
Ah.. the dreaded "Won't boot so I have to reinstall".. hang on.. it's much easier than that.  If you make changes to xorg and find you can't boot, you should either be booting into a "text" environment or try booting into the rescue mode (kernel option 2).  Once you're in the text mode you should be able to log in with your normal user name and pass.  Now the next point.  

For safety, you should never log into the root account by means discovered via IRC or other sources.. sudo is your friend.  To edit any config file or do anything as root, preface your command with sudo.  For instance, to edit xorg, get to the terminal and type "gksudo gedit /etc/X11/xorg.conf".  In this case I'm using gksudo which is neccessary with launching a gui app.  

When modifing xorg it will typically create a backup if you didn't do that to begin with.  So when editing xorg, to be safe make a back up of the functional one. "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup".  

As for the Graphire 4, I had mine working under Dapper but have yet to play with the setup in Gutsy.  I'll monitor this thread to read the answers and if I come up with a solution prior to someone else I'll post here..

Welcome!

---

