---
title: "External HDD Permissions"
date: 2007-02-15
forum: Hardware &amp; Laptops
---

### Post by arbulus on 2007-02-15
I have a 500GB external hard drive attahed to my HP Netserver E60 running Ubuntu.  The ubuntu machine is used as a file server for my LAN.  I wrestled with this for some time, but I seem to be spinning my wheels. 

The external HDD was originally attached to my iMac G5 running OS X.  But when I got the ubuntu box, I wanted to attach it to that machine for centralized storage space.  When I first moved it over, Ubuntu wasn't able to write to it.  It could read it and copy from it, but not write to it. I tried chmod and chown, but it would tell me that it was a "read-only disk" and wouldn't change the ownership or permissions.  So, I backed up everything on it and reformatted it in ext3 format.  It could then read and write to it, but it wouldn't allow file names with non-alphanumeric characters.  I have 100GB worth of stuff on there, so going back over everything and changing the file names is not an option.  So I tried formatting it fat32, but then Ubuntu wouldn't even recognize the drive.  So, I plugged it back into my iMac and formatted it HFS with journaling turned off.  I then plugged it back into the Ubuntu box.  Ubuntu could now see it and read/write, but I still had the file name problem.  So, I made a few empty files on the drive, just so ubuntu would know that it belongs to it, then I plugged it back into the iMac and copied may backup back to the drive.  Everything worked wonderfully!  I plugged it back into the ubuntu box and could then read/write and could share it with the iMac via Samba with full read/write permissions.

Everything was going fine until i had to reboot the ubuntu box. It seems to have spontaneously changed the HDD's permissions.  Now I'm right back to where i started:  no read/write permissions for ubuntu or the iMac, and chmod and chown won't change it's permissions.  It's just locked the thing down and I can't do anything with it.

Does anyone have any suggestions on how I can make ubuntu own the drive with full read/write permissions and allow it to be shared to the iMac via Samba with full read/write permissions, and it be permanent and not change when I reboot?

---

### Post by kidders on 2007-02-16
Hi there,

> **arbulus said:**
> When I first moved it over, Ubuntu wasn't able to write to it.The filesystem (presumably HFS+) may have been journalised.

> **arbulus said:**
> So, I backed up everything on it and reformatted it in ext3 format.  It could then read and write to it, but it wouldn't allow file names with non-alphanumeric characters.Strange. Ext3 imposes almost no file naming restrictions.

> **arbulus said:**
> I tried formatting it fat32Unfortunately, this is an extremely inflexible filesystem. :-(

> **arbulus said:**
> Everything was going fine until i had to reboot the ubuntu box. It seems to have spontaneously changed the HDD's permissions.Was the mount   handled in /etc/fstab? (Perhaps you'd specified some strange options.)

> **arbulus said:**
> Does anyone have any suggestions on how I can make ubuntu own the drive with full read/write permissionsFilesystems don't work that way. They store things like ownership using UID numbers, that are OS dependent. If your users' IDs differ from one OS to the next, this will cause you problems.

---

### Post by arbulus on 2007-02-16
Problem solved.

I didn't have the drive correctly configured in the fstab. 
I just started from the beginning.  I reformatted the drive ext3, then set up the mount point and configured the fstab.  Evertyhing is working well now!

Thanks!

---

### Post by kidders on 2007-02-16
Excellent. Using HFS+ would give you OSX interoperability though. Its permissions management is (on the surface at least!) identical to Ext3.

---

