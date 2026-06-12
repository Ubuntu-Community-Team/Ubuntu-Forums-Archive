---
title: "Permission problems with USB mounted windows share"
date: 2008-10-06
forum: Hardware
---

### Post by houdodu on 2008-10-06
i've got a usb mounted external drive formatted for ntfs that was previously used for windows XP.

i've mounted it a few ways, including: 

sudo mount -t ntfs-3g /dev/sdf1 /media/disk

most of the files can be read fine, but files that seem to have the "hidden" windows flag on are not able to be read, by root or otherwise. 

for example, i can read

/media/disk/file.txt

but i can't read

/media/disk/Documents and  Settings/c/file.txt

how can i mount this properly?

---

