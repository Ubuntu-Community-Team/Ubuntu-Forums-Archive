---
title: "I still need windows for usb flash drive / memory stick support"
date: 2009-09-12
forum: Hardware
---

### Post by gwm on 2009-09-12
Hi,
Ubuntu recognizes my memory stick right away. however, it frequently corrupts the file system. Then I have to dual boot back to windows to reformat it.
eg 1. delete some files - unmount device - asked if want to clean out deleted files - answer yes - corrupts file system.
eg 2. copy new version of directory structure onto device - asks about merge, skip etc. - select merge all - unmount - removed device - plug back into usb slot - nothing.  windows however, at least recognized the device and told me it was not formatted.
Ubuntu has no means for formatting the device (or for changing its label). For that I still need to dual boot to windows.

---

### Post by argosreality on 2009-09-12
Does it corrupt the file system when you reboot with the device plugged in or just randomly when its connected? Have you tried using gparted to format/rename the device?

Also, more hardware specs wouldnt hurt to see if its a bug that has been fixed or if a but report should be issued

---

### Post by gwm on 2009-09-16
Thanks for the interest.
I was copying some files from a laptop running Jaunty 64 bit. When I plugged into this machine which is a desktop running Hardy 32 bit, Ubuntu failed to even recognize that the device had been plugged in. I took it back to the laptop and it too, failed to even recognize that it had been plugged in. Windows at least recognized it was there.
I have gparted on my system but never thought to use it. However, how can you work on a device that isn't there (hasn't been recognized)?
I've just plugged it in now, but can't see any hardware info under properties. System Monitor doesn't tell me anything either.

---

### Post by gwm on 2009-09-16
I have just used Gparted to look at the device. It appears to me that any attempt to change the name in the label of a partition involves wiping the partition clean - primary and secondary parts. This is not a good solution. Why?
As an example, my Windows XP partition had no name and therefore appeared to Nautilus as "29Gb Media". I had to reboot to Windows, right click the C drive and under properties, I simply renamed it to "Windows XP". Back in Ubuntu, I now have a meaningful name for the partition. Gparted doesn't seem to be able to rewrite only a part of the label, The way it looks to me, is that it creates a new one from scratch and hence, destroys the partition's contents (and I don't feel inclined to experiment on a live machine full of data to check this theory out).

---

