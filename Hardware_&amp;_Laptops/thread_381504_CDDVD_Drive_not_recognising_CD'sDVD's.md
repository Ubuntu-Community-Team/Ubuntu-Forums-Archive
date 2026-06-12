---
title: "CD/DVD Drive not recognising CD's/DVD's"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by Rednut on 2007-03-11
I realise this is somewhat of an odd problem, mainly due to the fact that a google and forum search have uncovered few people that share it. My CD/DVD writer (a Samsung 'Writemaster') simply won recognise any CD's I put in it, despite the fact I actually installed Ubuntu off a CD.
Whats happening exactly is that I put a CD in the drive, go to Computer, click on "CD-ROM  1" and get the message:

> "Unable to mount the selected volume."
> Show more details

When I click on more details, I get:

> "mount: special device /dev/hdb does not exist"

It repeats this behavious for data discs, audio cds, and dvd's. Are there any drivers I need to install, or anything I need to do to get it working?

---

### Post by DagMan on 2007-03-11
Is hdb the mount point in your fstab file that maybe it's wanting to mount it there but it doesn't exist?
Perhaps if the problem is indeed that there's a place a device for your drive and it's just not being used correctly, you can find the correct one by looking around for it.
ls /dev/hd*
and see if there's /dev/hdc or hdd or something
ls -l /dev/cd*
and if there is a /dev/cdrom symlink, see what it is pointing at.  If you do have a /dev/cdrom /dev/cdrw /dev/dvd or so forth, as symlinks, just using one of them as the device to be mounted might be enough.
If you need that explained a bit more step by step then just say so.

If that isn't the problem then I can't help but for the next person who comes along, maybe you can describe if you've tried anything from the threads you've searched so things can be narrowed down more.

---

### Post by Rednut on 2007-03-14
> **DagMan said:**
> Is hdb the mount point in your fstab file that maybe it's wanting to mount it there but it doesn't exist?
Perhaps if the problem is indeed that there's a place a device for your drive and it's just not being used correctly, you can find the correct one by looking around for it.
ls /dev/hd*
and see if there's /dev/hdc or hdd or something
ls -l /dev/cd*
and if there is a /dev/cdrom symlink, see what it is pointing at.  If you do have a /dev/cdrom /dev/cdrw /dev/dvd or so forth, as symlinks, just using one of them as the device to be mounted might be enough.
If you need that explained a bit more step by step then just say so.

If that isn't the problem then I can't help but for the next person who comes along, maybe you can describe if you've tried anything from the threads you've searched so things can be narrowed down more.

Sorry, but could you please explain a bit more? I'm new to Ubunutu and Linux in general, and I'm struggling a bit with all the technical aspects:/

EDIT- I just checked inside my Dev folder and found no mentions of cdrom, cdrw, dvd or cd. However, there was a 'cdrom' in the folder a step above (root folder?). This folder has a normal folder icon with an arrow pointing diagonally upward and left over the top of it, and has nothing inside.

---

