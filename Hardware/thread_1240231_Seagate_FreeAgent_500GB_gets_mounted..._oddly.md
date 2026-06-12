---
title: "Seagate FreeAgent 500GB gets mounted... oddly"
date: 2009-08-14
forum: Hardware
---

### Post by uziel on 2009-08-14
I have purchased a 500G Seagate FreeAgent drive without previously checking on the Internet how much pain it is causing to the Linux users. As I am now starting a thread here, obviously I am no exception to this; anyway as far I have searched the forum, my exact problem wasn't covered anywhere yet.

After battling with the device for a day a few months ago I executed the sdparm magic that 'fixes' the spindowns of the disk. All other hardships remained however; I had to let it go for a time, but now summer came - what better time to delve again in some delicious hard/software debugging?

The behaviour breaks down like this:
1) When plugged in, the disk gets mounted automatically. Read-only, however, and at the mountpoint /media/usb0 although it has a label 'SG500'.
2) When I try to unmount it by Nautilus, operation fails with the following explanation: 'Device to unmount is not in /media/.hal-mtab so it is not mounted by HAL.'

And I would like the disk to behave basically as an USB stick - to get automounted, too (ideally at the mountpoint /media/SG500, but this is a minor detail), but in read-write mode and a possibility to unmount from the GUI. It would be logical to force HAL to mount the device, but I have no idea how to do it.

The disk has been reformatted to ext3, and I'm running Jaunty. I'd be happy to disclose some helpful information.

---

