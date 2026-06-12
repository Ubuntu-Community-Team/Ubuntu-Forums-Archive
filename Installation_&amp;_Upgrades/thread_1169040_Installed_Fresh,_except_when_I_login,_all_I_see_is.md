---
title: "Installed Fresh, except when I login, all I see is the desktop and cursor."
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by blackbird3216 on 2009-05-24
I installed a fresh jaunty today, backed up all my files. then installed by following these [instructions]("http://ubuntuforums.org/showthread.php?t=1152381&page=2"). After installation. I loaded all my files back onto the computer, and formatted my flash drives. I also removed quite a few packages(which may have ruined functionality). When I restarted my computer, everything was fine, except that all I could see was a cursor and the default background. I don't understand what happened(does the package ubuntu-desktop have anything to do with this?). I tried getting my files back by loading the live cd, but they are copy protected. I am so stressed, and I don't know how to fix this problem. Please HELP! I don't want to reinstall.

---

### Post by blackbird3216 on 2009-05-24
could it be something with my display driver? How do I remove that?(preferably from livecd).

---

### Post by sailthesea on 2009-05-24
Try typing xstart at the command line if that brings your desktop back you should be able to restore ubuntu-desktop from Terminal  
If not its probably a goner and it would be easier to reinstall
 EDIT : by the way your link was broken

---

### Post by blackbird3216 on 2009-05-24
> **sailthesea said:**
> Try typing xstart at the command line if that brings your desktop back you should be able to restore ubuntu-desktop from Terminal  
If not its probably a goner and it would be easier to reinstall
 EDIT : by the way your link was broken
how would I restore ubuntu-desktop from the terminal?
Edit: Link Fixed.

---

### Post by sailthesea on 2009-05-24
Sorry Jaunty decided to have a "wireless episode" on me there
 If you got Terminal up then enter sudo apt-get install ubuntu-desktop 
If you get an error read it through as it normally gives the fix or post it so we can see what the problem is

---

### Post by blackbird3216 on 2009-05-24
> **sailthesea said:**
> Sorry Jaunty decided to have a "wireless episode" on me there
 If you got Terminal up then enter sudo apt-get install ubuntu-desktop 
If you get an error read it through as it normally gives the fix or post it so we can see what the problem is
Yay! I managed to do that in terminal w/networking and I got back. However, all the crapware came back as well. Is it safe to delete the following?
Tomboy
Ekiga
All the games
Evolution
Rythmnbox
Palm support
Bluetooth support
SCIM

And is it safe to reinstall my graphics card drivers(as they got uninstalled when I reinstalled ubuntu desktop)

---

### Post by sailthesea on 2009-05-24
I wouldn't get rid of Rhythmbox as I think this may take some vital stuff with it
 If your graphics card is working with the native drivers Its probably best to wait and see how things go as you try compiz etc ED:
 When you add/remove I found it best to just do a couple at a time then restart and check the boot up logs to avoid problems
 Finally Personally Unless you are really pressed for space I wouldn't remove any of those it won't make much difference;)
 ED: But it should be fine to install the drivers

---

### Post by blackbird3216 on 2009-05-27
> **sailthesea said:**
> I wouldn't get rid of Rhythmbox as I think this may take some vital stuff with it
 If your graphics card is working with the native drivers Its probably best to wait and see how things go as you try compiz etc ED:
 When you add/remove I found it best to just do a couple at a time then restart and check the boot up logs to avoid problems
 Finally Personally Unless you are really pressed for space I wouldn't remove any of those it won't make much difference;)
 ED: But it should be fine to install the drivers
I actually got rid of all of those, rebooted, and there were no problems. The thing I am really worried about are the NVIDIA drivers though. When I go to the Hardware Drivers preferences, it says that a "different version of this driver (ver 180) is being used. Please activate this one". I am worrired that doing so will give me another error, and I will lose all my precious data. How should I make sure that this driver will not cause another GNOME/X11 problem? Should I just click activate and install from there? Or should I follow these instructions(link below)? Should I backup so that I don't lose my data?

[http://ubuntuforums.org/showthread.php?t=1139101](http://ubuntuforums.org/showthread.php?t=1139101)

BTW, will this "non root bug" affect me in anyway?
[http://ubuntuforums.org/showpost.php?p=7201482&postcount=3](http://ubuntuforums.org/showpost.php?p=7201482&postcount=3)

---

