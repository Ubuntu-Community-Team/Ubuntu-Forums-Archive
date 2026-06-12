---
title: "cd/dvd drive won't mount"
date: 2011-05-15
forum: Hardware
---

### Post by desert dweller on 2011-05-15
I can't get a CD or DVD to mount in my iBook G4. I'm using Ubuntu 11.04. If I restart the computer with the CD in the drive, it will mount most of the time, but not always. When I insert a CD in the drive and try to mount it, the drive grinds, but the CD doesn't mount. When I try to mount it in terminal mode, I get this response.

---------------------------------------------------------

$ sudo mount -t auto /dev/cdrom /mnt/cdrom
password: 
mount: mount point /mnt/cdrom does not exist

$ mount /dev/cdrom
mount: can't find /dev/cdrom in /etc/fstab or /etc/mtab

-----------------------------------------------------------

When a CD does mount and I eject it, the image of the CD remains in the places menu. When I insert another CD and click on this image, I get the following error message:

Error mounting: mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Does anyone know how I can fix this?

---

