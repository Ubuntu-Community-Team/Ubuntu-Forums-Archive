---
title: "Webcam box on desktop"
date: 2008-08-22
forum: General Help
---

### Post by Powerkid89 on 2008-08-22
Hi everyone
i'd like to have a small box the shows my webcam feed
somehting maybe like the windows toolbar style where i can just have the box anywhere on the desktop
is this request possible?


*Linux Noob*

---

### Post by easybake on 2008-08-22
> **Powerkid89 said:**
> Hi everyone
i'd like to have a small box the shows my webcam feed
somehting maybe like the windows toolbar style where i can just have the box anywhere on the desktop
is this request possible?


*Linux Noob*

There are a couple ways you can do this. I wrote a tutorial on how to add your webcam feed as your wallpaper [Check Here]("http://ubuntuforums.org/showthread.php?t=883176")

Also if you just wanted it to be a normal window, it's fairly basic. Just do this:
Open Up Terminal.
Install Mplayer```
sudo apt-get install mplayer
```
In terminal type paste ```
mplayer -quiet -fps 15 tv://
```
------------------------------------------------------------------------------

You might want to create a launcher for this so you don't have to have an open terminal window running all the time. 

Right click on a Panel. Click + Add to Panel. Click Custom Application Launcher. For name put ```
Webcam
```. Under Command put ```
mplayer -quiet -fps 15 tv://
```

REEDIT: Only one application can use the webcam at a time. So before you start using Skype or something be sure to close it first.

---

### Post by Powerkid89 on 2008-08-22
thanks man

---

### Post by Powerkid89 on 2008-08-22
any way i can have it open smaller?
i keep needing to resize it

---

