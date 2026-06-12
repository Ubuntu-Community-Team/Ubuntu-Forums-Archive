---
title: "AMD 64 - 3x 9800GTX Nvidia cards - overheat - crash comp?"
date: 2008-08-27
forum: Hardware
---

### Post by Onyxblack on 2008-08-27
Ok, well first off, I am running 3840x1024 with 3 19" LCD and 3x 9800GTX EVGA nvidia cards in tri-SLI, using matrox TH2G

It seems that the video cards are to new for ubuntu (seen in [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=889467](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=889467) ), and I downloaded the drivers from the nvidia site 
( [http://www.nvidia.com/object/linux_display_amd64_173.14.12.html](http://www.nvidia.com/object/linux_display_amd64_173.14.12.html) ) 

after downloading I had to stop x-server 

ctrl+alt + f2

did 

sudo /etc/init.d/gdm stop (stop x-server)

did

sudo sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run

installed and compiled or whatever 

did a restart got back to ubuntu but was unable to change resolution and kept having the problem of what i believe to be the video cards overheating (I don't think the drivers installed correctly or they arn't regulating the built in fans on the 9800GTX cards.) Causing my screen to go blank and forceing me to do a hard shutdown... so now... here i sit typing this in windows :(

---

### Post by sdennie on 2008-08-27
If you've manually installed the drivers, try running "nvidia-settings" from the terminal.  That should bring up a GUI that allows you to monitor the temperature of the cards.  I've never run an nvidia SLI configuration but, you may also want to ask at [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14) as there are many knowledgeable people there that may be able to advise you on possible caveats.

---

### Post by Onyxblack on 2008-08-27
Cool, I'll give it a try when I get home. 

Thank you!

---

### Post by tuxxy on 2008-08-27
woah nice setup! if only it worked, its a long shot but did you try envy to install the drivers first?

Also some pics would be good once its all working :)

---

### Post by Onyxblack on 2008-08-27
Im not familiar with envy - but ill give it a look-see when i get home... work kinda stinks today lol - any case here are some pics when i was building 'er, had to swap out the power supply mid build (not enough juice when i swaped the cards out) also have a different keyboard mouse and one of my old screens in the last pic (also thats when i was running xp 64, now im on vista 64) - 3 months old and still top of the line - not many can say that lol ;) 

Images
[http://titansites.com/beast/](http://titansites.com/beast/)

---

### Post by Onyxblack on 2008-08-27
Update - Ok it seems that my comp doesn't start with the nvidia driver enabled? so far every time ive restarted ive had to run 'sudo nvidia-xconfig' and even then I cant seem to get my resolution 3840x1024... (option isn't avaliable) and cant seem to edit the xorg.config with out having the nvidia driver stoping and me being left having to start all over again...

EDIT: HAH! just got it - but now im afraid to restart... lol

 - screen shot for proof!

[http://titansites.com/Screenshot-1.png](http://titansites.com/Screenshot-1.png)

Edit again -

Ok seems i got it starting with the nvidia driver now - needed to

> sudo nano /etc/default/linux-restricted-modules-common

Edit the DISABLED_MODULES line to make it look like this:-
Code:

DISABLED_MODULES="nv nvidia_new"

only 1 problem left with the display (login screen isn't showing the box's/ - resolution for login screen is only 1 moniter and the username/pass box's are off the screen/ i login blind! lol)- everything else is working like a charm.

---

