---
title: "Devices are not automounting"
date: 2009-01-26
forum: Hardware
---

### Post by spikespeigel42 on 2009-01-26
When I plug in an external USB harddrive, or put in a cd, or put in a flash card, the hardware performs like it normally would, and the devices show up in /dev, but I have to mount them by hand and they are always read only. I've tried reinstalling hal, and I even did apt-get remove --purge hal, which trashed my machine for awhile. This is becoming a major pain! Any help would be very appreciated.

---

### Post by nixscripter on 2009-01-26
Try plugging it in, let's say it mounts on /dev/sda, then run:

```
lshal | grep sda
```

To see if hal sees it, or if it's deeper in the system.

---

### Post by spikespeigel42 on 2009-01-27
lshal | grep sdb
  block.device = '/dev/sdb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1:1.0/host2/target2:0:0/2:0:0:0/block/sdb'  (string)
  block.device = '/dev/sdb1'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb7/7-1/7-1:1.0/host2/target2:0:0/2:0:0:0/block/sdb/sdb1'  (string)

is the output of lshal | grep sdb.

Also, if i mount a device by hand, and then remove it, and insert a new device, the letter is incremented, if thats any help.

---

### Post by nixscripter on 2009-01-28
Okay, that tells me hal can see the devices, which means it might be GNOME's problem.

Next time you put it in, you can run this command to see whether GNOME is having the problem or not:

```
gnome-mount -d **/dev/sdb** && echo $?
```

If the result is zero, it worked, and the disk should appear. If it's 1, then GNOME is having the problem... and I'm afraid my expertise stops there. :neutral:

---

