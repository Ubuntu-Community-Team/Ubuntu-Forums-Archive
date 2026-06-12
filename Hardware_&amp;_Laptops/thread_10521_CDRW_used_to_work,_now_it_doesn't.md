---
title: "CDRW used to work, now it doesn't?"
date: 2005-01-08
forum: Hardware &amp; Laptops
---

### Post by MarcDM on 2005-01-08
I installed Warty with one CDRW (TDK 12x4x24x), then a couple months later it was replaced by a regular CD-ROM. 

I kept the CDROM in the PC for about 3 weeks, then I replaced it with a newer (32x10x40x) TDK brand CDRW. 

All three CD-Rom/RW drives were connected to secondary ide as master (/dev/hdc).

It all worked well, until I decided I was gonna read the man page for cdrecord. I made a few changes to my system and since then things haven't been the same. 

1. I added hdc=ide-scsi to the boot string (is that what it's called?) 
2. I removed the symlink /media/cdrom that points to /media/cdrom0 
3. renamed /media/cdrom0 to cdrom and changed the mount point in /etc/fstab to point to /media/cdrom .

Nothing worked. 
No more burn:/// when I insert a blank CD. No more auto-mount and put an icon on the desktop. Can't burn CDs. Can't play CDs. It didn't even find /dev/hdc.


Thinking that I could just undo what I did, I removed the hdc=ide-scsi from the boot-string,  replaced the symlink (/media/cdrom -> /media/cdrom0) and replaced the mount point in /etc/fstab like it was. 

I can now read CDs (I get the file listing, haven't tested much else), but nautilus still won't allow me to burn. 

Any ideas on how I can fix this? Anyone can tell me what I did wrong?

Thanks.
  :oops:

---

### Post by MarcDM on 2005-01-09
I figured that my current /etc/fstab listing would be useful :

$ cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy  auto    rw,user,noauto  0       0
/dev/hda5       /mnt/sue        reiserfs rw,user,exec   0 0
/dev/hda2       /mnt/linfat     vfat    rw,user,noexec,umask=0,auto     0      0
10.0.3.1:/opt/docs /mnt/kag     nfs     rw,user,noexec,auto     0       0
10.0.3.1:/netshare /mnt/netshare     nfs     rw,user,noexec,auto     0       0

---

