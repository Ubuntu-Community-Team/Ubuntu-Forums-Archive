---
title: "Ubuntu says my Mass Storage Device is a CD-R"
date: 2010-12-27
forum: Hardware
---

### Post by Robert1995 on 2010-12-27
Got a new device for christmas, it's a photo keyring thing which you have to add pictures too and charge via USB. When in Connect mode the device is meant to appear as a storage device on your computer. When connected, Linux makes no effort to show it's connected... It's not even noticeable at the Computer.

It is however visable in my Disk Utility...
Peripheral Devices > CD Drive (buildwin Photo Frame)

It's 8.4MB capacity and not partitioned.

I have also tried going to the directory of /dev/sr1 which says is not a folder.


Anyway to make linux think this is a Mass Storage Device, (which it is...... or should be)???

---

### Post by Fafler on 2010-12-27
Open a terminal and type:
```
tail -f /var/log/messages
```

Connect the photo frame and post the output here. Also, try mounting the photo frame with
```
sudo mount /dev/sr1 /mnt
```

---

### Post by Robert1995 on 2010-12-27
I used
```
sudo monut /dev/sr1 /mnt
```

to get this error:
```
mount: block device /dev/sr1 is write-protected, mounting read-only
```

I don't understand, this is new out of the box lool :P

---

