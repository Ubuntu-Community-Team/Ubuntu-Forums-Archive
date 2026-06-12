---
title: "Migrating Ubuntu to New PC"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by flyingsolo on 2009-05-25
I have a very old Dell that has run Ubuntu for a long time but is starting to have failures & has a rather slow processor by today's standards.  But I have another newer Dell box that I'd like to move to but would like to essentially duplicate the programs, files, preferences etc to the new machine. ('Copy' the installation basically)  How is this best done?
(NB:  I have an external drive for backup that may be of use perhaps)
Thanks b/c I haven't found this discussion on old posts--point me to another post if it seems to suit.

---

### Post by Therion on 2009-05-25
That's going to be dicey since you're talking about two entirely different hardware profiles on the two machines.  I suppose you could try using PartImage or Rsynch or QuickStart to do the backups, or image the drive, but I'd strongly suggest you simply suck it up and do a fresh install.  

I'm not saying what you want to do *can't* be done, I'm just saying it's probably best to do a clean install.

---

### Post by kimda on 2009-05-25
I would make a backup of your and other users home dirs. This basically contains your program settings besides all the stuff you store. 
So you should copy that to your external harddrive. Also make a backup the /etc directory it has more general settings. Like the xorg settings. I would basicly do a new install and not a clone since your new PC will be completely different than your old one.  

Make a dump of all installed packages on your old machine like this (in terminal): 
dpkg --get-selections >  packages.txt   

save this also to your external drive

then on your newly installed pc execute the following commands:
sudo dpkg --set-selections < packages.txt
sudo apt-get dselect-upgrade

This basically reads the old packages and reinstalls all the same packages you had on your old pc. 
Now you can copy your old home dir in place of the new one. Then it should read all the old settings.

---

### Post by flyingsolo on 2009-05-25
Thanks to both above--the cautious & the adventuresome!  I hope to try the second method above realizing there are risks but I will still have the original Dell box intact.  It has been backed up to external drive with rsync and I was hoping the new Dell could import /home and more from the external drive backup.
Please advise if you forsee difficulties with this strategy.
thanks.

---

### Post by kimda on 2009-05-26
If you backup your data and restore it properly by copying your home dir to the new machine. Make sure the hidden files are also copied! Check with nautilus with Ctrl-H to show hidden files. 

Also I would use the same Ubuntu version like on the old machine. And upgrade afterward if applicable. If you use evolution you could also make a backup with the program itself. Good luck!

---

### Post by edgeeffect on 2009-06-24
I'm really confused by what people are saying on this and other forums on this subject.

We have 3 systems in our house/office that I like to keep as near-identical configurations. In the past I've simply "cloned" the installation from 1 machine to the other 2, and then tweaked a few files in /etc (hostname, fstab, etc).

I've done this with SuSE, Slackware, and Debian - and it's worked fine for me. Today, trying the same procedure with Ubuntu and booting throws heaps of error messages at me.

---

