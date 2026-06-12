---
title: "best way to transfer everything to new desktop"
date: 2011-12-16
forum: Hardware
---

### Post by virtdave@mcn.org on 2011-12-16
I've installed Ubuntu (currently 11.10) on a creaky old Dell Optiplex.  Several times a day, it spontaneously reboots, usually when doing graphics-intensive stuff (e.g., opening Stellarium is immediately a sure shutdown/reboot).  I've concluded that the problem is largely the puny hardware, and am looking for a new more serious OS-free system to replace the current one, on which I plan to install Ubuntu again.  Of course, I've installed a lot of stuff on the Dell, and would like to avoid going thru reinstalling the programs.  I do regularly back up with the Backup utility.  What's the easiest way to move everything on the current hardware to a new (and presumably more stable) desktop?

---

### Post by 2F4U on 2011-12-16
What do you mean by "everything"? Just your data or also applications you installed later on? Moving the data will be easy if you kept everything in your home folder. Moving applications is difficult and I would not recommend doing it.

---

### Post by virtdave@mcn.org on 2011-12-16
I would like to avoid having to re-install all of the programs I currently have in my system  since some of them (like TrueCrypt) were a bit tricky to get running...I understand that I can (I think) get all my files, emails, etc., from the Backup utility on a fresh install, but from what you say, a tedious re-installation of the apps/programs might be necessary. Perhaps (since I do believe the problem might be in the graphics card on my current system) I might try  just replacing that, to see if it solves the pesky crash/reboot issue?

---

### Post by jerome1232 on 2011-12-16
Use imaging software like clonezilla? That is assuming the new drive is as big or bigger than the current.

You would have to expand your partitions to fill up the new drive after, but you should get an intact duplicate of your old system that way.

You may have to temporarily plug the new drive into your old computer to do this.

edit: It may be a good idea to remove your video driver if you have a different brand of video card on the new computer.

---

### Post by BC59 on 2011-12-16
Try to do it with Remastersys but there is a problem. The project was abandoned for some years so there was no support up to now. 

There is a way to install it through PPA but the version installed is old of Karmic era.

The new developer created a Remastersys 3.0 beta which is here

[http://www.remastersys.com/repository/ubuntu-testing/](http://www.remastersys.com/repository/ubuntu-testing/)

A good guide on how to do it is here:

[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys) (a little out of date)

Then install the .iso on a USB to check it.

Try to do the same with Clonezilla. Is a little more complicated because you need to install Clonezilla to a USB or CD and then to perform the backup of the system.

Follow the instructions from here:

[http://geekyprojects.com/cloning/how...illa-tutorial/](http://geekyprojects.com/cloning/how...illa-tutorial/)

and of course from the official website:

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Maintech on 2011-12-16
> **virtdave@mcn.org said:**
> I've installed Ubuntu (currently 11.10) on a creaky old Dell Optiplex.  Several times a day, it spontaneously reboots, usually when doing graphics-intensive stuff (e.g., opening Stellarium is immediately a sure shutdown/reboot).  I've concluded that the problem is largely the puny hardware, and am looking for a new more serious OS-free system to replace the current one, on which I plan to install Ubuntu again.  Of course, I've installed a lot of stuff on the Dell, and would like to avoid going thru reinstalling the programs.  I do regularly back up with the Backup utility.  What's the easiest way to move everything on the current hardware to a new (and presumably more stable) desktop?

Have you thought of installing Lubuntu? It is still ubuntu but made for older computers and low resource computers. You could install it and leave your /home directory alone. Then follow the directions of the others to move your files when you get a better system.

---

### Post by virtdave@mcn.org on 2011-12-16
Thanks for all the suggestions--I meanwhile did some research on the replace-the-graphics-card option, and on my Dell (Optiplex GX520 Small Form Factor) it looks like the power supply (220W) might not be adequate for a more robust graphics card, so I'll look into some of the options folks above have kindly provided.

---

