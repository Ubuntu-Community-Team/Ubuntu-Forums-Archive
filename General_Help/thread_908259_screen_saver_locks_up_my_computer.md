---
title: "screen saver locks up my computer"
date: 2008-09-02
forum: General Help
---

### Post by bentvalve3g on 2008-09-02
hi there, this is my first post, so sorry if i sound like a noob.  long story short my sister messed with the screen saver on here and now if you leave the computer for a minute the screen goes black, says constructing molecules...  and you can't get that screen off.  when i tried to change the screen saver settings, the computer locks up and won't respond to anything.  any ideas on how i could fix this?

---

### Post by Felipejane on 2008-12-18
I just encountered this same problem, and every time I would go into the Screensaver app to change it, it was already on Molecule and so would freeze my machine. I finally looked in the Help for Screensaver; in there is a command that you can issue in a terminal session that returns the path where the screensavers are stored. You navigate (still in the terminal) to that folder, ls to show all the files, and then: 
> sudo rm molecules
That deletes the file. The next time you open the Screensaver app, Molecules is no longer listed.

---

### Post by Chito on 2009-01-12
I think I know what your problem is but first. Which screensaver do you have it on? is it "molecule" by any chance. 

I had a problem with the same screensaver, it locks my computer completely, nothing works, the mouse moves, but can't click on nothing, and the keyboards locks too. and after so many tries and so many commands, there is a simple way to stop it. You might loose some screensaver and maybe some cool pictures that come with it, but is worth it. Follow the steps. 

I have Ubuntu 8.10 and it work for me, try it:

SYSTEM>ADMINISTRATION>SYNAPTIC PACKAGE MANAGER> "look for the search box and type"xscreensaver" then look for the xscreensaver files that are mark with a different color box, those are the packages you have, click on all the boxes you have in your system. A mssg box would appear "Click on "To be remove" and then press "APPLY" 

The package will be removed. and your problem will stop. 

You can reinstall it if you want to, by following the same steps.

Good Luck.

---

### Post by hivelocitydd on 2009-01-13
You can delete the screensaver by the following command

sudo rm -rf `locate -i screensavername`

---

