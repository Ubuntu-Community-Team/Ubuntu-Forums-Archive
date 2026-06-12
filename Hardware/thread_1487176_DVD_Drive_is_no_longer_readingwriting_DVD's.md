---
title: "DVD Drive is no longer reading/writing DVD's"
date: 2010-05-18
forum: Hardware
---

### Post by Xalrons on 2010-05-18
After installing 10.04, my DVD drive was no longer recognised by the system.  If I try to go to places-->cdrom0, I get the message: Unable to mount cdrom0 mount: special device /dev/scd0 does not exist
My fstab looks like this:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=48848197-0109-4297-a06a-c8d57c5c6de7 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d9a6a029-162c-4c3a-853a-2261cd4321ec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by 2hot6ft2 on 2010-05-18
You might try this, it worked for another mounting/unmounting issue
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install systemsettings
```
then
1. On top menu bar goto System --> Preferences --> System Settings
2. A Systems Settings Window will pop-up
3. On the Systems Settings Window click on the 'Advanced' Tab (the other one is 'General')
4. On the section 'Advance User Settings' look for 'Removable Devices' and click on it
5. This will take you to Removable Devices - System Settings Window.
6. Click 'Enable automatic mounting of removable media' and Apply
:popcorn:

---

### Post by Xalrons on 2010-05-18
It didn't work, however, another thing that I noticed is that whenever I try to unmount the cd that appears, it states: Unable to unmount cdrom0 umount: /media/cdrom0 mount disagrees with the fstab

And this "cd" isn't actually a cd that I've inserted. It appears whether I have a disk inserted or not, and it's empty.

---

