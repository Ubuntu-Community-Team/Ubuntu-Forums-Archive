---
title: "Netbook Remix fails to install - &quot;failed to remove conflicting files&quot;"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Arathon on 2009-04-26
I've tried about five times to install Ubuntu NBR onto my Asus EEE 1000H.  For those of you who have one, you'll know that there are two HDDs - an 8GB drive, on which I install my OS and swap, and a 32GB drive that I put /home onto.  Naturally, I use the manual partitioner, so that I can tell it to mount /home in the proper place.

The problem is a fairly undescriptive error message that happens early in the process, right after formatting the 5.7 GB OS partition.  It gives me an error message titled "Failed to remove conflicting files" with the text:

[INDENT]The installer needs to remove operating system files from the install target, but was unable to do so.  The install cannot continue.[/INDENT]

By this point, it's already formatted the old OS.  I tried ext3 and ext4, with no difference in the results.  I also tried using gparted to manually format before running the installer, but that made no difference.  I even deleted the lost+found directory on the newly formatted partition just to see if that might be what it was complaining about.

Does anyone have any suggestions about how to get a better, more descriptive error message?  Or any ideas as to what's going wrong?

Thanks....

---

