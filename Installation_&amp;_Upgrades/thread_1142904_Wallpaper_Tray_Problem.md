---
title: "Wallpaper_Tray Problem"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by EuphoniumFantasi on 2009-04-29
Today I installed the Wallpaper-Tray app and accidentally set it to .1 minutes.  I have tried apt-get --purge remove wallpaper-tray and it removes, but if I reinstall it it still changes the wallpaper starting flying by again. It goes so fast, that I can not right click into the context menu on the panel and change it. Does anyone have any ideas about what to do? I also tried moving all pof the pictures out of the directory.

---

### Post by zero7404 on 2009-04-29
do you still see a file in the /home/username/.config/autostart folder ?
maybe try to completely remove the package from synaptic, then run a sudo get-apt autoclean on your system, then reinstall it and try again....

---

### Post by EuphoniumFantasi on 2009-04-29
I tried both.  I do not have an autostart folder, and we did the autoclean after the purge remove and another install.  It's still not working.

---

### Post by zero7404 on 2009-04-29
there must be a left over config file or setting, i'm not sure but did you look in configuration editor ?

when i open it i see an entry called wp_tray, in there you will find the time setting you can change it there

---

### Post by zero7404 on 2009-04-29
i do have one question, i don't see how i can get wallpaper tray to use a directory on a mounted ntfs partition....

i like to keep my OS's on one physical disc, then docs/pics/music/etc. on another....

---

### Post by upchucky on 2009-04-29
if you did not set up a separate home partition for all your settings and files it can still be done. this ensures that in the unlikely event a new install is required everything is intact.


Separate Home Partiton

after ubuntu is already installed

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by zero7404 on 2009-04-29
i have a /home/ folder on my ext3 partition, with the necessary folders...but i am looking to avoid using them. reasons: in case something goes wrong with my installation, i can minimize losing all my personal files; i also use windows and in vista i have my personal folders linking to these locations and have my software there configured to look on the seperate partition.

i wish i could completely dump windows, but there are still some programs i need that only come to that platform, so while using both platforms, it's nice to have 1 copy of my personal files instead of more than 1.

---

### Post by EuphoniumFantasi on 2009-04-29
Thank you, this is sounding closer.  Where is the Configuration Editor?

---

### Post by zero7404 on 2009-04-30
> **EuphoniumFantasi said:**
> Thank you, this is sounding closer.  Where is the Configuration Editor?

you have to go to Applications-->System Tools. if it is not there, then click on Applications-->Add/Remove... and you can add it to the drop down from there.

---

### Post by emongev on 2009-05-24
thanks a lot this helped me as well =)

---

