---
title: "mount trouble with usb external hard drive"
date: 2009-01-14
forum: Hardware
---

### Post by snuffler on 2009-01-14
Hello,
       I have a Western Digital My Passport 320Gb external USB hard drive.When I plug it into the USB port of my Ubuntu 8.10 computer I get a cycle of mounting and unmounting that continues until I unplug the drive.I see the icon for a brief time as it is mounted,nautilus comes up briefly showing the contents and then seems to navigate to the parent folder.The drive appears to unmount at that point with the desktop drive icon disappearing and an error message saying cannot find media "diskname" .Then the cycle begins again.The drive works on windows.Unfortunately I seem to have corrupted some of the software it came with whilst using gparted,however the same problem was occurring before that point as well.Any help would be greatly appreciated.
I might add that the problem was the same when wine was installed and not installed so it is probably not caused by some software being run off the drive.

---

### Post by snuffler on 2009-01-15
Just an update if anyone is interested.I have been able to use the external hard drive with knopix ,format it and then use it successfuly in ubuntu for a while.Whilst copying some files over to it an error was produced on the external drive and the original problem started again.So this leads me to think that errors on the external hard drive are helping to cause the odd behaviour.Not an ideal situation still as it would be nice to get a correct error message and have some simple way to fix it.
Now I am wondering ,is it possible that the file copying process is somehow flawed or is it more likely the product may be defective?

---

### Post by cdtech on 2009-01-15
If you could at some point during the mounting and unmounting right click and unmount the device. If you can get it to unmount but remain plugged in you could try and mount it within the /mnt directory instead.

If it's unmounted find the device with "sudo fdisk -l", create a directory within the /mnt directory to mount the device. At this point we can look within the device to determine the cause.

As long as it continues to mount and unmount using HAL, it can be difficult to determine the cause as to why it does this. It could be HAL itself and not the device.

---

