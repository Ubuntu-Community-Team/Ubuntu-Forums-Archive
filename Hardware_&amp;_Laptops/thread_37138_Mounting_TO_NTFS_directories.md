---
title: "Mounting TO NTFS directories"
date: 2005-05-26
forum: Hardware &amp; Laptops
---

### Post by pja on 2005-05-26
While I am new(ish) to Linux, I have managed to dual boot Ubuntu onto a second disk drive and can mount the WinXP (C:\) drive at boot time and it is then accessible.

The issue is that the mount is to the C:\ drive where I would like to mount to the **"My Documents"** directory on that drive.  I can navigate to it each time I want to access files from "My Documents" but it would be much easier if I could go straight to a "My Documents" mount point.

I have searched extensively for a solution and experimented with fstab settings but can't get it to work.

My fstab entry is:
/dev/hda1       /media/windows    ntfs    umask=0222      0       0

I would like to be able to use:
/dev/hda1/Documents and Settings/Peter Anderson/My Documents  /media/windows    ntfs    umask=0222      0       0

Does **MOUNT** support this or does it only mount to the volume?

Thanks in advance for any help.

Regards,
Peter   ](*,)

---

### Post by Burgundavia on 2005-05-26
You can only mount partitions with fstab.

Corey

---

### Post by bored2k on 2005-05-26
[QUOTE=pja]I would like to be able to use:
/dev/hda1/Documents and Settings/Peter Anderson/My Documents  /media/windows    ntfs    umask=[/QUOTE]
You could try, but Linux does not like Spaces between dir names. 
Documents and Settings would be Documents\ and\ Settings/

You could first try using the mount command + the dirname. If all goes good, copy it to your fstab.

---

