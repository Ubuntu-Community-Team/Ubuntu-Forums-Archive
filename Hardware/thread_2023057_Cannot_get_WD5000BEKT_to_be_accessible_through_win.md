---
title: "Cannot get WD5000BEKT to be accessible through windows."
date: 2012-07-11
forum: Hardware
---

### Post by stykea on 2012-07-11
Something has gone seriously wrong with my memory drive. I'm typing this  through ubuntu, and this is what its' drive utility is showing me:

[IMG]http://i.imgur.com/Vs5Wd.png[/IMG]

I can access my files throguh Ubuntu. Back  at windows, my options are less limited. I can't view the hard disk at  all in Explorer, although it shows in  Disk Manager. I can't make any  changes to it. Trying to assign letters  to it through command prompt  returns errors. EaseUS partition manager  also doesn't allow me to do  anything with the partition I need.  Partition recoverer returns an error  when targeting this hard drive. I need the highlighted partition to be accessible through windows as it had programs installed on it and it's gone ahead and messed everything up. 

I  think one of the culprits, if not the culprit is the partition type,  linux swap 0x82. However, when I try and change it, I get 

"Message did not receive a reply (timeout by message bus)"


Any ideas?

---

### Post by ahallubuntu on 2012-07-11
Looks like something got corrupted for sure.

Before messing with partition types etc., you first need to be sure you have *EVERYTHING* on this drive backed up somewhere else, just in case!!!  Don't take any chance.  Then, if you mess something up, you can just re-format and start over.

I'd probably use Gparted to try to change the partition type after that.  I'd also wonder how it got changed in the first place.

---

### Post by stykea on 2012-07-11
> **ahallubuntu said:**
> Looks like something got corrupted for sure.

Before messing with partition types etc., you first need to be sure you have *EVERYTHING* on this drive backed up somewhere else, just in case!!!  Don't take any chance.  Then, if you mess something up, you can just re-format and start over.

I'd probably use Gparted to try to change the partition type after that.  I'd also wonder how it got changed in the first place.

I was messing about installing some Linux distributions. I think I made it a swap partition by accident. Thank you, I'll give it a shot soon.

---

### Post by oldfred on 2012-07-11
You may be able to use sfdisk. Then you edit text file it creates & reimport it as the new partition table.

But do not use any liveCD that automounts the swap partition. Ubuntu's liveCD does mount swap. I think Knoppix & gparted do not, but am not sure.

Example of direct change, you would want 07 or 7 for sdb2, see man sfdisk for details:
change sdb7 to type 83
sudo sfdisk --change-id /dev/sdb 7 83


caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)

---

