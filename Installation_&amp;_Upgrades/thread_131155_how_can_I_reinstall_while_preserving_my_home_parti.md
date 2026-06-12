---
title: "how can I reinstall while preserving my /home partition?"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by nrwilk on 2006-02-15
The last few times I've reinstalled, I made sure to make a partition for /home.

Now that I've encountered a situation where I need to reinstall, I'd like to reassure myself that I won't lose the data I'm trying not to lose.

When I get to the partitioning step, do I wipe the / partition and keep the /home partition, choosing to mount it?  Will it overwrite the data on the /home partition?  How do I link my home directory on /home to the user which is created during installation?  Do I have to make a new user entry and later copy the stuff from the old home directory to the new one?  If I name the new user entry the same username I'm using now will it overwrite the /home/<username> folder?

Can anyone lay out the process step-by-step?

Thanks!

---

### Post by Sutekh on 2006-02-15
[QUOTE=Fealos]The last few times I've reinstalled, I made sure to make a partition for /home.

Now that I've encountered a situation where I need to reinstall, I'd like to reassure myself that I won't lose the data I'm trying not to lose.

When I get to the partitioning step, do I wipe the / partition and keep the /home partition, choosing to mount it?  
[/QUOTE]Yes this is how to do it.  At the partition stage, select your root partition (/) and choose to format it.  

With your home partition, you select it and choose to mount it in /home.

[QUOTE=Fealos]
Will it overwrite the data on the /home partition?  How do I link my home directory on /home to the user which is created during installation?  Do I have to make a new user entry and later copy the stuff from the old home directory to the new one?  If I name the new user entry the same username I'm using now will it overwrite the /home/<username> folder?[/QUOTE]
I'm pretty sure that the same user name will 'take-over' but not 'write-over' your home partition.  A new user name should create a new /home/user folder.

[QUOTE=Fealos]
Can anyone lay out the process step-by-step?

Thanks!
[/QUOTE]
I'm gonna adapt a step from Herman's Guide (which is as good a installation guide as you will ever see)

[Herman's Guide to Installing Ubuntu and Windows (NTFS)]("http://users.bigpond.net.au/hermanzone/p3.htm")

 - When you get to the partitioning step, your partitions will probably be not named /, /home, and the others, they will probably be listed in the partitioner as /media/hda1, /media/hda5, etc.  So you will need to know what your partitions are called before doing any of this (use 'sudo fdisk -l', or 'df -h')

 - Then select your root partition, now that you know what its called)

 - Look at Step 19 (19th NTFS) of Herman's guide.  Because you already have an existing filesystem on it, it will look slightly different, but there should be an option that allows you to format the partition.  Choose to do this for your root (/) partition and then choose to mount the new root partition as /.  Then choose 'Done setting up this partition'

 - When you select your /home partition, do not format it, but just choose to mount it at /home.

 - Then you can continue the installation like every other time you've done it.


I hope you got what I was saying.  Remember that the formatting doesn't take place until after you specify all this, so you will have a chance to double check.  I might try this later today and take some photos of the partition options.

---

### Post by nrwilk on 2006-02-15
I understand all of it.  Thanks a lot, man!  :) 

I pretty much knew what I had to do, but I wanted to make sure there wasn't another step I couldn't think of to make sure that /home got preserved as it is.

I've even done this before, but I'm just a bit overly paranoid about it, I guess.

---

### Post by Sutekh on 2006-02-15
Well I guess you don't ever want to get to casual when it comes to formatting.  

I always hesitate on that last button press;
"Now did I copy *everything*" :D

---

### Post by nrwilk on 2006-02-16
oh NO!  I have no idea what to do with this!

After install, when rebooting, at the filesystem check, it tells me that the fsck failed and that the /home partition has an unreadable filesystem.  All I did was tell it to mount at /home.  What can I do?  It isn't reading the partition at all!  I rebooted and it happened the second time too.

Does this happen often at install?

How did it get corrupted?

Do I have to wipe it?

---

### Post by Sutekh on 2006-02-16
I have no idea why that would happen!  Anything else you can share about the installation or the error?  

I don't see how it could be corrupted.

Is it something like this?

[http://ubuntuforums.org/showthread.php?t=35591&highlight=fsck+failed]("http://ubuntuforums.org/showthread.php?t=35591&highlight=fsck+failed")

If you have a Live CD try booting into that, and mounting your /home partition.

---

### Post by nrwilk on 2006-02-16
the install went normally, just as it always has gone.  It says that the partition is not an ext2 filesystem.  It says that if it is ext2 or ext3, the superblock must be bad.  I edited the startup script to automatically fix filesystem errors that occur at boot, but that hasn't worked.  It says to try running e2fsck -b <backup superblock> <device>.  I did this, and it caught a whole lot of errors, and asked if I wanted to fix each one, I said yes to all fixes, then it said "/dev/hda4 has been modified!" But, at the next boot it fails again.  I ran the e2fsck command again, and it caught all the same errors again.  I told it to fix them, but it still fails at boot.

The weird thing is that I CAN mount the partiton, and I can see it's files after bootup.  I have no idea what this means.

Any help?

---

### Post by nrwilk on 2006-02-16
nevermind.  I diagnosed the problem.  It's not /dev/hda4, it's /dev/sda2.  I had my firewire HDD turned on while installing, so the startup isn't finding it when I bootup.  if I tell it to ignore it, it continues booting up, mounting /home in the process.   I'll fix it tomorrow thanks for all the help!

---

### Post by Sutekh on 2006-02-16
Well hope it works out okay, sounded scary for a while!

---

### Post by nrwilk on 2006-02-16
So, I edited my fstab file to remove the /dev/sda2 entry, and all is fine.  Thanks for your help, Sutekh!

On a different note, though, I have to say that even though /home is retained, it's a bigger pain in the butt than I thought.  I would rather have backed up important docs and reinstalled from scratch.

Oh well.

---

### Post by Sutekh on 2006-02-16
I don't know why it went pear-shaped.  I didn't have any problems, and it only took the 30 mins to re-install Ubuntu.

---

### Post by nrwilk on 2006-02-17
Did you use the same username when reinstalling as you had been using before the install?  Did it just automatically use the existing home directory and user group?  That would have sped up my process a whole lot.

I was afraid that would mess with the existing home folder, so I made a differently named user account and chowned everything in the existing home folder, and copied it all over to the new home folder.

---

### Post by Sutekh on 2006-02-18
Hey your name is changed now?

I used the same username.  Who then became the owner of my old home.

Funny thing is the other day I tried installing the AMD64 version on some free space, *without* sharing the /home partition, putting it all on this free space.

The user I created for the 64bit version became the new owner of my 32bit home folder when using the 64bit version!  Even though they had completely different names.  Twas very wierd.  Everything was fine when using the 32 bit version though.

Who knows.

---

### Post by nrwilk on 2006-02-18
Crazy.  I think we may be getting too esoteric about this.  :p 

hehe, no but it's good to know.

Yes, the name changed.  It was long past time to change it.  Been using the other one for too long.

---

