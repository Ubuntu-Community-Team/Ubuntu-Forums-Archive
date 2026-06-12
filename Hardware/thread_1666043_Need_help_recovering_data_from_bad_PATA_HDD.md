---
title: "Need help recovering data from bad PATA HDD"
date: 2011-01-13
forum: Hardware
---

### Post by lonewolf454 on 2011-01-13
I have 2 - 80GB IDE/PATA hard drives in my computer, 2nd one was just files, and disk 1 was partitioned and had xpsp2(NTFS) and ubuntu on it.  I have been having trouble for a while with computer rebooting etc, and determined hard disk 1 to be bad.  It got to where xp wouldn't boot (possible virus- wife uses computer a lot and likes to click on things, etc) but then I started having trouble with Ubuntu taking extremely long time to open folders etc and last few days it wouldn't do anything, and disk has gotten noisy.  These drives are about 8 years old with moderate to high use.  Anyhow, I backed up all data on disk 2 and swapped it to be master and other (bad) disk the slave.  I have successfully installed xpsp2 and ubuntu 10.04LTS on this disk.  

My problem is recovering data from disk 2(old disk 1).  I can see the disk and it reports correct size, two partitions, etc.  When I try to mount it ubuntu complains with an error 13 that NTFS cannot be mounted due to error, etc and wants to run chkdsk /f.  I do not want to format I will lose all data.  How can I mount this to recover data?

---

### Post by IcarusR on 2011-01-13
> chkdsk /f

Will not format the drive but check for errors & fix any found.
Unfortunately there is no linux equivalent to 'chkdsk /f' that I've heard off that works reliably.

Having run chkdsk on the drive you can download & install testdisk onto your Ubuntu partition & hopefully you will be able to copy all your data from the failing drive.

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

PhotoRec may also be of use.

[http://www.cgsecurity.org/wiki/PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")

---

### Post by lonewolf454 on 2011-01-13
But will I run chkdsk from windows (not possible) DOS terminal or Ubuntu terminal?  I assume I would first have to point to the windows drive designator, in this case the d: drive?

---

### Post by IcarusR on 2011-01-13
You need to run 'chkdsk /f' from dos, possibly from within windows I'm not sure. It is a dos program & will not run from Ubuntu.

'/f' tells chkdsk to fix errors.

Yes you have to add a drive letter.

More info here on M/S support page

[http://support.microsoft.com/kb/315265]("http://support.microsoft.com/kb/315265")

---

### Post by Ad@m on 2011-01-13
ntfsfix /dev/sdX

Where X is your drive letter

This may allow you to mount the drive and recover the files.

---

### Post by lonewolf454 on 2011-01-21
chkdsk /f didnt help did it 3 times,  I cant mount it with ubuntu and windows wants to format it, not an option.  I moved it to position2 (slave) drive, and installed fresh copy of windows and ubuntu 10.04lts on other drive, they boot fine, just havent had much luck recovering data off this drive, can manually go in to some of it with testdisk, but it will be a very slow process, would be uch better if I could mount it and copy the files that way.

It seems the mbr is still screwed up even though I told it fix the mbr from within testdisk.

---

### Post by trundlenut on 2011-01-21
Can the windows install see it?  As it is running as slave and the machine boots off the other driver the MBR on the suspect drive should be irrelevant.

Does the drive make any odd noises, clicking, ticking or whining etc?  Does it feel hotter or colder than the other one?

---

### Post by lonewolf454 on 2011-01-23
Windows "sees" the drive (now labeled d:) but if it is clicked on, computer waits awhile and after a couple of minutes, windows box pops up and wants to format the drive.  Ubuntu still won't mount it either.

It does click and sound like it stops abruptly perodically.  If I run chkdsk on it there are missing/bad sectors reported.

---

