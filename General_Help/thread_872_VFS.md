---
title: "VFS"
date: 2004-10-16
forum: General Help
---

### Post by jeremy on 2004-10-16
I have installed ubuntu and the disk (sda1) is formatted with the reiser fs. I am using the 2.6.8.1-3-686-smp kernel and all is well, except that, when booting I get a message saying;
   VFS - Can't find ext3 filesystem on dev sda1
this is followed by a delay of some 5 seconds, then it says;
   mounting a tmpfs over /dev
then the boot continues and all is well.

I think it is clear what is happening, but I do not know why, or how to fix it, can any one help? 
TIA

---

### Post by Damon on 2004-10-16
Could there be something wrong in your /etc/fstab file? Could you post it for us?

---

### Post by jeremy on 2004-10-16
I don't think that that is the problem, but here it is;

proc /proc proc defaults 0 0
/dev/sda1 / reiserfs defaults 0 1
/dev/sda5 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/hdb /media/cdrom1 udf,iso9660 ro,user,noauto 0 0
/.dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0

---

### Post by bdoetsch on 2004-10-16
got the same problem here as well! 
my fstab looks like this:

proc            /proc           proc    defaults        0       0
/dev/hda1       /windows  ntfs    rw,suid,dev,exec,auto,nouser,async,umask=022        0       0
/dev/hda5       /               reiserfs defaults        0       1
/dev/hda7       /home           reiserfs defaults        0       2
/dev/hda8       /opt            ext3    defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

---

### Post by triad169 on 2004-10-16
This is covered in the Ubuntu Bugzilla:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=2100](https://bugzilla.ubuntu.com/show_bug.cgi?id=2100)

Triad

---

### Post by jeremy on 2004-10-16
Ah, thanks for posting the link, I must confess, I haven't figured out how to use the bugzilla yet!

---

