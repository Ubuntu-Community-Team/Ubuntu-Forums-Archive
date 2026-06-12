---
title: "GUI Help!"
date: 2008-08-04
forum: General Help
---

### Post by rbolio on 2008-08-04
Hi! Heres mi problem:

I was browsing around the tips and tricks area and i found a post called "Faster and smoother Ubuntu" or something like that [heres the link btw.  [http://ubuntuforums.org/showthread.php?t=856485](http://ubuntuforums.org/showthread.php?t=856485) ]

Now none of the bars work! by bars y mean the top bar (applications, places, systems, quickstarts...etc etc.) bottom bar (cant see which programs are active nor running, which one is active....) and side one (wont show up!) 

Please help me!

---

### Post by tamoneya on 2008-08-04
hit alt-F2 and type:```
gnome-panel
```
If that doesnt work hit ctrl-alt-F1 to go to tty1 and type:```
sudo dpkg-reconfigure ubuntu-desktop
sudo /etc/init.d/gdm restart
```
Then hit ctrl-alt-F7 to return to your desktop.

---

### Post by rbolio on 2008-08-04
wow thanks for the quick reply! that worked just fine!. 

THANKS!

---

