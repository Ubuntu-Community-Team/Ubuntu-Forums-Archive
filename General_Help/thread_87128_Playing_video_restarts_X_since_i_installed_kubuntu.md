---
title: "Playing video restarts X since i installed kubuntu desktop"
date: 2005-11-07
forum: General Help
---

### Post by kitsos on 2005-11-07
I have an ATI mobility x600 card using the fglrx driver and ubuntu and everything was running perfectly...until i installed kubuntu desktop on top with apt-get. Now whenever i start Xine, X server restarts. Same happens for Totem and Kaffeine (when i try to open/play a video file), regardless of which environment i use (gnome or KDE). 

For Kaffeine/KDE i found that switching from preferences to gstreamer engine and then back to Xine solves the problem...but i have to do that every time i restart kaffeine + if i try to open another file kaffeine shuts down...so it is not a solution really. 

I cannot understand what caused Totem and Xine to break...they were working perfectly in gnome.:confused: 

Can't really see the output of Xorg.0.log since the X server restarts and it is overwritten. However dmesg reveals a Kaffeine segmentation fault.

Any ideas???

---

### Post by PuleX on 2005-11-07
Do check out this page: 
[http://xinehq.de/index.php/faq#XFREECRASH](http://xinehq.de/index.php/faq#XFREECRASH) 

It helped me figure out why xine, totem and vlc crashed when I started playing a video (allthough I haven't found a real solution ;-) ).

---

### Post by kitsos on 2005-11-07
Hi Pulex,
thanks for your reply. It does seem to be an XV extention problem. Also found your thread at [http://www.ubuntuforums.org/showthread.php?t=86016]("http://www.ubuntuforums.org/showthread.php?t=86016")
and i have exactly the same issue here. If i disable the support for the 2nd monitor in xorg.conf/or connect it everything runs normally. 
It is still weird though as i didn't have this problem before installing kubuntu-desktop.

---

