---
title: "Mounting DVD Drive"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by XDevHald on 2005-04-22
I currently have a DVD movie that I want to play, but it's not recognizing the DVD drive. based on that, it's also not mounted, the CDrom drive is, but not the DVD to where if you put a DVD in, it'll auto load the movie in Totem, or Mplayer , etc...

Is there a command I need to put into my fstab to make this load?

Great detail would be very much appreciated!
[b]

Here's my fstab[/b]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
[b]

And here is my mtab[/b]

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

---

