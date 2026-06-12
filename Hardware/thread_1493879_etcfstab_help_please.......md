---
title: "/etc/fstab help please......"
date: 2010-05-26
forum: Hardware
---

### Post by phillyfandeal on 2010-05-26
Hello all, 

I am trying to get my Dell 720 printer to work in 10.04 and have  followed a great instruction guide; however I am now stumped. Here is my  /etc/fstab file that it tells me to put in the usbfs which I did;  however when I attempt to mount the usbfs its giving me an error.  Any  suggestoins?

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c05f9a32-3000-4b46-8d08-2b8eb3b9712c /               ext4     errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0


error output is mount: mount point /proc/bus/usb does not exist

Thank you in advance.

---

### Post by cariboo on 2010-05-26
> usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0

Is no longer used in Lucid due to the removal of hal, just comment the line out, or remove it from /etc/fstab.

To see if your printer is detected properly, open a terminal and type:

```
dmesg | tail -n10
```

just after you have plugged your printer in.

---

### Post by anglican on 2010-05-27
> **cariboo907 said:**
> Is no longer used in Lucid due to the removal of hal, just comment the line out, or remove it from /etc/fstab.

To see if your printer is detected properly, open a terminal and type:

```
dmesg | tail -n10
```just after you have plugged your printer in.
However, some older printer drivers (and some scanners I believe) depend on usbfs. There is a workaround see [here]("http://ubuntuforums.org/showthread.php?t=1493771&highlight=fstab").

H

---

