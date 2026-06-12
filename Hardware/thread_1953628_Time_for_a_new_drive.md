---
title: "Time for a new drive"
date: 2012-04-06
forum: Hardware
---

### Post by Lloydb39 on 2012-04-06
What I have: Dell Dimension 4600 with 1.5 gigs of memory, running Ubuntu 11.10, 120 gig Seagate hard drive with 12 bad sectors.
What I want: To install a 250 gig hard drive to replace old one, moving my OS and (few) files I have, without reinstalling Ubuntu.
Can anyone point me to detailed instructions on how to accomplish this step by step? Ideally, I'd like to reformat the old drive after replacing it and use it for a backup drive.

---

### Post by Mark Phelps on 2012-04-06
You can do this using Clonezilla.

Read through the instructions in the link below:

[http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone]("http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone")

---

### Post by sudodus on 2012-04-06
A simple solution would be to clone your drive. This is possible from a smaller to a bigger drive. Both drives should be unmounted, and you should boot from a third drive for example a CD or USB Ubuntu install drive or a dedicated cloning tool.

You can run dd from your Ubuntu install drive, but it is risky. A small mistake and you wipe your original drive instead of clone it. You can download the iso file of Clonezilla, make a boot CD or USB and clone using Clonezilla. You will be prompted via a 'wizard', and if you select 'beginner mode', it helps you avoid mistakes.

After cloning, you can create new partitions or grow a partition, so that the extra space will be available.

It is also possible to design the partition table before transferring the system and data, but it is more difficult.

---

### Post by ahallubuntu on 2012-04-06
Clonezilla has not proven reliable for me.  Sometimes it works perfectly; sometimes it just fails without obvious explanation in the middle of a clone.  While it's nice to have a free tool like Clonezilla available, it's not very easy to use.

I own a copy of True Image from Acronis; the newer versions do a good job of cloning Linux partitions, so that's usually what I use these days.

dd will also work to clone  a drive (boot a live CD and running it from there - don't use dd on a live file system).  As mentioned above, you must be EXTREMELY careful when using dd; if you type the wrong destination partition, it's quite easy to ruin your data in half a second.  But if you confirm the command syntax and run it correctly, it should be fine.

For example, if your old drive is sda and the new one is sdb, MAKING ABSOLUTELY SURE sda is the 120GB and sdb is the 250GB drive(!!!!!), you could type from a command line, after booting a live CD:

sudo dd if=/dev/sda of=/dev/sdb bs=2048

This will copy EVERYTHING from /dev/sda to /dev/sdb and may take quite a while, a few hours at least.  Afterward, start up gparted from the live CD and resize the last partition by something tiny like 1MB; this will allow it to grow to use the rest of the drive instead of being as small as it was on the 120GB drive.

Of course, you may get errors copying those bad sectors, depending on what "bad sectors" means.

---

### Post by sudodus on 2012-04-06
I'm glad you observed the bad sectors, *ahallubuntu* :-)

Then I think that dd is really no good, ***ddrescue*** is much better. I think Clonezilla will succeed if there is no file that is partly in the bad sectors.

---

