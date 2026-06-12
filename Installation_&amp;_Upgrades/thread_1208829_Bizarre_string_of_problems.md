---
title: "Bizarre string of problems"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by litlfrog on 2009-07-09
I'm close to actual tears here. My new installation of Ubuntu worked great for about a day, then when I rebooted, I got as far as the Ubuntu loading screen with a progress bar. After that, I get a lot of random colored bars and boxes. (If I boot from a live CD, everything looks fine.) I gave up waiting for an answer and decided to just reinstall, but when I try to tell the Ubuntu to use the whole disk and the partition editor starts, it comes back saying "ext3 filesystem creation failed." I don't have the option to use Windows because this is a work computer and we don't have any more copies. I've used Linux off and on for a couple of years, but I'm far from an expert and no one else knows anything about it. I can't go back to the initial installation of Ubuntu because the partition has been wiped and there's no one here who can get a new hard drive out of storage. What can I do to get Ubuntu reinstalled?

---

### Post by phillw on 2009-07-09
Can u get hold of an install CD for Ubuntu ?

If so - and this may well be a sledge hammer to break a nut. 

Try going into the install Ubuntu, only select manual partitioning, delete the (possibly) poorly ext3 partion and try re-creating it.

Obviously, you would lose any work saved on there - but, via the Install CD you can switch to liveCD mode & copy documents etc from your ~/home directory to a folder in your windows partition.

One of the more technical people may have a more elegant solution, but that's at least something to have a think about.

Hope you get it sorted soon.

Regards,

Phill.

---

### Post by coffeecat on 2009-07-09
I really don't know whether what I am about to suggest will work, but if I was in your situation this is what I would try. Be warned that this will definitely destroy any data on the drive, but it sounds as though you've gone beyond the point of no return anyway.

I've never seen the "ext3 filesystem creation failed" error, but it suggests that there's something wrong with the partition table. So...

Boot up from the live CD and go to System > Administration > Partition Editor (Gparted). Since you've had one (failed) attempt at creating new partition(s), it will probably be showing an exclamation mark and/or "unknown filesystem". But whatever, now go to Device > Create Partition Table. Drop the "Advanced" arrow down and make sure that the partition table type is showing as "msdos". Now click on "create". You'll get a warning that this will destroy all data, and if you OK this, after it has created the new partition table the window will refresh and should show you the whole disc as being "unallocated". Which is fine. You could use Gparted to create new partitions now, but it's easier to close Gparted down and start the graphical installer and let it do the partitioning.

I can't remember the exact choices at the partitioning stage, but the one you want should be to use the whole disc. If everything goes OK, then fine. If not, then possibly the hard drive is failing. Your comment about not having someone to get a new drive out of storage suggests that you may suspect that this is so. Am I correct?

Let us know how you get along.

---

### Post by rainwalker on 2009-07-09
I'm not sure what could be wrong, since I would normally tell you to try reinstalling, but you could try booting the Gparted live CD and reformatting the drive (either erasing anything on it and then installing ububntu, or creating whatever partition you want and installing over that, I don't think it matters). If that doesn't work, your hard drive may be dead or something, I really don't know what else to tell you :?

---

### Post by litlfrog on 2009-07-09
OK, for now things are going well. I deleted the partitions per people's suggestions and got the same error. I found instructions on how to delete the Master Boot Record by using the command

> dd if=/dev/zero of=/dev/hda bs=512 count=1

After doing that AND a false start of trying to reinstall from a DVD drive that the computer didn't like, I've finally gotten it reinstalled. Thanks so much for the responses

---

