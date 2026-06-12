---
title: "Removeable disk problem"
date: 2007-08-02
forum: Hardware &amp; Laptops
---

### Post by bandreasen on 2007-08-02
I recently installed Ubuntu 7.04 on my desktop PC and have now connected a large (650GB) removeable hard drive to a USB port.  What's wrong?  It appears that all of the corect preference are checked in the removeable drives and media section but I can't find the drive.  Is there something I can add to the fstab or someplace else?

---

### Post by gyeti on 2007-08-02
You can plug in the disk and run a tail on /var/log/messages. There you should find a new SCSI device and the corresponding device name. You can try to mount the new device by hand. If you can't mount it, run "fdisk -l [device name]" to find information about the partition table and file systems on the disk.

---

### Post by bandreasen on 2007-08-03
I thought I'd try to add an entry to the fstab and mount this removeable disk when I boot.  However, the fstab uses UUID numbers and I don't know how to get a UUID number.  Can anyone tell me how and where to get a UUID number>

---

### Post by gyeti on 2007-08-03
I know that one can specify a device by a uuid but I'm not familiar with it. Anyway, there's no need to use uuid when you know the device name. Both are connected to the file system label and should be recognized automatically when you plug in the disk. No need to do any re-boot or stuff like this (this ain't Windows;-))

Anyway, could you plug in the disk and post the corresponding entries in /var/log/messages that pop up? Otherwise it would be hard to find out what's going on.

---

### Post by Larkshall on 2007-08-04
I use an external HDD plugged into the USB port. If the drive does not show in "Places" then go to your root directory and click on "media" and you should find it there. My Ext HDD is used on both Ubuntu and Windows computers, it was formatted as FAT 32 under Windows. It was named "DATA FILES".

---

