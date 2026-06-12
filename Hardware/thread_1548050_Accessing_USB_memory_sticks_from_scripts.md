---
title: "Accessing USB memory sticks from scripts?"
date: 2010-08-07
forum: Hardware
---

### Post by skewray on 2010-08-07
I find myself repeatedly doing the following tasks:

  Insert USB memory stick
  wait for the Device Notifier to pop up
  choose dolphin only so the device gets mounted
  delete annoying dolphin window
  run Makefile that copies project to/from /media/disk
  use Device Notifier to dismount USB stick
  wait for mysterious checkmark to clear
  Pull out USB stick

Is there some way to just get a makefile to mount the USB device?

Brian

---

### Post by skewray on 2010-09-08
bump

---

### Post by Fafler on 2010-09-08
The USB stick should use the same devicename every time, like /dev/sdb1. If for some reason it doesn't, you need to write a udev rule to map it to a specific devicename.

Add a entry to your /etc/fstab like

/dev/usb-stick /mnt/mountpoint defaults 0 0

Now, just add

mount /mnt/mountpoint

in the beginning of the makefile and

umount /mnt/mountpoint

in the end. Remember to rename /dev/usb-stick and /mnt/mountpoint accordingly.

---

