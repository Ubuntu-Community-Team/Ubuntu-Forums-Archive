---
title: "Did Ubuntu 9.04 Install overwrite my RAID array?"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by PencilGeek on 2009-08-24
On Saturday, my Ubuntu RAID server boot drive crashed. I purchase another PATA drive, download Ubuntu 9.04, and begin the installation. I notice the default installation drive is one of my SATA RAID5 drives, even though my PATA drive is (and always has been) the default boot drive. Instead of accepting the default SATA drive for installation, I select my new 250G PATA drive, and perform the installation.
 
After installation is complete, the computer reboots, then black-screen -- nothing. Reboot: nothing. Reboot again: nothing. Now I'm worried that Ubuntu accidentally wrote the installation to my RAID drive, I turn off the computer, unplug all of the RAID drives, and reinstall Ubuntu. After it's done, reboot, and all is fine.
 
Install mdadm, reassemble the array, and mount it. The array won't mount because it says the filesystem is corrupt on the RAID array. I notice I accidentally forgot to plug in one of the RAID drives. Turn off the computer, plug it back in, and go through the same procedure. Same results. OK, now I notice the array is degraded because of the one-time missing drive, so I re-add it and the array rebuilds overnight.
 
Back to remounting the array, and same problem: filesystem corrupt. dmesg reports that the group descriptors are corrupt. I take the computer to work, and have our RAID guys look at it. Their diagnosis: I have a two-disk failure in my RAID-5. I claim that's impossible because the failing boot drive isn't related, and there was really no possibility of whatever failure occurring on my boot drive, also caused a failure on one of my RAID drives. Basically, that just didn't happen. So what did happen?
 
We could only build one scenario that would have caused a 2-disc failure. And if this is true, then Ubuntu installer has one heck of a serious problem. Here's the only thing that makes sense. During the first install, whether I wanted it to or not, Ubuntu installer did in fact use, or partially use one of my RAID drives for installation data. That's DISC-1 failure. Then, by accidentally failing to plug in one of the drives after the second installation procedure, the array became degraded. Once degraded, it needs to be rebuilt. Upon re-adding the drive, the array rebuilds from 1-FAILED drive, 4-GOOD drives, onto my re-added drive. Therefore the re-added drive now contains rebuild data that is partially good, and partially bad (4/5 good, 1/5 bad). Now, it's a 2-DISC FAILURE and the array is hosed.
 
If this did not happen, can anybody explain why I can't mount the filesystem on the RAID array, and why mount reports that it's not a valid ext3 filesystem; and dmesg contains errors saying there are corrupted group descriptors? fsck -n ran and did indeed find an ext3 filesystem, but reported thousands of iNode and descriptor errors.
 
I appear to have the same pathology and error messages as the thread listed below.  User installs new boot drive, can't mount ext3 filesystem thereafter.  In my case, I'm so willing to give up as he was.  I'll have to pay for a data recover service if I can't get the array to come back to life.
[http://ubuntuforums.org/showthread.php?t=833770](http://ubuntuforums.org/showthread.php?t=833770)
 
What happened to my array? Did Ubuntu really clobber it during the installation?

---

