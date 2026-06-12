---
title: "Wine fonts trouble"
date: 2008-11-27
forum: General Help
---

### Post by runneri.q on 2008-11-27
I have just installed wine on my intrepid ibex computer, then i tried to install fulltiltpoker.exe on wine. it installed properly and i was able to play it. however, after i installed compiz fusion, my fonts in wine went missing. I then tried repeatedly to reinstall wine and start it from scratch. however, the problem stayed.
Now i am wondering how to reset wine completely like i had it originally or how to fix the fonts

any help would be greatly appreciated...
      Runneri.q

---

### Post by happyhamster on 2008-11-27
- To reset wine, get rid of the hidden .wine folder in your home directory. That folder is where all the windows stuff is installed, and also contains wine's registry. 
(Press ctrl-h in nautilus to be able to see hidden files, then just delete the folder or rename it. The folder will be created afresh next time you run wine.)

- Try running wine with compiz disabled.

- Also, a lot of wine's font troubles are solved by installing the msttcorefonts:

sudo apt-get install msttcorefonts

- If that didn't help, there are a few more fonts that can be installed using the winetricks script. Go here for more info and instructions:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

Good luck, and keep us informed.

---

### Post by SeaJayEmm on 2008-12-16
I to play online poker, tried paradise poker in wine with no sucess (wouldn't load table) so I installed a VirutalBox OSE running winxp. I now use that to run all of my windows applications. If you don't know how to install and use VirtualBox OSE go to Google and do a search. You can figure it out from there.

---

### Post by SeaJayEmm on 2008-12-16
I just uninstalled Wine and related packages. I seen something that could be the possible solution and is worth checking out. /usr/share/fonts/truetype/ttf-liberation...look into that and you might find a solution

---

### Post by stryknyner on 2010-04-05
i installed wine then installed fulltiltpoker but everytime i try to start it it will act like its starting then stop what am I doing wrong? I did not configure wine cause I have no idea what that means or how to do it can someone help me with this?

---

### Post by lisati on 2010-04-05
Necrophilia. Old thread closed.

p.s. It's ok to start a new thread (discussion) for each of your questions. Go to [http://ubuntuforums.org/](http://ubuntuforums.org/) and pick a category, then click on the "new thread" button

---

