---
title: "Win XP drive images and Ubuntu Installation"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by grocer on 2009-05-03
I just went through upgrading my laptop from a 60 gig to a 320 gig hard drive and had a devil of a time getting my XP image to boot properly after successfully copying the image to the new drive.  For anyone with similar issues, here's the answer...

Short version - 

Step 1) Edit the boot.ini (this may or may not be required, if windows was on the first partition of the disk and is on the first partition of the new disk, not necessary; in my case, I had a FAT32 partition for system recovery and I didn't copy that partition to the new drive so my boot.ini needed edited)

Step 2) Delete the contents of MountedDevices in the System Hive of the registry in XP with the [_Offline NT Password & Registry Editor_]("http://home.eunet.no/pnordahl/ntpasswd/") CD because windows hashes its partitions and the surrounding partitions in the registry.

I'm guessinig if you're messing with images, you have some technical skill...I may post a more detailed follow-up on how to install Ubuntu and Windows on a dual boot system using an XP drive image if anyone thinks it will be helpful...

---

