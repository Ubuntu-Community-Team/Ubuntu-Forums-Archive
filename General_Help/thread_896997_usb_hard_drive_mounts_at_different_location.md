---
title: "usb hard drive mounts at different location"
date: 2008-08-21
forum: General Help
---

### Post by afonteijn on 2008-08-21
I have a laptop and two usb hard drives. Depending on which one is connected and which one I turn on first the mount point changes.
Example: First 500gb hard drive mounts as /dev/sda5 - becomes /media/disk-1, second time I start up with the 70gb hard drive attached as well and the 500gb moves to /dev/sda8 - becomes /media/disk-2. 
Problem is that all the links to this mount point become unusable. My music collection isn't found, virtualbox can't find *.vdi files etc.

Is there a way to make sure that the 500gb hard drive always mounts at e.g. /media/500gb? I thought about adding it to the fstab, but the problem is that the /dev/sda# number changes as well.

Any help is appreciated, please let me know if I'm unclear about anything. Thanks!

---

### Post by becatlibra on 2008-08-21
If you look at the format at [http://ubuntuforums.org/showthread.php?t=590267](http://ubuntuforums.org/showthread.php?t=590267) you will see that you can use the fstab and actually specify a UUID so that it will know which device is which

---

### Post by becatlibra on 2008-08-21
OH - and to FIND the UUID of the device, simply plug each drive in, run mount to see which is mounting to where (or rather, what you are looking for is the /dev/sdxx)

Then use the command as follows

 sudo vol_id -u /dev/sdxx (replace the xx with the important information)

---

### Post by afonteijn on 2008-08-21
Thanks becatlibra. It works like a charm! I actually found the UUID by using the blkid command.

---

