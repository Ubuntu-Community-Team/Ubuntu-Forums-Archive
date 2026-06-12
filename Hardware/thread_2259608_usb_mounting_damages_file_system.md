---
title: "usb mounting damages file system"
date: 2015-01-05
forum: Hardware
---

### Post by danielsender on 2015-01-05
Hi,

I'm running 14.04.1 on a Dell Precision M6300. A few times, after removing a flash drive or an SD card (with an adapter) the file system is damaged, making it empty. I go through the unmounting procedure in the file browser. I'm wondering if is a hardware issue or some software (e.g. driver?). Is there any test program to check the health of the USB system? If is a software issue, how can be fixed?

Many thanks in advance.

Daniel

---

### Post by weatherman2 on 2015-01-05
Make sure the USB drive is really unmounted.  You can do it manually from a terminal with something like:

```
sudo umount /dev/sdb1
```

(Where sdb1 is the device name - may differ in your case.)

If that command returns immediately without error, it should be unmounted correctly.  Sometimes I get a warning (when doing it through the Gui/Desktop) that the device can't be unmounted at that moment.  Maybe you are getting the same response - but without the error notification.

Obviously, if the light on the USB device is flashing then something is being read/written on it so I would not remove it yet.

To attempt to repair a corrupt filesystem - for a Linux ext2/ext3/ext4 filesystem, anyway - you can try the e2fsck command.

---

### Post by danielsender on 2015-01-05
I was assuming that when I click on the up-arrow symbol and the disk entry name disappears it means that it has been unmounted, are you saying that even when that sequence of events happen, the disk may still be mounted?

---

### Post by yancek on 2015-01-05
You should see an icon in the panel on the left of the Desktop for eacg device.  Right click and select Eject.  The up arrow in the file manager moves you to the directory immediately above.  Not sure what you are referring to.

---

### Post by yancek on 2015-01-05
You should see an icon in the panel on the left of the Desktop for eacg  device.  Right click and select Eject.  The up arrow in the file manager  moves you to the directory immediately above.  Not sure what you are  referring to.

---

### Post by SuperFreak on 2015-01-05
In the file manager on the left column where discs and directories are listed there is an upwards arrow next to each mounted drive.

---

### Post by danielsender on 2015-01-06
> **yancek said:**
> You should see an icon in the panel on the left of the Desktop for eacg  device.  Right click and select Eject.  The up arrow in the file manager  moves you to the directory immediately above.  Not sure what you are  referring to.

That's the arrow I meant. Even after seeing that the name of the device  disappeared (as an indication that is unmounted), I found the filesystem  damaged. Fortunately fsck.vfat fixed it, but the timestamps and  original names were gone.

---

