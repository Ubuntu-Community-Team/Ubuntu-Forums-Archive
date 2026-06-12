---
title: "Having trouble viewing files in /home/ folder on old SATA hard drive"
date: 2012-06-14
forum: Hardware
---

### Post by hoey2011 on 2012-06-14
Ok, so I have had an Acer Aspire 5517 laptop running Linux Mint 11 for the past year or so.  The entire HDD was formatted to EXT4, and just a few months ago, I backed up my MicroSD card to this computer.  About 3 weeks ago, that SD card failed, and I lost all of the data.  I was only out about 2 months of pictures, though, since the last 18 months of data was already backed up.  

Enter: the problem.

Last night, the video failed hardcore on the Acer, and after an hour or so of troubleshooting, I determined the motherboard had failed in some way.  Memory was good, hard drive was spinning up, fan was spinning.  I was forced to purchase a new machine, and I did so.  I got a Samsung NP305v5A-A0CUS, and after a bit of research, determined that Ubuntu 12.04 LTS was the distro I needed.  Booted it up, and everything worked out of the boxed, which is an experience I have never had with installing Linux (typically wifi or graphics drivers needed to be side-loaded).  

My old hard drive contains many pictures and videos that I wish to recover, approximately 10-12GB worth.  I purchased a SATA-to-USB 2.0 HDD chassis, and plugged it in.  Within 10 seconds, I had mounted the hard drive, and could access the /bin/ files, and various system components needed to boot on the Acer.  Everything I needed, was obviously in the /home/ folder, under the /hoey/ directory.  

The issue I have encountered is that my /home/hoey/ folder on the old hard drive is not showing ANY of the common directories, only two files: Access-Your-Private-Data.desktop, and README.txt .  When I attempt to open those files, I receive the error: This link cannot be used, because its target "/usr/share/ecryptfs-utils/ecryptfs-mount-private.txt" doesn't exist.

I have tried numerous programs such as parted, rsync, and running the normal file explorer with SU.  I have mounted the external drive to my internal(for identity purposes, the internal is /dev/sda, the external I am trying to gain access to is /dev/sdb, and the partition I need to get into the home folder on is /dev/sdb1).  

I am not completely new to Linux, I have been running either Ubuntu 10.04 LTS or Linux Mint 11 for the better part of 2 years now, and I am familiar with command line execution.  What I seem to be missing is why I am able to view even the python directories I installed to run IDLE, but unable to see any of my pictures and videos.  The directories just simply aren't there.  When I attempt to access the /root/ folder, I am given a no permission error.

Help?


Respectfully

-Joe (Hoey)

---

### Post by sffvba[e0rt on 2012-06-14
Seems you encrypted your home...

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

Perhaps the link above can shed more light on gaining access to your files :)


404

PS - Not sure that your link is in the most relevant sub-forum but will leave it open for another mod to move if needed ;)

---

### Post by hoey2011 on 2012-06-14
I should have taken the cue from the ecryptfs prompt that I had to decrypt this info before I could access it.  Silly, me.  I've been so frazzled trying to recover from the loss of my loved one (the Acer).  I'm trying the decryption now.

Also, as soon as I posted this, I reported it to the subforums mod, because I was unsure of the best place for it.  Hopefully it will be placed where I can get the most information, and be the most helpful when I find a solution.

---

### Post by cariboo on 2012-06-14
If you're having problems, Dustin is the maintainer of encryptfs, check out this post on his blog:

[http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)

---

### Post by hoey2011 on 2012-06-14
Alright, I GOT IT!

ecryptfs was extraordinarily simple, Kudos to Dustin.  Turns out, I had around 55GB of necessary data, and around 25GB of music, so whew, lifesaver!  

The first step was pretty simple, but I overlooked the location that the files were temporarily mounted to.  It is apparently generated per use, so keeping the terminal open and running gksudo nautilus, then navigating to the /tmp/ directory where it was mounted unlocked my successful attempt.  

I'm about 30 minutes away from a successful restore of my data, and on to a fresh wipe and nifty new backup hard drive to use for tons of data I need to backup, in case any more motherboards decide to poop the bed.

Thank you so much, guys, and I can't wait to be a contributing member with such fast response times!

---

