---
title: "Changing mount location of partition"
date: 2008-09-19
forum: General Help
---

### Post by governmentproj13 on 2008-09-19
When I was first installing Ubuntu, I had no clue where the best location for the second partition would be, so I just picked "/usr".  Several months later, I saw I was running out of disk space, and apparently I had only 1G left!  I checked my partitions, and realised all my stuff was under /home/username, in the root partion, not in the second partition.

I guess quite simply what I'm asking is
   
   :What's the best way for putting "/home" onto partition 2 and "/usr" onto partition 1, aka my root partition?

   :Could I just change the mount location in fstab from "/usr" to "/home"?  What would that do?  It's probably not that easy... but I thought I'd ask. XD

---

### Post by timcredible on 2008-09-19
well, if you do that, all your files would still be on the original drive.  so, what it sounds like you really want to do is to backup your /home data, copy it over to the /usr drive, then swap the mount points.  how you do the backup and restore is vitally important - you need to keep the file permissions intact.  so, do this to backup your stuff:```

su
tar -cvf /home.tar /home/*
cd /usr
tar -xvf /home.tar

```
that should create an exact duplicate of all users home directories in /usr (please check this before going on).

then, change the mountpoints in /etc/fstab and reboot.  the system should mount the old /usr as /home now and your user directories should be there and all will be good.

---

### Post by governmentproj13 on 2009-07-11
So, I did all that, but I ended up backing up to a NTFS partition, which I guess doesn't preserve certain special unix permissions.  In the end, I followed a how-two on restoring permissions and restored all of the default to /home and such, but now, whenever I log into machine, I can't do anything administrative wise, unless if I log into superuser in terminal.  This is really annoying, because I think because of this, my wireless won't start, and I can't adjust this from the menu bar because it won't let me adjust any settings (the screen requiring a password won't even show up, just a "denied" type message).  Anyone know how to fix this??

---

