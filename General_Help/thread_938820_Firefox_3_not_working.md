---
title: "Firefox 3 not working"
date: 2008-10-05
forum: General Help
---

### Post by Tex786 on 2008-10-05
Hi,

Last night i noticed that all of my bookmarks were gone and that i could not restore any of my backed up files. I installed and uninstalled firefox 4 times last night thinking it may fix the problem but it did not work. 

I did the installs from the Synaptic.p.m. I think I need to start firefox 3 from scrach.

can someone give me a comand to get firefox back working again the way it should?

P.S. I am unable to bookmark anything

---

### Post by fooman on 2008-10-05
have you tried deleting your profile from the ~/.mozilla directory? ...then when you restart firefox,  it will create a new profile and hopefully fix your problem.

*FIRST backup your bookmarks file!

open your home directory.  in the toolbar, click view and put a tick in the box next to "show hidden files"

navigate to the .mozilla folder and open it.  then open the firefox folder.  you should see a folder with some random numbers/letters.default....like: "d65ja59c.default"

right click on that folder and choose "move to trash".  WARNING: this will delete* all* your firefox settings,  including your bookmarks, add-ons, extensions and themes that you have installed.  you will need to reinstall them after starting firefox again.

restart firefox and see how it goes.

---

### Post by PocketDog on 2008-10-05
Sometimes your profile is wrongly thought to be in use by Firefox, and it loads a fresh one. Not very helpful. Next time, in a terminal type ```
killall firefox
``` to make sure Firefox isn't running in the background. Then, ```
firefox -p
``` to force it to show the profile dialogue on startup. If you haven't set one up, choose 'default' and all your bookmarks and settings should be back.

---

### Post by Tex786 on 2008-10-05
> **fooman said:**
> have you tried deleting your profile from the ~/.mozilla directory? ...then when you restart firefox,  it will create a new profile and hopefully fix your problem.

*FIRST backup your bookmarks file!

open your home directory.  in the toolbar, click view and put a tick in the box next to "show hidden files"

navigate to the .mozilla folder and open it.  then open the firefox folder.  you should see a folder with some random numbers/letters.default....like: "d65ja59c.default"

right click on that folder and choose "move to trash".  WARNING: this will delete* all* your firefox settings,  including your bookmarks, add-ons, extensions and themes that you have installed.  you will need to reinstall them after starting firefox again.

restart firefox and see how it goes.

That sounds like a good idea but could you explain how i would get to the directory?

I am still pretty new. explain it in detail please.

thanks for the reply

---

### Post by fooman on 2008-10-05
> **Tex786 said:**
> That sounds like a good idea but could you explain how i would get to the directory?

I am still pretty new. explain it in detail please.

thanks for the reply

in your top panel,  go to places > home folder

when the directory opens,  look in the toolbar, click view and in the drop down menu, put a tick in the box next to "show hidden files"

find the .mozilla folder and click on it. then click on the firefox folder. in there, you should see a folder with some random numbers/letters.default....like: "d65ja59c.default"

right click on that folder and choose "move to trash". 

restart firefox.

---

### Post by SuperSonic4 on 2008-10-05
You can press alt+f2 and type /home/<username>/.mozilla to take you straight there

---

### Post by Tex786 on 2008-10-05
> **fooman said:**
> in your top panel,  go to places > home folder

when the directory opens,  look in the toolbar, click view and in the drop down menu, put a tick in the box next to "show hidden files"

find the .mozilla folder and click on it. then click on the firefox folder. in there, you should see a folder with some random numbers/letters.default....like: "d65ja59c.default"

right click on that folder and choose "move to trash". 

restart firefox.

Hey everything is back to normal :D

thanks a lot for the help!

---

