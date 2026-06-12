---
title: "Onboard Sata"
date: 2008-08-07
forum: Hardware
---

### Post by f37u5g0d on 2008-08-07
I have a pc-chips motherboard with onboard sata.  I also am using a 5+ year old ide harddrive.  I am thinking about getting a SATA drive to replace it.  Will a sata drive work with ubuntu?  I am only buying one I don't want a raid array.  Also is there a way that I can move everything to the new harddrive?  All of my files, the operating system (as is), and all of my settings easily?  Or will I have to install the operating system on this drive, copy all of my files to a CD and then start from scratch on the settings and configurations?

---

### Post by phidia on 2008-08-07
Most sata drives should work fine with linux/ubuntu unless it some very odd or unusual hardware.
There are many threads on backing up and moving. You can use dd (see man dd) to copy your entire install. You proably will have to do some editing to fstab and maybe menu.lst to make it all work.

Take a look at the [adding a new drive Ubuntu wiki]("https://help.ubuntu.com/community/InstallingANewHardDrive") and this [howto]("http://ubuntuforums.org/showthread.php?t=599599&highlight=dd+move+partition") on moving from your old drive to a new one using dd.

---

### Post by f37u5g0d on 2008-08-07
Thank you for your help!  I must admit that I didn't expect such a quick response.  I won't start on this project for another month and already I have all the details nailed down!  Thank you again!  (Ubuntu and it's community rocks!)

---

