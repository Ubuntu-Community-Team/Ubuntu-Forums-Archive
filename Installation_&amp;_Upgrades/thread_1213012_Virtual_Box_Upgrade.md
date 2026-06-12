---
title: "Virtual Box Upgrade"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by Cametan on 2009-07-14
Virtual Box told me now 3.0.2 is available.
So I did this:

> sudo aptitude update
sudo aptitude upgrade

But it failed.
Bash told me that Virtual Box depends on Python 2.5 and Python2.5-minimal package is broken.
I tried to reinstall to set up Python 2.5, but it failed again. It implies Python2.5 itself on the repository is broken, I guess.
Is anyone here experienced same? If so, it is better to report this, isn't it?


Thanks.

---

### Post by Operan on 2009-07-14
-Add this line to your source.list:
> deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free

-Download and import key:

> wget -q [http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc) -O- | sudo apt-key add -


-and:
sudo apt-get update

-Remove your old virtual box
-Install VB 3.0: apt-get install virtualbox-3.0

Have fun!

---

### Post by Cametan on 2009-07-14
Oh, Sorry. I figured out what happened.

First, I set up python-programing environment on Emacs and I used pycomplete.py for that.
So I put pycomplete.py under /usr/lib/python2.5/site-packages. This caused the problem.
Aptitude's diff noticed unexpected pycomplete.py in the directory, and it warned python2.5-minimal package in the repository broken.
Actually I forgot the existance of pycomplete.py. So I didn't understand what happend in my Ubuntu then.

Be aware, to anyone who put utilities like pycomplete.py in some paticular directories handled by a deb-package.

Thanks.

---

