---
title: "new install - dependtry &lt;= 4' failed."
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by kybalion on 2005-12-18
Just did a fresh install, and installation of some packages failed after the initial reboot.  It seemed to be a hang up of some gs-packages, but after I installed gs-gpl and gs, that seemed to be fine. I'm still having problems, though of this sort:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
user@ubuntu:~$ sudo dpkg --configure -a
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
Aborted

or after installing joe, for example:

Setting up wget (1.10-2ubuntu0.1) ...

dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

Is this important? Can I ignore it? How can I make it go away? I have to run sudo dpkg --configure -a after every install, which is quite annoying.

----

Update 1.

Okay, 

sudo apt-get autoclean
sudo apt-get --reinstall install ubuntu-desktop

Led me to figure out that gs-esp wasn't extracting properly, so I rm'd the deb and downloaded another one, so it got over that herdle. Now I have a new one to get over. A whole heap of packages aren't installing because dpkg is now choking on python:

user@ubuntu:~$ sudo dpkg --configure python-gst
Setting up python-gst (0.8.1-2) ...
Compiling /usr/lib/python2.4/site-packages/epydoc/gui.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
dpkg: error processing python-gst (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-gst

-------

Update 2

Gave up, reinstalled. Second install went off without a hitch.

---

