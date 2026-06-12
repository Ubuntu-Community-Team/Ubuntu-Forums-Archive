---
title: "I've pretty much nuked my system python"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by phatlikebuddha on 2009-04-19
A few months ago, I was young and brash and overwrote the distributions python (lived in /usr/bin/python - was version 2.5) with python2.6 from a source build.

This caused all sorts of problems with system software that expected python 2.5; so I tried to reinstall via Synaptic/apt-get but it got nowhere.

So I built a python2.5 from source and overwrote it to the /usr/bin/python. For the past few months I've been able to live with this; until now. The main problem is that the gtk module blows up in python2.5 so anything uses pygtk causes a problem.

Is there any sane way to restore the system python via synaptic/apt-get/dpkg?

I've tried removing the python I compiled to solve. I used dpkg --purge python to remove that package and dpkg -i with a .deb from packages.ubuntu.com and this didn't work either.

I've tried compiling the PyGTK module on my own but I get errors during ./configure around GLIB.

I run 8.10 and was thinking of upgrading to 9.04 to remedy this (as jaunty runs python2.6) but the update app required PyGTK :(.

Anyone got any help for me?

---

### Post by Bakon Jarser on 2009-04-19
You can do a distribution upgrade from the terminal.

> sudo apt-get dist-upgrade

---

### Post by phatlikebuddha on 2009-05-02
That command doesn't update your distro.

You need to use

```
sudo do-release-upgrade
```

Which still won't work for me. I get the following error:

```
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool 
Done downloading            
extracting 'jaunty.tar.gz'
authenticate 'jaunty.tar.gz' against 'jaunty.tar.gz.gpg' 

Reading cache

Checking package manager

Can not upgrade 

Your python install is corrupted. Please fix the '/usr/bin/python' 
symlink. 

```

Any help on how to fix the /usr/bin/python ?

---

### Post by pdah on 2009-09-21
I don't know if you had fixed this problem or not. Just want to put my solution here to help any googlers around.

The 'distribution upgrade' command need /usr/bin/python to be a symlink with 777 permission. I think you had made changes on this symlink. 
I had the same issue on my Ubuntu 9.04 and this is what I've done so far
```

$ sudo rm /usr/bin/python
$ sudo ln -s /usr/bin/python2.6 /usr/bin/python

```
Change python2.6 to the right version on your Ubuntu.

---

### Post by maxpulse on 2013-02-06
make sure
/usr/share/python/debian_defaults matches the version /usr/bin/pthon sym link

---

### Post by wildmanne39 on 2013-02-06
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

