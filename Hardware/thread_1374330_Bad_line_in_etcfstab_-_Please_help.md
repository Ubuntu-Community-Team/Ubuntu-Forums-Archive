---
title: "Bad line in /etc/fstab - Please help"
date: 2010-01-06
forum: Hardware
---

### Post by krlrvr on 2010-01-06
Hi to all.

I'm running Karmic(64bit) on a stock HP dv3-2155mx and I ran into this message the other day. 

Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 13 in /etc/fstab is bad
mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab

I googled around and became more confused.
 
I opened up /etc/fstab to find this
 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6572f122-cbb2-4afd-acb0-2228eaf5d3c2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4a333a52-f7a4-437b-b5af-7403021d6244 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0

Not sure of what to replace line 13 with and if that's all that I have to do.
Any help would be most appreciated.

Thanks in advance.

---

### Post by mikewhatever on 2010-01-06
The cdrom line looks odd.
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
```

needs to be just that
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

---

### Post by krlrvr on 2010-01-07
Hi[ mikewhatever]("http://ubuntuforums.org/member.php?u=160645")
That was it.:D
Works perfectly now.
Thanks for this.
:KS:KS:KS:KS:KS

Regards

- krlrvr

---

### Post by Jalke on 2010-01-22
I seem to have the same issue.  It won't read any cd's.  Here is my /etc/fstab file:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda5 during installation
UUID=06d55e08-7104-4429-8a6d-5d1a9c623087 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=96d338d6-9712-4c2e-b574-fc66d766b07b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto, exec,utf8 0 0
/dev/fd0 /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Any help would be greatly appreciated!

---

### Post by glássgost on 2010-02-08
I'm having the same problem. when I insert a CD, i get

Error mounting: mount exited with exit code 1: helper failed with:
mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab

etc/fstab says 

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=9b90d2fa-c1d9-4b59-929d-69766f2f89ff /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b8155b6e-ef5d-4c5c-9a2a-472e6cecdf91 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

