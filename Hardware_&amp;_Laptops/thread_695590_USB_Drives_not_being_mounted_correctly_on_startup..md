---
title: "USB Drives not being mounted correctly on startup."
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by tws on 2008-02-13
Hello.

First off, i am not too savvy with all the things. I got all i know from needing to know it for a certain task, so my knowledge is limited.

To the problem:

I use my second PC as a " storage hub" (if you will) to keep all my big files.
Now, as it was my desktop machine before i bough a new PC, i just set it up from scratch.

I need it to mount my two USB Harddisks when it starts up. (please note, when the machine starts, not when the desktop env. is loaded, as i am not going to start it)

So, as they are always connected on /dev/sdb1 and /dev/sdc1, i entered them into /etc/fstab:```
/dev/sdb1       /media/usbhd1   vfat    rw,users,auto   0       0
/dev/sdc1       /media/usbhd2   vfat    rw,users,auto   0       0
```

Though, after starting up, /media/usbhd* are both empty. When i just use "mount /media/usbhd*" the drive is mounted correctly and everything works fine, which lets me assume the entries in the fstab are done correctly?

Also, if i execute /etc/init.d/mountall.sh, the drives are also mounted correctly. To make sure mountall.sh was executed properly on startup, i removed and re-set the startup links of the script using update-rc.d. Still no change.

Any ideas?

Thank you in advance.

---

### Post by collink on 2008-02-14
Apparently, the usb disks are not available by the time the mountall script runs.  Some googling suggests the proper ways to do this involve either [using the HAL hotplug system to mount the drives automatically]("http://www.nabble.com/How-to-mount-USB-drive-at-boot-time-td11774674.html#a11774674") or rebuilding your initrd boot image with all the modules needed to make the usb disks and vfat filesystem available earlier in the boot process.

The quick and dirty way is to add your mount commands to /etc/rc.local BEFORE the line that says "exit 0".  This script runs at the end of the boot process, so your disks should be available by then.

---

### Post by tws on 2008-02-15
Thanks collink.

Unfortunately, the quick and dirty way didn't work. :)

---

