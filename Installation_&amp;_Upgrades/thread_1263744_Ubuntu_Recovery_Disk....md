---
title: "Ubuntu Recovery Disk...???"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by randolf_ambrose on 2009-09-11
after getting so irritated by windows, i finally moved to Jaunty Jackalope!!!

i had complete transformation of all my apps...

just got one problem.......

IS THERE ANY WAY TO CREATE A RECOVERY DISK OF MY UBUNTU... ???

---

### Post by ahbart on 2009-09-11
I'm not sure about a recovery disk option, but you could make an image of the root partition. If anything is going bad, you couldoverwrite the root partition with the image. 
Beware this is only possible of you have a good backup of your personal files, or if you have a second partition or disk mounted at /home. 

Clonezilla is good option to make an image.

---

### Post by presence1960 on 2009-09-11
I would recommend you get a sensible backup/imaging plan in place and use it regularly. 

I use rsync to do a backup of my home directory and my data directory every weekend. If you don't like the command line you can use grsync instead for a GUI rsync. 

I also have images of my OSs. You can use clonezilla, PING or partimage. This way if anything happens to your OS you can restore the image to it's partition. If anything happens to your home or data directories you have a backup.

Anyone who uses a computer should have a plan in place to backup and /or image their data. If you do not what will you do if the unexpected happens?

---

### Post by randolf_ambrose on 2009-09-11
The main reason why i wanted a Recovery Disk is because it saves the time in installing all hardware apps and other apps, my desktop, themes, all other settings.......

creating an image of root works??? does it??? is it possible to replace root like that???

---

### Post by StuartN on 2009-09-11
And it is also possible to save a list of all the installed packages, for instance in Synaptic use File->Save markings as. This is a small text file that will re-install any missing applications or packages if you ever need to re-install Linux. Combined with a backup of your /home directory it is much, much smaller than backup up /.

---

### Post by solitaire on 2009-09-11
also take a look at "Remastersys" in the repo's
it will make a backup image of your install. it will even burn your install into a "LiveCD" if you want to take it with you on other machines ;)
I use it to make a backup image from time to time when i get everything the way i like it.

---

