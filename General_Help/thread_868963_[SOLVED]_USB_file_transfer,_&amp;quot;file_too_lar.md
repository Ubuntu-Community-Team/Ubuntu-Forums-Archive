---
title: "[SOLVED] USB file transfer, &amp;quot;file too large&amp;quot;"
date: 2008-07-24
forum: General Help
---

### Post by suprfish on 2008-07-24
I recently made a backup archive of my hard drive. When I tried to transfer it onto an external hard drive (USB), it transfered 4 gigs of it and then quit with the message "File too large." How can I transfer the entire archive over (total 9.6 gb)?

Thanks

---

### Post by coffeecat on 2008-07-24
The USB drive is formatted with the FAT32 filesystem which has a maximum filesize of 4 GB. Reformat it with NTFS (which works perfectly well with Ubuntu Hardy) or ext3.

**Edit:** What file type is the archive? Is it .tar.gz? I believe there's a way of splitting tar.gz tarballs.

---

### Post by tamoneya on 2008-07-24
I agree with the FAT32 analysis but wanted to clarify on your options of NTFS and ext3.  You can use either as support has gotten better for NTFS in linux and there is [fsdrivers]("http://www.fs-driver.org/") for windows.  So ultimately you could pick either but I recommend that you pick NTFS if you are primarily windows and ext3 if you are primarily linux.

---

### Post by suprfish on 2008-07-24
> **coffeecat said:**
> The USB drive is formatted with the FAT32 filesystem which has a maximum filesize of 4 GB. Reformat it with NTFS (which works perfectly well with Ubuntu Hardy) or ext3.

**Edit:** What file type is the archive? Is it .tar.gz? I believe there's a way of splitting tar.gz tarballs.

Right right right; yes (.tgz). How do I split it?

---

### Post by insane_alien on 2008-07-24
if i were you i'd format the drive. FAT32 is more than a little obsolete these days. it is also inefficient on drives larger than 32GB

---

### Post by coffeecat on 2008-07-24
> **tamoneya said:**
> I recommend that you pick NTFS if you are primarily windows and ext3 if you are primarily linux.

Interesting point, but I would modify that. Now that NTFS read-write is reliable in Linux, as a single user of my systems I would choose NTFS over ext3 for external drives any day, precisely because NTFS does **not** support Linux permissions. Ext3 is a damn nuisance for the single user imho. If you have an ext3-formatted external drive it will be automounted only with root privileges. Which means that you have to create a folder (as root) for the ordinary user and then chown it for the ordinary user, or chown the mountpoint (which is not a particularly good idea). Although NTFS mounted files are owned by root (if you look at properties), by  the magic of ntfs-3g, the ordinary user can read, write, delete, modify or do what they like with them. Another advantage for me is that NTFS can be read by (but not written to) Mac OS. I've used NTFS to transfer large files from Linux to my Mac Mini.

---

### Post by timcredible on 2008-07-24
i would stay away from ntfs and use ext3.

---

### Post by suprfish on 2008-07-24
[http://ubuntuforums.org/showthread.php?t=824052](http://ubuntuforums.org/showthread.php?t=824052)

---

