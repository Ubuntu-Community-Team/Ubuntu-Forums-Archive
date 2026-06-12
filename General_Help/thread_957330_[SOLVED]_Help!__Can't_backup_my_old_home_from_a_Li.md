---
title: "[SOLVED] Help!  Can't backup my old /home from a LiveCD"
date: 2008-10-24
forum: General Help
---

### Post by boombox1387 on 2008-10-24
So I had [a problem with my UUIDs]("http://ubuntuforums.org/showthread.php?t=955073"), and I did exactly what you're not supposed to do when something goes wrong.  Instead of waiting for intelligent people to guide me, I messed around with things.  In an attempt to fix my problems, I installed the RC of Intrepid because I really wanted to try it out, and because I hoped that an upgrade would fix some things.

Instead...  at startup, the Usplash stops and runs a disk check every time I try to boot.  The disk check fails, tells me to run "fsck" manually, and gives me a root command line.  Before upgrading to Intrepid RC, I could skip the disk check and load a Failsafe GNOME.

I stuck in a live CD, hoping that I would just be able to copy my Home folder to my backup hard drive and reinstall.  Unfortunately, upgrading to Intrepid apparently added some level of protection to folders in my Home folder, and when I try to copy them, it tells me: "...cannot be copied because you do not have permissions to read it."

Can anyone help me backup all of my valuables so that I can reinstall Ubuntu?  Either that, or can anyone help me fix my UUID problems and failing disk checks?

---

### Post by scragar on 2008-10-24
open a terminal from the liveCD (or press alt+F2) and type```
gksu nautilus
```
this will open a the file manager with root perms which will give you rights to move the files

---

### Post by AndyCooll on 2008-10-24
Or rather:
```
gksudo nautilus
```
And when you do a re-install you might want to consider manually creating partitions and create a separate one for your /home.

That way if you ever do something similar you're unlikely to need to do what you're having to do now. You can just do a clean install, but you're /home partition will still be there.

:cool:

---

### Post by Elfy on 2008-10-24
Maybe it would also be worth fixing your fstab while you're in there then it will probably boot for you - but it's worth doing a backup while you're there as well :)

When scragar gets back I suspect (s)he'll change the command to either 

gksu or gksudo nautilus

---

### Post by scragar on 2008-10-24
> **forestpixie said:**
> Maybe it would also be worth fixing your fstab while you're in there then it will probably boot for you - but it's worth doing a backup while you're there as well :)

When scragar gets back I suspect (s)he'll change the command to either 

gksu or gksudo nautilus

ooh, missed that.

And gksudo is just an alias for gksu, so no reason to bother typing the extra 2 characters.

---

### Post by boombox1387 on 2008-10-24
See, that's the problem.  Root Nautilus still doesn't let me copy files, and root operations from a terminal don't work either.

```
sudo cp /media/disk/home/michael /media/SHARE/Backups/everything
```

gives the output: "omitting directory /media/disk/home/michael"

Opening Nautilus as root and trying to copy files still tells me that I don't have permission to access them.  Under the permissions tab, it lists Owner and Group as "1000."

Anyway, here's what worked:  As root, even though it still wouldn't let me copy files, it did let me change permissions on them.  I changed permissions on everything so that root had permission to copy it and I put it all on my backup drive.

@forestpixie:  You mention fixing the fstab as a possible solution.  The fstab points to a UUID that isn't listed when I run "sudo blkid."  If you would have tips for fixing my fstab, which would be very welcome, I'd recommend that we continue the discussion on my [original thread]("http://ubuntuforums.org/showthread.php?t=955073"), since the problem that I created this thread for has been resolved.

---

### Post by Elfy on 2008-10-24
Ok I did :)

---

