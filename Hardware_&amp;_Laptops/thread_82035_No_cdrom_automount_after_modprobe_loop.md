---
title: "No cdrom automount after modprobe loop"
date: 2005-10-25
forum: Hardware &amp; Laptops
---

### Post by toorima on 2005-10-25
I  do the following

sudo modprobe loop
sudo mount image.iso /media/iso/ -t iso9660 -o loop

The image mounts fine but the cdrom won't automount, everything else automounts, usbmemory, external hdd etc. 
After a "rmmod loop" the cdrom automounts again. Can't find anything about it either here or on google.

/etc/fstab entry for cdrom
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/etc/mtab when image mounted
/media/hda3/static/image.iso /media/iso iso9660 rw,loop=/dev/loop0 0 0

/etc/mtab when cd mounted
/dev/hdc /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=toorima 0 0

---

