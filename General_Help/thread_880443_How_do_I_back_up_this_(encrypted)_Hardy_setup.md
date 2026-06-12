---
title: "How do I back up this (encrypted) Hardy setup?"
date: 2008-08-05
forum: General Help
---

### Post by MountainX on 2008-08-05
I have Hardy installed on a system with multiple HDDs. 

On the first drive (74GB) I have /boot (unencrypted) and / (crypto).
On the second drive (74GB) I have /var, /tmp and swap (all crypto).
On another drive I have /home (crypto too).

I'm currently backing up /home. However, I am not backing up the OS. I'd like a strategy for that. Ideally, I would like to be able to recover from a failure of either drive 1 or drive 2 without having to reinstall anything. 

Can I store an image of both drive 1 and drive 2 on my 1 TB drive? It would be nice to just boot from a live CD, copy the stored image to a new 74GB drive, put the new drive in, and be done. 

I would have to know how to make an image, restore an image, and I would have to be able to access the encrypted partition that holds my image from the live CD. Is all that possible?

How would I go about doing this? Thanks.

---

### Post by tamoneya on 2008-08-05
use the "dd" command to copy each partition byte for byte.
```
http://research.att.com/~gsf/man/man1/dd.html
```

---

### Post by MountainX on 2008-08-05
Thanks for the link.

In my case, to make the backup, would the in-file be this:
```
/dev/mapper/sda2_crypt (where my / partition is)
```

How would I specify an out-file as a file on a network drive? Assuming the network drive is mounted, would I use:

```
/media/MyShares/MyFolder/mybackupfile
```

To restore, what would I do? There would be a boot partition (no crypto) and a root partition on the new drive. I have no idea how to use dd to restore an encrypted partition.

Thanks for any tips.

---

### Post by tamoneya on 2008-08-05
you got the in file and out file correct.  To restore though you can just swap in and out to replace the partition.  You may want to schedule the command via cron to run daily or weekly.

---

### Post by tact on 2008-08-05
> **tamoneya said:**
> you got the in file and out file correct.  To restore though you can just swap in and out to replace the partition.  You may want to schedule the command via cron to run daily or weekly.

If you use the .img extension on the outfile dd will create a disk image at the destination, rather than wipe out everything on the destination drive and make it a clone of the input drive.

This way you could store images of both drives you want backed up on the TB drive.

Booting from a liveCD or liveUSB stick you could use dd to restore the original drive from the image (wiping out whats on the drive and replacing it with the contents of the image - assuming when you are booted from liveCD/USB your TB network drive is accessible)

However - if you ever want to be able to access files on the img or cloned drive after its created (e.g. to update the back up incrementally, or recover a file or two as opposed to a full restore) you may encounter problems:
When you use dd, or any other sector copier, windows or linux based, to create an image of a drive, or clone one drive to another, it also copies partition UUID's and (in the case of an encrypted drive, or one using LVM) it also copies VG and LV names.

UUIDs are meant to be "unique".  Volume Group (VG) names are also meant to be different for different devices.  So your running system will take a puke if you mount another drive (or drive image using the "mount -o loop ..." command) that has the same UUID's or VG names.

Before I started using disk encryption in ubuntu I used to keep a full clone (using dd) of my laptop's internal HDD - as I wanted to ALWAYS have a "ready to boot" option in case the internal drive suffered some disaster.  Its a 2 minute job to swap in/out the HDD.

To keep that clone updated I needed to connect it to my laptop regularly, mount the drive, and (g)rsync just /home to it to keep data up to date.

As noted above because of duplicated UUID's this is a problem.  There are some hoops to jump through but one can manually change UUID's on partitions and solve that little gotcha.

Since moving to disk encryption (as provided by the ubuntu alternate installer) I have found that its not just UUID's that need changing.  Also need to change VG name.  I have not yet dug deeper to find out if I can do this and so for now I cannot connect my cloned drive to update the backup.

The internal drive did have a disaster last week and I thought I was stuck with the only option being to swap drives in/out.   I would lose a few days work as the last cloning was a couple of days prior (it takes like 9hrs to clone 120GB drive!!! so its a PITA).

I did manage to restore the up to date data -  getting around the duplicated VG name problem like this:
-  swap drives (put the back up HDD inside the laptop, original drive in external enclosure
-  boot up laptop on (slightly out of date) HDD
-  attach the USB (original up to date) HDD to a DIFFERENT computer and share it across LAN
-  copy back /home across the LAN

---

### Post by MountainX on 2008-08-05
> **tact said:**
> If you use the .img extension on the outfile dd will create a disk image at the destination, rather than wipe out everything on the destination drive and make it a clone of the input drive.


All the info you posted was very helpful, but especially the part about the .img extension. Thank you!

---

