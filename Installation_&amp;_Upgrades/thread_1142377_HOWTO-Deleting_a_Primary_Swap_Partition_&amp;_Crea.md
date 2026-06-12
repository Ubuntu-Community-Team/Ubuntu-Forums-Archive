---
title: "HOWTO-Deleting a Primary Swap Partition &amp; Creating a New Extended Partition with a Sw"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by Sugi on 2009-04-29
Deleting a Primary Swap Partitiion and Making a New Extended Partition with a Swap Partition inside of that.

Get your LiveCD ready and put it into your computer and reboot
*sudo reboot

Now running off your livecd, open up Partition Editor *gparted*

Select your old swap partition -> Right Click -> SwapOff

Select your old swap partition and delete it. 

Now create a new partition with the remaining space of your old swap partition (mine was 512 BM)

Create the new partition as an "Extended" partition.

Select your new "Extended" partition and create your new swap partition inside of that. (Once again my new swap partition will be 512 MB)

Select your New Swap partition -> Right Click -> SwapOn

Find your new swap partition, swapon -s, My new swap partition was /sda5.

Find the UUID of your new Extended Swap Partition,
*sudo blkid

Take the UUID number and replace it with /deb/sda# in your fstab
*sudo nano /etc/fstab

Example:
Before:
/dev/sda3 swap swap defaults 0 0
After:
3578985eh-587y-krf3-84683t3u26 swap swap defaults 0 0
****Please remember this is only an example, this is not a real UUID number and you should not use it for your own UUID. You will have to look up your UUID for your new swap parition. Once again, will be *sudo blkid

If all is well, boot back into your OS. Open up your terminal and:
*swapon -s

It should return with all of your active swap partition. If it does, you're all ready to go. You now have a new extended partition with your new Swap parition inside of it and you freed up another Primary partition. Now go install another OS!!!

TROUBLESHOOTING:
But if it doesn't return any Swap Partitions, Let's try activate all Swap Partition
(if this returns any information at all that means there are issues with your fstab.)
*sudo swapon -a

Your error message will probably say something like
swapon: 3578985eh-587y-krf3-84683t3u26: no such file or directory

The best way to fix this, is find your UUID and repaste it back into your fstab. This should fix it. 
*sudo blkid

Copy the UUID number correct, the whole thing and input it into your fstab
sudo nano /etc/fstab

Example:
3578985eh-587y-krf3-84683t3u26 swap swap defaults 0 0

Now save the fstab and let's see if it's working again.
swapon -s

If it returns with your swap partition. Then all is good and everything is fixed.

Credit: geirha from IRC provided information on the troubleshooting.

Cheers,
Sugi

The Original Post

[I]I have installed the following OS on my laptop in order: Ubuntu Hardy, Vista, and now Osuse 11.1.  I am trying to install on my single harddrive, everything has gone oh kay until now.  I am stuck at the point where I need to setup my partition table for my third OS.  Which I am having a problem with, because the LiveCD of OpenSUSE 11.1 does not see my free space which is 29 gigs.  

My current setup: 
sda 1 WIndows Vista
sda 2 Hardy / 
sda 3 Hardy swap 
sda 4 Hardy /home .  

I think I know the problem, all of these partition is set to primary (if I have remembered correctly).  And if I am not mistaking, a harddrive can not go over 4 primary partitions of a harddrive.  Is this correct?  By the way, I am unable to see which partition is primary or logical with the OpenSuse LiveCD.

And if this is the issue, is there any way around this besides from reinstalling the Ubuntu OS with logical parition.... I do not think this is possible.

Thank you,
Sugi[/I]

---

### Post by LoloftheRings on 2009-04-29
Someone is gonna have to confirm this, cuz I'm not sure.
1. Remove the swap partition
2. create logical partition swap
3. create logical ext3 partition for Suse

Hope this helps

---

### Post by Sugi on 2009-04-29
I would have to edit the line in the fstab to corect this after deleting and making a new swap logical partition?  And do I have to turn off the swap partition before deleting the swap partition?  Can it not be active when deleting the swap partition right? even from a LiveCD will the swap partition be active?  Also, will this even work? Does extended/logical partition require at least one primary partition?

Sugi

---

### Post by Mark Phelps on 2009-04-29
> **Sugi said:**
> I would have to edit the line in the fstab to corect this after deleting and making a new swap logical partition?  

Correct, but you can use fdisk -lu and blkid commands to get the /dev and UUID info needed to do that.

>  And do I have to turn off the swap partition before deleting the swap partition?  Can it not be active when deleting the swap partition right? even from a LiveCD will the swap partition be active?  

I had to do this very thing recently when I needed to add another partition to a drive with 4 primaries alread.  Open Partition Editor, select the swap partition, and select Swapoff.  Then, unmount that partition.  Then, you can delete it.

Then, you can create an Extended partition, and after that, create a Swap partition inside that.  Then, select the Swap partition again and select Swapon.

> 
Does extended/logical partition require at least one primary partition?
Sugi
NO .. but you create logical partitions inside an Extended partition.

However... Vista MUST be in a primary partition, and if you're thinking about shrinking it to make more room, be sure to use the Vista Disk Management tool; don't use GParted or the Ubuntu partitioner.

---

### Post by Sugi on 2009-04-29
Deleting a Primary Swap Partitiion and Making a New Extended Partition with a Swap Partition inside of that.

Get your LiveCD ready and put it into your computer and reboot
*sudo reboot

Now running off your livecd, open up Partition Editor *gparted*

Select your old swap partition -> Right Click -> SwapOff

Select your old swap partition and delete it.  

Now create a new partition with the remaining space of your old swap partition (mine was 512 BM)

Create the new partition as an "Extended" partition.

Select your new "Extended" partition and create your new swap partition inside of that.  (Once again my new swap partition will be 512 MB)

Select your New Swap partition -> Right Click -> SwapOn

Find your new swap partition, swapon -s, My new swap partition was /sda5.

Find the UUID of your new Extended Swap Partition,
*sudo blkid

Take the UUID number and replace it with /deb/sda# in your fstab
*sudo nano /etc/fstab

Example:
Before:
/dev/sda3 swap swap defaults 0 0
After:
3578985eh-587y-krf3-84683t3u26 swap swap defaults 0 0
****Please remember this is only an example, this is not a real UUID number and you should not use it for your own UUID.  You will have to look up your UUID for your new swap parition.  Once again, will be *sudo blkid

If all is well, boot back into your OS.  Open up your terminal and:
*swapon -s

It should return with all of your active swap partition. If it does, you're all ready to go.  You now have a new extended partition with your new Swap parition inside of it and you freed up another Primary partition. Now go install another OS!!!

**TROUBLESHOOTING:**
But if it doesn't return any Swap Partitions, Let's try activate all Swap Partition
(if this returns any information at all that means there are issues with your fstab.)
*sudo swapon -a

Your error message will probably say something like
swapon: 3578985eh-587y-krf3-84683t3u26: no such file or directory

The best way to fix this, is find your UUID and repaste it back into your fstab.  This should fix it.  
*sudo blkid

Copy the UUID number correct, the whole thing and input it into your fstab
sudo nano /etc/fstab

Example:
3578985eh-587y-krf3-84683t3u26 swap swap defaults 0 0

Now save the fstab and let's see if it's working again.
swapon -s

If it returns with your swap partition. Then all is good and everything is fixed.

Credit: geirha from IRC provided information on the troubleshooting.

Mark Phelps, you were a little misleading in your post, but all is well.  You do not have to unmount the Swap Partition after using SwapOff. At this point, the Swap Partition is ready to get deleted.

Cheers,
Sugi

---

