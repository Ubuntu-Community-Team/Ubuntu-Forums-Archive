---
title: "Edgy &amp; FAT32 USB drive with several users"
date: 2006-12-13
forum: Hardware &amp; Laptops
---

### Post by aweller on 2006-12-13
I am trying to mount a FAT32 USB drive so that several users can have access to it. I have added the following line to my /etc/fstab:

UUID=6853-5BA9 /media/LACIE vfat users,owner,rw,umask=000 0 0

and when I switch it on, I get the following in Nautilus:

error: mount point /media/lacie is already in /etc/fstab
error: could not execute pmount

I tried creating a /media/LACIE folder with 'chmod a+rwx', but when switched on it bypasses this and creates a /media/LACIE-1 folder!?

Am I missing something here? Also, is it possible to convert this drive from FAT32 to ext3 without formatting or screwing my data up?

Thanks, Andy

---

### Post by bapoumba on 2006-12-13
[http://ubuntuforums.org/showthread.php?t=311816]("http://ubuntuforums.org/showthread.php?t=311816")
May be that thread will help you.

---

### Post by aweller on 2006-12-13
Unfortunately not, I still get:

error: mount point /media/lacie is already in /etc/fstab
error: could not execute pmount

Having deleted the line

UUID=6853-5BA9 /media/LACIE vfat users,owner,rw,umask=000 0 0

from fstab it mounts fine for me as user. But if another user tries to access the USB drive, they can't. There's got to be a permissions thing somewhere...

---

### Post by aweller on 2006-12-14
OK, I used GParted to create an ext3 partition (/dev/sdc2) on this external drive (allowing me to slowly migrate for better permissions management). So:

*I logged in as a different user and switched USB drive on.
*It mounts as /media/usbdisk.
*The user had no permissions, so I 'chmod a+rwx /media/usbdisk'.
*User can create folders, etc.
*I copied a small folder for testing.
*Re-logged in as me.
*I cannot alter this music folder (copy, cut, etc)! (I guess this a permission thing, that is, only creator can do this?!)
*I tried to access stuff as a second user - it finds the folder, but NO files!
*I also cannot copy stuff into the other-user-created 'Music' folder.

Is it possible to be more flexible with the permissions allowing all users to read/write data to/from it? Perhaps this is a fstab thing?

Also, I use several usbdisks on this machine (flash drives, etc) - is it possible to create a fstab entry that mounts this drive permanently as '/media/xyz', with these relaxed permissions?

Thanks, Andy

---

