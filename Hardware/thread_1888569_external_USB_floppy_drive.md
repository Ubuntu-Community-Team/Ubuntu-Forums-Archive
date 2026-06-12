---
title: "external USB floppy drive"
date: 2011-11-29
forum: Hardware
---

### Post by NikkiRuiz on 2011-11-29
I can't seem to get Ubuntu 11.10 to recognize my external USB floppy disk drive (Sony MPF82E-U1).  On Windows, it works as plug-and-play (no driver installation needed).  Do I need to install a device driver for Ubuntu?  I couldn't find anything on the Sony website about drivers.  How do I get Ubuntu to recognize the drive and load files from floppy disk?

---

### Post by dabl on 2011-11-29
Try a ```
sudo modprobe floppy
```

Also I found this on Kubuntu forums:  [http://kubuntuforums.net/forums/index.php?topic=3116533.0](http://kubuntuforums.net/forums/index.php?topic=3116533.0)

---

### Post by xtgyal on 2011-12-11
"sudo modprobe floppy" gives a fatal error, "error inserting floppy" "no such device"

I also tried "sudo mkdir /mnt/fd0" / "sudo mount /dev/fd0 /mnt/fd0" which returns "special device /dev/fd0 does not exist"

---

