---
title: "Failing hard drive due to shock"
date: 2015-01-22
forum: Hardware
---

### Post by d-lhoest-y on 2015-01-22
Hello guys, 

I'm in a bit of a pickle here and really need your help.
I was repairing a desktop computer on my desk when the tower fell on my laptop. The latter was on and it resulted in a massive failure (plenty of colors on the screens).

I turned it off and back on, and I had a message (summerized) kernel panic not syncing attempted to kill init! exitcode=0x00000007
Disk utility self-test fails.

I can access the Windows partition; as well as my files.
I'm doing a backup as we speak using a live CD.

What would you suggest me to do?

In advance, thanks

---

### Post by kpatz on 2015-01-22
Back up and replace the drive.  Hopefully nothing else in the laptop was damaged.

---

### Post by weatherman2 on 2015-01-22
Check the drive's real S.M.A.R.T. status.  It's possible a few sectors were messed up ("Pending Sectors").  If you can't do it with Disk Utility, try GSmartControl (which you will have to install on a live session).

If there are a few pending sectors, once you have completely recovered all important files, try zeroing out the drive.  That may clear the sectors (check S.M.A.R.T. again afterward) and the drive may be just fine.  I have done this a few times on hard drives that "failed" but worked fine for years afterward once the drive was zero'ed out/sectors cleared.  But it doesn't always work.  Sometimes drives fail and must be replaced, of course.

Before zeroing, you could try to make a copy of your whole Windows partition (Clonezilla can copy partitions as images to files) and see if you can copy that partition without errors; if so, after you've zeroed the old drive or replaced it with a new drive, you may be able to restore the Windows partition to the clean drive without needing to re-install Windows.  Same with the Linux partition if there is one, though Windows usually takes much longer to re-install/activate etc.

---

### Post by sammiev on 2015-01-22
Try your HD in another computer after backing it up. It maybe your computer that is damaged and not your HD.

---

### Post by mamamia88 on 2015-01-22
My suggestion sounds like a good time to switch to an ssd

---

### Post by mamamia88 on 2015-01-23
You can get a 120gb ne for $50 if you shop around less than the price of the average videogame.  But if you dont even have sata connectors i guess its pointless

---

### Post by d-lhoest-y on 2015-02-01
Brilliant ideas, I'll try all of that. At the moment I am dd_rescuing the diskn 253GB of error size, 1590 errors. 
Splitting the blocks did not work, I'm trying the retrim but to no avail so far.

I'll keep you updated! Thank you

---

