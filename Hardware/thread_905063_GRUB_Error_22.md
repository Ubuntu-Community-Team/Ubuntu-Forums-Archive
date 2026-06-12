---
title: "GRUB Error 22"
date: 2008-08-29
forum: Hardware
---

### Post by sjmiller85 on 2008-08-29
I've done quite a bit of extensive digging on resolutions, none of which are possible considering the circumstances I have.  I currently have a laptop that would make a fantastic dedicated server, but not much of anything else.  Keyboard is shot, battery is shot, headphone jack is screwed up, one of the fans underneath accidentally came disconnected during a cleaning, and best of all, the disk drive is 100% inoperable.  I cannot even open the tray to pull out the disk that is currently in it.  Not much to worry about I guess, I'll figure out a way eventually.

Best part about all of this is, my Kubuntu is (as far as my patience is concerned) beyond repair and a fresh install is necessary.  Yet I cannot install via the CD route due to an inoperable disk drive.  I've searched alternate methods for installation, and nothing has come up that would result in me maintaining my non-grayed hair.  It clicked that since the laptop hard drive is a SATA, I could EASILY pop it out of the laptop, and plug it into my desktop to do the installation.  Cake!  So I crack open the side of my desktop, never having to do this before, and I plug in the power and the SATA cable.  Easy enough I guess, and I successfully install a copy of Kubuntu linux!  Woohoo!!  I'm all excited at this point, and so I take it out of the desktop and put it back into the laptop thinking I may have just easily resolved my problem!!  That is of course, until I boot up and I am greeted with a:
```
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 22
```
Now I'm at a lost.  All of the google'ing I did brought back resolutions, using the LiveCD.  I sure wish I could use a disk drive to do it though, as I am assuming that this cannot be done on a separate computer?  Can I safely assume that I cannot fix the GRUB on my laptop by attempting a repair while the hard drive is plugged into my desktop?  I'm getting to the uncomfortable state where I don't want to start guessing these things, vice bringing down another computer in my house!  Anyone have any resolutions for how to handle this error WITHOUT using the broken disk drive on the laptop?

---

### Post by nicedude on 2008-08-30
While this could probably be fixed via your desktop I have no idea how with the present information to tell you for sure. Most likely this error could be due to when you loaded kubuntu on the laptop drive it assigned it thought of it as a certain device and then when you put it back into laptop it is no longer that drive address and therefore grub can't load. 

For starters when you pluged it up to another computer and did the install was the laptops drive the only drive connected to that PC at that time or were others still connected? If your other disks were still connected you might try doing it again with only it connected to the PC in question so it would for sure be dev sda and grub would reference (hd0,0) as the MBR it is using.

---

### Post by sjmiller85 on 2008-08-30
Oh!  Doh, I completely forgot.  When I installed Kubuntu, I still left a very small partition of this hard drive to Windows (about 10GB if I remember correctly).  Am I to assume that it produces this error because I completely reformatted the hard drive to contain nothing but Kubuntu?

I could re-install Windows as a partition, yet I cannot remember what the partition structure was as far as names and such, and I'm afraid I'd waist hours of my time trying to get it back on only to realize that I need exact replication with partition names.  How strict is GRUB as far as partitioning hard drives with regards to partition names and such?

---

### Post by nicedude on 2008-08-30
Grub works like this, First thing on your hard drive is called the MBR or master boot record now the MBR of a disk is too small to contain all of grubs files and info it needs so it uses a trick. It puts the first bit of info it needs in the MBR and the rest on your Linux partition in a directory called /boot/grub the file called menu.lst contained in that folder has the actual settings that grub uses to load up all operating systems installed. If for any reason the menu.lst due to being moved between PC's is trying to load from MBR the rest of its code from a disk partition that is no longer correct in its assignment then it will fail. Deleting a windows partition from the drive after the Kubuntu  install should not cause this though as lets say windows was the first partition and Kubuntu was the second then by deleting windows the Kubuntu partition should still have the same partition assignment. But if you put the laptop drive say in a desktop and you also had a hard disk in that desktop that say is drive one to the BIOS and the laptop is drive two then when you move it to the laptop I believe that it would then be called sda ( first drive sda sdb sdc etc and each drive will have partitions like sda1 sda2 etc ) instead of sdb ( 2nd drive ) like it was when you used your desktop to install Kubuntu ( this is assuming there were one or more hard disks in your desktop when you plugged in the laptop drive and installed Kubuntu on it ) and now that it is seen as sda then grub would be looking for a sdb disk partition and therefore cant find it. This is not 100% that this is what you did but I just see it as a good possibility.

In general if you were going to try and install to your laptop drive from a desktop I would suggest you physically unplug all your other hard disks and not have any USB disks plugged in as well so that there is nothing to confuse grub later because it would be the same setup when you plop it back into your laptop ( as in one hard disk ).

You have a tricky situation here and it would take me awhile to figure it out for sure if I was sitting at your house in front of the equipment but without being there it is next to impossible for me to know for sure what has happened.

---

### Post by sjmiller85 on 2008-08-30
You, my friend, nailed the problem and resolution right on the dot!!!  Just for clarification for future references to this topic, this is what I did:

After reading your post, I immediately shut down my computer.  I have 3 hard drives attached to my Desktop.  1 is an external USB, so I unplugged that.  Secondly I had a Kubuntu dedicated hard drive.  This drive was unplugged and replaced with my laptop's hard drive.  thirdly I have a Windows Vista Hard drive.  All in all, 3 hard drives.  After unplugging all 3 and replacing the second one with my laptop's hard drive, I booted up my desktop, Kubuntu CD in the disk drive.  I initiated an install, went and had a beer, came back 20 minutes later to see the installation completed.  With higher hopes than before, I shut down, unplug my laptop hard drive (leaving all the others unplugged for now) and plug my laptop's hard drive back into the laptop.  I boot up the laptop, go through the boot-up and blamo, I now have a fully functioning Kubuntu on my laptop that was not too long ago just a heap of metal crud.

You my friend have my gratitude.  You took my 2 year old Alienware laptop that I called dead, and brought back life to it!  I owe you a beer!

---

