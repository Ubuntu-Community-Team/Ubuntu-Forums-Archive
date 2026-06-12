---
title: "Messed up my dual boot - do I need to do something with GRUB?"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by rosiet on 2009-05-06
I just got a new laptop and set it up dual-booting Windows Vista and Ubuntu 9.04.

Then I decided I wanted to mess around with the partitions.  I deleted the shadow Windows recovery partition.  Windows was still working fine.  I then used gparted to move the Windows partition to fill the gap (but keeping it as the same partition), and resized it at the same time (leaving a big gap after it that I was planning to create a /home partition in).

There were no error messages but now when I choose Windows on the boot menu the computer says "Starting up.." then restarts and sends me back to the boot menu.

Have I messed up Windows or do I just need to change some of GRUB's settings?

---

### Post by Bartender on 2009-05-06
Please tell me you made recovery discs before deleting the recovery partition.
I also tried moving Vista with a GParted LiveCD.  Vista quit working.  It's been said to use the Vista partitioner when trying to move Vista.
There may be some tricks to geting it back, but I just popped in the recovery discs and started over.

If you decide to go that way, I have a suggestion.  Use GParted LiveCD to wipe the drive.  Decide how much space you want to give Vista, and create a primary partition.  Apply the change.  Use GParted to format the partition as NTFS.  Apply.

When you pop your Vista recovery CD in, it will only recognize the NTFS partition, leaving the rest of the drive alone.  

There are several choices as far as the rest of the drive.  Here's four.  This would be addressed with GParted, either before re-installing Vista or after.
1) Leave it unformatted.
2) Format it as a primary partition, then set the file system as ext3 or 4.
3) Create an extended partition, and a logical partititon inside, set as ext3 or 4.
With 1, 2, and 3 you could use the "Guided" setting when you get to installing.

4) Create an extended partition, then three logical partitions inside.  Two ext3 or 4 partitions for / and /home, and one swap partition.  You would only do this if you plan on setting up your partitions manually when you get back to the Ubuntu install CD.  You can create and format the swap partition from GParted.  The Ubuntu installer (when using the "manual" option) will recognize it and leave it be.  The / and /home partitions aren't handled the same way.  In GParted you would pick the sizes and the file systems (ext) but you don't actually dedicate those partitions as / and /home until you're in the "manual" mode within the Ubuntu install CD.  Using the Ubuntu installer you would mount / to one of your previously built ext partitions and mount /home to the other one.
It all sounds a little complicated, but it's pretty easy after you've done it a few times.

---

### Post by rosiet on 2009-05-06
Thanks, Bartender.  I may well try that if it comes to it.

Why do I need to format the whole drive first if Windows will automatically pick the NTFS partition?  Can't I just delete the current Windows partition and create a new NTFS one without having to reinstall ubuntu? 

Would be happy to hear of any possible shortcuts...

---

