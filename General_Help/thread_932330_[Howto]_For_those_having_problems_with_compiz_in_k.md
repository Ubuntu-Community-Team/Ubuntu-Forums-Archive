---
title: "[Howto] For those having problems with compiz in kde"
date: 2008-09-28
forum: General Help
---

### Post by snowangyl on 2008-09-28
how to enable compiz in kde

Its a pretty simple process.
Make sure that all the proper drivers and compiz is installed before starting

Just type these commands
sudo apt-get install fusion-icon compizconfig-settings-manager

then go to the menu -> system 
open compiz fusion icon
youll see an icon show up in your tray
right click on it and select settings manager
then you can select all of the options you want
the first time you set the options there, it won't work
close the settings window 
the right click on the icon and select reload window manager

**NOTE 
you must keep the icon running if you want to have compiz effects. WHen you close the icon, the effects stop working

Hope this helps

---

### Post by snowangyl on 2008-09-28
to startup the icon automatically, look at 
[http://itg.chem.indiana.edu/inc/wiki/software/168.html](http://itg.chem.indiana.edu/inc/wiki/software/168.html)

It should be linked to 
/bin/fusion-icon --no-start

---

