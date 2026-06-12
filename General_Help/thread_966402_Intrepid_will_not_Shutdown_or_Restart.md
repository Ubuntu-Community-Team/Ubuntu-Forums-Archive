---
title: "Intrepid will not Shutdown or Restart"
date: 2008-11-01
forum: General Help
---

### Post by dj1203 on 2008-11-01
I recently did a clean install of the Intrepid RC and now my computer fails to restart or shutdown. Instead of seeing the traditional Ubuntu shutdown bar, it just goes to a blank screen without showing anything or making any sounds. It will remain on with a blank screen and will hang indefinitely (i have let it sit there for about 7 hours). I have tried using sudo halt and sudo shutdown -H now. Both gave the same results. I have attached a portion of the syslog file where i think the culprit can be found. any help would be greatly appreciated

---

### Post by dj1203 on 2008-11-01
To add to this, if i do not log in when i start the computer, and shutdown from the login screen then the computer will shutdown correctly.

---

### Post by fouadk on 2008-11-01
same problem here....i have not tried the scenario of not logging in and tring if it restarts or shutsowns normally or not but if i install the nvidia drivers, instead of a black screen i get i a white screen with black dots scattered all arouns...

8.04 didn't have this problem...

8.10 is great and have many exciting features and most of all is detects my broadcom by default... i wonder why things that used to work doesnt anymore :$

please help

thanks in advance

---

### Post by dj1203 on 2008-11-01
It appears that the usplash screen causes the problems here. If i disable usplash then it will restart and shutdown correctly, however i would like to have the usplash screen if possible, anyone know a good fix? As it indicates in my attached log files the usplash is "tainted"


to disable usplash remove the splash option from menu.lst

---

### Post by dj1203 on 2008-11-01
Now that it does shutdown however, the computer will not show any bios information on startup or grub menu... it displays a black screen till the Ubuntu login window..... which is not the way it should be.... any help as to why it would cause this behavior?

---

### Post by Rodney9 on 2008-11-01
I am also having this same shutdown problem on a new 8.10 64bit install on a new pc. Hopefully a fix soon.

---

### Post by dj1203 on 2008-11-03
Does anyone know what could cause ubuntu to be able to shutdown the system and prevent bios and grub menu from displaying at next boot? The only way to get the computer to display this information again is to physically unplug the computer or switch the power supply off and on.

---

### Post by Potatoman on 2008-11-03
Same thing here. On shutdown it hangs with a blinking cursor in the corner of the screen. For some reason clicking shutdown is causing the PC speaker to beep as well.

---

### Post by Joe on 2008-11-03
[http://ubuntuforums.org/showthread.php?t=964177&highlight=intrepid+shutdown](http://ubuntuforums.org/showthread.php?t=964177&highlight=intrepid+shutdown)

---

