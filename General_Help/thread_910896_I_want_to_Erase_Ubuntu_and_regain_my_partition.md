---
title: "I want to Erase Ubuntu and regain my partition"
date: 2008-09-05
forum: General Help
---

### Post by sendblink23 on 2008-09-05
Well I have a HP Media Center PC m7060n, naturally Windows XP ....  currently Dual Boot having Ubuntu 8.04 LTS

Well I want to Erase my Ubuntu and Regain my Partition for Windows, and Erasing the whole computer and Restoring to a Clean Windows back to original. 

This HP has an internal *Restore Hard Drive Partition...  Can anybody help me out.. how to get get rid of Ubuntu and Regaining the Partition(from Ubuntu) for XP... 

Completely Restoring back clean on Windows XP .. so take in mind its an internal *Restore Partition Inside the HP  :P  i tried to search around the Forum.. but well noticing my Computer has the Internal partition(Restore)   .. well its a Different Case, than the others I've read around

---

### Post by winbutu on 2008-09-05
Dont uninstall ubuntu, easy decision.
Uninstall windows. much easier.

---

### Post by sendblink23 on 2008-09-05
> **winbutu said:**
> Dont uninstall ubuntu, easy decision.
Uninstall windows. much easier.

I need to use Windows I'm a Graphic Designer and I'm always using CS3  which is not compatible on Ubuntu  understand

before stating something...  When Replying... just Stay on whats on the Subject.. question.. If a user wants to go back to windows.. well thats all he wants  ... as Like i am at

---

### Post by ad_267 on 2008-09-05
You can use gparted (by booting from the Ubuntu live CD) to delete the Ubuntu partition and then resize your Windows partition. You can then use a windows disc to fix the windows boot loader. I think you just select "repair" from the boot menu. I don't think the "restore hard drive" partition should be an issue with this.

If you want to wipe the whole hard drive and start again then you can delete all partitions with gparted and use the windows install cd to install windows on the empty hard drive.

---

### Post by Xgen on 2008-09-05
Try this:
[http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php")

Edit: Ayyyye..not fast enough...

---

### Post by abhishek.malhotra35 on 2008-09-05
You can use the internal HP Restore program which will restore your windows to original factory settings. Or you can reinstall windows and while reinstalling, you can delete the Ubuntu partitions manually.

---

### Post by jerome1232 on 2008-09-05
> **ad_267 said:**
> You can use gparted (by booting from the Ubuntu live CD) to delete the Ubuntu partition and then resize your Windows partition. You can then use a windows disc to fix the windows boot loader. I think you just select "repair" from the boot menu. I don't think the "restore hard drive" partition should be an issue with this.

This would be the best method if hp was actually nice enough to give you an OS cd. You shouldn't lose any data (when messing with partitions it is best to backup first though just in case something goes horribly wrong)

---

### Post by densant on 2008-09-05
Try this, i had to the same thing and it help me

[http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)

---

### Post by bigbrovar on 2008-09-05
(1) Go here and download gparted for free [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) , its a partition manager or ask someone for a partition manager or any partition manager you can get your hand on will do.

(2) I assume you want to get rid of ubuntu totally, so the first thing you do is stick in your windows cd and boot from the cd.

(3) When the cd is fully started, you should at some point get a prompt to press R for recovery, do this.

(4) Choose your disk drive, stick in your administrator password (Just press enter if you have no administrator password)

(5) Then type in the command fixmbr

(6) It will let you know know its done by saying something like new master boot loader written blah blah blah and maybe also ask you something like are you sure you want to write a new blah blah blah.

(7) When you are done, you should notice that the grub bootloader is gone and your computer boots straight into windows xp. The reason you have to do this all is because if you delete your ubuntu partition immediately, the grub bootloader will still be there and notice, that one of its booting components or whatever is gone and will give you an error 22 message and you won't be able to boot into windows xp (this can be fixed with the fixmbr command).

(Cool Then after using the fixmbr command, stick in the gparted or respective partition manager, use partition manager to delete the ubuntu partition, and tada ubuntu is gone and windows xp present.

Now these instructions assume that you have only 2 Operating systems installed, mainly ubuntu and windows. If you don't, I assume you can edit the grub bootloader so it doesn't go into error state. I don't know how to do it because I have just deleted ubuntu for like the tenth time on my computer because I can't use it proprly, but these are sources that should help with queries.

---

### Post by bigbrovar on 2008-09-05
to regain ur the partition used by ubuntu .. boot windows then go into Disk Management - right-click My Computer, Manage, Disk Management. there you should see the ubuntu partition which u deleted .. it should be called unallocated partition ...  right click on an existing partition and choose expand .. it should expand to the former partition u used for ubuntu

---

### Post by dodle on 2008-09-05
Edit:  I am putting this at the top because I think you might want to try it first, much simpler.  
If you can boot into Windows, download this tool: [MbrFix]("http://www.download.com/MbrFix/3000-2094_4-10485990.html").  Extract it to whichever directory you want, then open a cmd window and navigate to that directory.  Input: ```
mbrfix /drive 0 fixmbr
``` Then it will ask you to confirm.  You will now have your Windows mbr back.  As far as booting into the recovery partition, you'll have to go through the "F" keys during bootup until you figure out which one gets you there (you may be able to do this with Grub as well).

(original post)
Can you boot into Windows?  It sounds like you are trying to wipe everything and make a clean Windows install, am I wrong?  I had to reinstall Windows on my sister's machine which was taken over by viruses.  Her machine was a Compaq and didn't come with a Windows CD, so I browsed around trying to find a way to create a legal installation CD for her and found this:  [http://www.howtohaven.com/system/createwindowssetupdisk.shtml]("http://www.howtohaven.com/system/createwindowssetupdisk.shtml").  This method worked perfectly for me.  If you can access the i386 folder from Windows (or Ubuntu) you should be able to make yourself a CD.  Personally, I like having the system CD better than a restore partition, because if your mbr gets messed up you can still book into the CD.

---

