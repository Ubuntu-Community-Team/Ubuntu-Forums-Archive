---
title: "Dual-Boot dilemma with Ubuntu!!!"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by tongrd on 2009-09-28
I'm currently looking at installing an OS onto my computer so that I can recover my files. Its quite a long story, but in short basically I was in the process of updating Windows to Vista SP2 and after the restart it didn't work, something wrong with the logs or something but apparently it can't be fixed. I dont seem to have backups or recovery points, and I've exhausted Robocopy (wasn't very good) and have turned to an alternate OS to solve my problems.

I would just follow the guides to dual boot windows-ubuntu, though my situation is a bit different. For starters, Windows itself doesn't boot up, I can only run the recovery console part from my recovery partition or allow it to boot up and eventually get stuck running some wierd text across the screen. :(

So my question is, how can I install Ubuntu so that I can use it as an OS to recover all my files? Should I try the usual Windows-Ubuntu dual boot method (doubt it will work as i can't get into windows) or should I install Ubuntu itself on my C: Drive (not sure if this will work or how it will work)?:confused:

Any help is appreciated, also if there are any awesome guides that I've somehow missed on a similar case that'd be great too :)

---

### Post by DFlame on 2009-09-28
There's no need to install if you only wish to do some file recovery. Ubuntu will run from a LiveCD, giving you access to the tools you will need.

In this case, I'd download, burn and boot a LiveCD of Jaunty(9.04) or Hardy(8.04). When this loads, it is possible to gain access to the Vista files on the hard disk.

What happens from here depends on the equipment you have. A spare CD/DVD burner can be used to make discs containing the files or the files could be sent to another computer on the network. Failing that, you could dump the files from the internal hard disk to an external one or use a smaller thumbdrive to ferry files from the 'bad' system to the other.

When the backup is complete, you could re-install Vista and restore your files. If you like Ubuntu, you could follow regular Dual Boot instructions afterwards to get that kind of system. Hope this offers some insight :)

---

### Post by tongrd on 2009-09-28
> **DFlame said:**
> There's no need to install if you only wish to do some file recovery. Ubuntu will run from a LiveCD, giving you access to the tools you will need.



Thanks for the advice I'll give that a go now, just one question, is the livecd the one i download from the website or is it a different file?

---

### Post by wojox on 2009-09-28
LiveCd should be the one you downloaded.

---

### Post by tongrd on 2009-09-28
Ok, I've finally gotten Ubuntu to work and it looks great, I might use this instead of Windows. Only problem is I'm still trying to backup files, and it keeps giving me an Error with File is too large, when there is 100GB in the External and the file is only 4.4GB . I read somewhere that I might have to partition or format my External HD to NTFS, is this true? How can I copy my files?

---

### Post by presence1960 on 2009-09-29
sorry

---

### Post by mailman1175 on 2009-12-05
> **tongrd said:**
> Ok, I've finally gotten Ubuntu to work and it looks great, I might use this instead of Windows. Only problem is I'm still trying to backup files, and it keeps giving me an Error with File is too large, when there is 100GB in the External and the file is only 4.4GB . I read somewhere that I might have to partition or format my External HD to NTFS, is this true? How can I copy my files?

I know this is an old thread (I stumbled across it looking for something else and noticed you never really got much of a response), and I don't know if you've figured out the source of your problem or not, but here's the deal: FAT file systems, as far as I understand it, have a maximum file size of 4 GB. HTH.

---

