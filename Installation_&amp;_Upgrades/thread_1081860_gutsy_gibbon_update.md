---
title: "gutsy gibbon update"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by dawin45 on 2009-02-27
hi!
I did an update of my gutsy gibbon 2 the latest version so far so good,it finished updating started installing,and then restarteed the computer withouth asking 4 my permission,when I got in to login screnn,I posted my user an pass as ussual, and afther that is showed an emty orange screen? what shall i do,I don't want 2 lose my files...

---

### Post by cybergalvez on 2009-02-27
> **dawin45 said:**
> hi!
I did an update of my gutsy gibbon 2 the latest version so far so good,it finished updating started installing,and then restarteed the computer withouth asking 4 my permission,when I got in to login screnn,I posted my user an pass as ussual, and afther that is showed an emty orange screen? what shall i do,I don't want 2 lose my files...

My bet is its the video driver thats having issues.  if you want to make sure your files are still there do a ctrl-alt-F1 log in and you should still see all your files

I would try to reinstall your video drivers or reset your X config, I'm blanking on the command to do that search the forums for x.org config issues that should give you some clues

---

### Post by dawin45 on 2009-02-27
tryed all the tricks i could find,it didn't work I have 1-2 days till I get a new linux if you got any help 2 offer pelase do it :confused: me is :confused::( ...
will edit in a moment with what i tryed

sudo dpkg-reconfigure xrever-xorg
sudo ati config --force-- initial
ather alt+f2
sudo /etc/init.d/ gdm restart
 $ sudo apt-get remove --purge xorg-driver-fglrx
$ glxinfo |grep vendor
$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
sudo vim /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
$ glxinfo | grep vendor
$ glxinfo | grep "direct rendering"
$ LIBGL_DEBUG=verbose glxinfo
nothing worked me is having ati radeon 9250

---

### Post by dawin45 on 2009-02-28
bump

---

### Post by cybergalvez on 2009-02-28
> **dawin45 said:**
> tryed all the tricks i could find,it didn't work I have 1-2 days till I get a new linux if you got any help 2 offer pelase do it :confused: me is :confused::( ...
will edit in a moment with what i tryed

sudo dpkg-reconfigure xrever-xorg
sudo ati config --force-- initial
ather alt+f2
sudo /etc/init.d/ gdm restart
 $ sudo apt-get remove --purge xorg-driver-fglrx
$ glxinfo |grep vendor
$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
sudo vim /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
$ glxinfo | grep vendor
$ glxinfo | grep "direct rendering"
$ LIBGL_DEBUG=verbose glxinfo
nothing worked me is having ati radeon 9250

since it looks like you've got an ATI card and your on Hardy, give envyng a try,
sudo apt-get install envyng-gkt
from the command line you can try envyng -t and follow the prompts

---

### Post by dawin45 on 2009-03-01
it worked by sudo dpkg --configure -a
problem solved closing thread...:guitar:

---

