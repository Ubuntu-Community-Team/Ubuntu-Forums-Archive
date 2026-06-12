---
title: "Contents of /mnt"
date: 2008-08-03
forum: General Help
---

### Post by sofasurfer on 2008-08-03
The /mnt directory is where I mount my backup hard drive. When I open /mnt, I see the backup files I have on my backup drive. Now, when I unmount my backup drive and I save a backup file to /mnt, it goes into /mnt but NOT onto the backup drive. Then when I mount my backup drive and look at /mnt, I do not see the file I saved to /mnt with my backup drive unmounted. Why can I not see this file?

The reason for this question is that I have files in /mnt that where saved when my backup drive did not mount because of the issue where my drives are recognized by the wrong name (/dev/sda instead of /dev/sdb and vica versa). I had thought that I had this issue corrected but I guess not.

Sometimes when I open /mnt I see the files that were saved when the drive mounted correctly and sometimes I see the files that were saved when the drive did not mount correctly.

I hope this makes sense.

---

### Post by hal8000 on 2008-08-03
> **sofasurfer said:**
> The /mnt directory is where I mount my backup hard drive. When I open /mnt, I see the backup files I have on my backup drive. Now, when I unmount my backup drive and I save a backup file to /mnt, it goes into /mnt but NOT onto the backup drive. Then when I mount my backup drive and look at /mnt, I do not see the file I saved to /mnt with my backup drive unmounted. Why can I not see this file?

I hope this makes sense.


Your mount point can be controlled at boot by the contents of /etc/fstab or set manually e.g. sudo mount /dev/sda1 /home/user/camera

In your case you  have set the mount point as just /mnt and if your external hard drive is not mounted, then /mnt is just treated as an ordinary directory. This is the reason why Mounting your hard drive after files have been copied into /mnt are not visible.

You need to make sure the drive is mounted first then copy files.
You dont say if you are using fstab or using mount manually with the mount command.
You can tell if your drive is mounted using
df -hT

before copying any files across, hope that makes things clearer.

---

