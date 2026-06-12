---
title: "xfce 4.6.0 Jaunty desktop bugger out."
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by dLeon on 2009-04-28
What happen to Xfce
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
After clean upgrade to xubuntu I find xfdesktop --reload doesn't work as it use to be in intrepid. This command originally will refresh your xfce desktop & image list so we get random wallpaper. Usefull for wallpaper changer script.

In intrepid Desktop wallpaper mode 'auto' automatically tiled the imaged if it 3/2 of the screen size. In Jaunty it will over scalled everything beyond the screen size.

Also using image list with more than 5000 image listed will hog system resources. In intrepid I can listed around more than 40000 image, xfce happily except it.

Trying to play with xfdesktop command will eventualy kill xfdesktop daemon. Keep playing with it, then start menu applet will killed followed with xfpanel.

Sorry, that's long... I also found some other drawbacks in Xubuntu Jaunty, but either it already posted or I will post it in another threads.

---

### Post by bl00d666 on 2009-04-29
I have the same problem here with my jaunty after the upgrade from intrepid. i usually use xfdesktop --reload with cron to choose a new wallpaper at random and it doesn't work anymore. i have to do a xfdesktop --quit and an xfdesktop to get the same result except that now it usually stop working and i have to refresh it manually. 

the image list is really eating all system resources. i find it really weird because it came from people who are suppose to make a system more fast and more light on ressource.

 i hope the next update from xfdesktop correct the xfdesktop --reload problem

---

