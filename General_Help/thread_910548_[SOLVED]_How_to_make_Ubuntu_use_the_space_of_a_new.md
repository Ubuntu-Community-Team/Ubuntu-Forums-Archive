---
title: "[SOLVED] How to make Ubuntu use the space of a new HD?"
date: 2008-09-04
forum: General Help
---

### Post by aqui_c on 2008-09-04
Hi!
I'm going to buy a new HD to use with my Ubuntu installation. However, my question is how to configure Ubuntu so it begins to use the new HD.
I mean, I could change the /home directory to the new HD, and mount it, etc. but the other directories like /usr, would continue to be in the same HD, right?

How can I make so Ubuntu uses from now on the new HD for (almost) all the directories. (I can't simply move everything to the NEW HD, because I have grub installed in the master HD, since it's being shared with Windows.)
Thanks in advance!

---

### Post by Elfy on 2008-09-04
You could move your home - [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Or you could use it as a data storage and add it to fstab, easily accomplished.

---

### Post by tuxulin on 2008-09-04
are you saying that you have 2 drives or 1.
one with windows and grub the other with ubuntu.

anyway why not simply clone the disk to the new one

Tuxulin

---

### Post by SpaceMaster on 2008-09-04
> **aqui_c said:**
> Hi!
I'm going to buy a new HD to use with my Ubuntu installation. However, my question is how to configure Ubuntu so it begins to use the new HD.
I mean, I could change the /home directory to the new HD, and mount it, etc. but the other directories like /usr, would continue to be in the same HD, right?

How can I make so Ubuntu uses from now on the new HD for (almost) all the directories. (I can't simply move everything to the NEW HD, because I have grub installed in the master HD, since it's being shared with Windows.)
Thanks in advance!

I believe you can change mount points through the Gparted application.  The graphical interface is very handy for that.  As for your /home directory, I believe that can be changed in user preferences.

Also, after properly formatting the drive, you could try editing fstab manually to map the mount point, etc.  Be careful with fstab, though, or you could have some serious issues.  To do it this way (which I like, because it feels 1337) takes a few steps.

First, find out where that new HDD actually is.
```
ls /dev | grep sd
```
This should output a list something like "sda sda1 sda2 sdb sdb1," though this will vary depending on how many harddrives you have and how they are partitioned.  anything "sda" will be your boot disk.  So for example's sake, sdb is your new hard drive; this makes sdb1 the primary partition.

Next, you need to create a new mount point.  I like coming up with nonsense names, that way I have something to curse at when I break it down the road.
```
sudo mkdir /media/nonsense
```
After that, you're going to need to map your drive to that point.  This will vary slightly depending on what filesystem type you used for its primary partition, so be sure to read the man page for mount, first.
```
sudo mount -t ext3 /dev/sdb1 /media/nonsense
```
So now you have your drive.  But wait!  It doesn't show up on startup!  That's where fstab comes in.  First, get the UUID of the partition on your drive (I do this the lazy way and right click the drive -> properties -> volume).  Make sure to note this!  next, 
[CODE]sudo cp /etc/fstab /etc/fstab.bak
sudo nano /etc/fstab
OR
sudo gedit /etc/fstab[CODE]
It looks a little messy, but follow the guide at the top, entering your new drive into the bottom.  For "Device Name" use that UUID (I have successfully used /dev/sdb1, but this may not work if on boot the OS chooses to map, say, a USB drive to sdb1 first.  The UUID is unique, and will always work). Hit tab, or space, and for "Mount Point," enter your /media/nonsense.  Repeat for "Type" (this will be the fs type, the same value you used after "mount -t"), "Options" is optional, and you can use just "0" for "Dump" and "Pass".

I just did this last night, and forgot a "-" in my UUID.  That made Ubuntu rather cranky on the next boot, as it couldn't find the dev to run a FSCK on.  So, make sure the UUID is exactly the same =-)

---

### Post by mb_webguy on 2008-09-04
> **forestpixie said:**
> Or you could use it as a data storage and add it to fstab, easily accomplished.

+1

This is by far the simplest method (assuming you're adding the second drive to your system as your post seems to indicate rather than replacing your old drive), and I don't see that moving various directories to this new drive would necessarily provide any concrete advantages.  After all, your total storage (old HD + new HD) is the same, regardless of how you use it.

---

### Post by aqui_c on 2008-09-05
> **mb_webguy said:**
> +1

This is by far the simplest method (assuming you're adding the second drive to your system as your post seems to indicate rather than replacing your old drive), and I don't see that moving various directories to this new drive would necessarily provide any concrete advantages.  After all, your total storage (old HD + new HD) is the same, regardless of how you use it.

Hi!
Yeah, my situation is: I have a HD with Ubuntu and Windows. The Ubuntu partition has almost no free space. So I thought in adding a new HD, just for Ubuntu. If I added and mount it, and change things in fstab, **Ubuntu will know how to use that space**?

If I continue to add things to my /home directory, for example, or to the /usr, will it begin to fill my new drive?

---

### Post by Elfy on 2008-09-05
Yep - install the harddrive in the pc, install gparted in your ubuntu

```
sudo apt-get install gparted
``` use it to format the drive, then add it to fstab.

I did the same the thing yesterday for someone else - 

[http://ubuntuforums.org/showpost.php?p=5720510&postcount=5](http://ubuntuforums.org/showpost.php?p=5720510&postcount=5)

---

