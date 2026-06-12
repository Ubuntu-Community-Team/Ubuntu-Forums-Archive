---
title: "How to Uninstall 9.04 beta and re-install 8.10?"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by martialartist81 on 2009-03-30
Hey all... installed 9.04 beta just to tinker with it, and so far so good, with a few exceptions (that don't really matter for this post).  I do, however, want to get rid of 9.04 and reinstall 8.10.  Thoughts?  Suggestions?  Emotional Outbursts?  'Roid Rages?

Oh, here's a few details:

Testing Windows 7 Beta as my primary partition.
Only have 1 Hard Drive.
I would like to keep the Windows 7 install the way it is, however, I'm prepared to wipe the whole drive clean, reinstall Windows 7 and then just install 8.10, however, I'd like to avoid having to reinstall 2 OS's.  

Let me know what you guys/gals think! 

Much appreciated!

---

### Post by Mark Phelps on 2009-03-30
Presuming you installed 9.04 in dual boot mode ...

Download and burn a GParted LiveCD (which you can get from distrowatch.com), boot into it, remove the Linux partition(s).

Boot from the 8.10 CD and install like you did with the 9.04 CD.  Just make sure you don't choose the "whole disk" option for installation.

If you installed it using Wubi, you should be able to simply remove it.

---

### Post by martialartist81 on 2009-03-30
Downloading it now...

Will post up with results!  Thanks!

---

### Post by coffeecat on 2009-03-30
Do you have Windows 7 on one partition and Ubuntu 9.04 on another partition (with a separate swap partition, of course)? Then you don't even have to remove the partition with the Gparted live CD. (By the way, Gparted is on all the Ubuntu live CDs anyway.)

Just boot up with the 8.10 live CD. Start the install Wizard and when you get to the partitioning stage, choose 'Manual', **not** 'Guided'.

Simply designate your current Ubuntu / (root) partition as the / partition for 8.10 and it will reformat it and install 8.10 on it. It will pick up the swap partition automatically.

If you installed with wubi, ignore everything I have said. :)

---

### Post by martialartist81 on 2009-03-30
> **coffeecat said:**
> Do you have Windows 7 on one partition and Ubuntu 9.04 on another partition (with a separate swap partition, of course)? Then you don't even have to remove the partition with the Gparted live CD. (By the way, Gparted is on all the Ubuntu live CDs anyway.)

Just boot up with the 8.10 live CD. Start the install Wizard and when you get to the partitioning stage, choose 'Manual', **not** 'Guided'.

Simply designate your current Ubuntu / (root) partition as the / partition for 8.10 and it will reformat it and install 8.10 on it. It will pick up the swap partition automatically.

If you installed with wubi, ignore everything I have said. :)

Update & New Situation:

used Gparted, wiped that partition clean (I believe it's labeled "/dev/sda2" since my Windows 7 Partition is labelled "/dev/sda1").  Now, booted up with 8.10 liveCD, and now sitting on the Prepare Disk Space for partitioning.  I have "41% Free Space" on the entire drive, that's what I want to make as the 8.10 partition.  However... (drum roll), using the Guided Variants of the install process, I'm unable to select that section of the HDD.  I'm only able to modify/add/install onto the existing Windows 7 Partition (which I don't want to do).

So I'm assuming then that I have to do the "Manual" variant of the install for the Partitioning.  Now.... the big kahuna question is, how do I do that?  What am I going to be doing in order to get 8.10 onto that correct partition (again, only a theory that it's sda2, I haven't found a way to verify that yet; open to suggestions!)?

And no, did not use Wubi.

EDIT: Update: Just tinkered with the "Manual" and was easily able to make that "Free Space" a new partition... now labeled "sda5".  More news once I get it to install/run.

---

### Post by coffeecat on 2009-03-30
I didn't catch you in time with my earlier post. You can't use Manual if you've already wiped the partitions and if you want to do it properly; you have to use one of the 'Guided' options. But as it's been so long since I've used 'Guided' I don't know which of the 2 or 3 'Guided' options you choose. What's for certain is that if you have 41% free space, one of those Guideds will pick that up and create a / partition and a swap partition for you.

**Edit:**> **martialartist81 said:**
> EDIT: Update: Just tinkered with the "Manual" and was easily able to make that "Free Space" a new partition... now labeled "sda5". More news once I get it to install/run.

Oh dear! Have you got a swap partition? Probably not. :(

---

### Post by martialartist81 on 2009-03-30
Well, yes/no.

Bigger Issue now, right after I did the "Manual" change to that Free Space partition, I mistakenly went back to "Starting up the partitioner" just before it shows you the partitions and what changes you want to make to it.... Now stuck at 50% "Scanning Disks" for the last 20 minutes.

I think I'm gonna have to reboot to get out of it, then reload Windows 7 from scratch.

Thoughts?

---

### Post by coffeecat on 2009-03-30
> **martialartist81 said:**
> I think I'm gonna have to reboot to get out of it, then reload Windows 7 from scratch.

Thoughts?

No, you won't, and yes. :)

Boot up from the live CD again (you don't need that Gparted CD) and go to System > Administration > Partition Editor. Lo and behold - Gparted!! :p Now delete all partitions **except** your Windows one (sda1?). Now in the unformatted space create an extended partition using all the unformatted space. In the extended partition, create two logical partitions, firstly a swap of 2x your RAM, but no more than 1-2GB (depending on how much total space you've got. Secondly an ext3 partition of the rest of the space. 'Apply' and if you've followed me correctly, you'll have a swap partition sda5 and ext3 partition sda6. Now close Gparted and start the installer. When you get to the partitioning stage, choose 'Manual' and designate sda6 as your / (root) partition. Finish the installation and you'll have a dual-booting system.

And now I'm going to bed. It's late here in the UK and the clocks changed yesterday so everyone's got jet-lag. :(

---

### Post by martialartist81 on 2009-03-30
Took me a little bit of searching in the Manual Install mode, but finally found what you told me to look for.  Still quite new the Linux File System and learning the little things along the way.

Anyhoot!  It's currently installing into sda6 (and yes, sda5 is the swap!).  I'll update/repost once it finished installing!

Thanks again!

---

### Post by martialartist81 on 2009-03-30
I'm in, running nice and smooth.

Finished all my updates, and now onto installing WINE and getting all my goodies working!

Thanks a ton again!

Cheers!

---

