---
title: "CD does't show in File Browser"
date: 2009-02-11
forum: Hardware
---

### Post by John Seal on 2009-02-11
I've been using Ubuntu 8.10 for 6 days on Parallels on a MacBook and took the plunge yesterday to install on it's own bootable partition using a downloaded ISO. All went great and with a lot of suck and see I managed to repartition the HDD using "Parted". Was easy and quick and no data loss. :popcorn:

This community is great to learn from as are nearly other Linux Forums.:P

A wee problem I sorted and thought I'd post. Nearly twilight zone stuff!:confused:

If a DVD is left in the drive during a start or reboot of Ubuntu 8.10 the DVD is read OK but the data or disk size doesn't show in File Browser. Doesn't show in WinLin Pro Desktop either. After removing the DVD and rebooting all is OK. In WinLin Pro Desktop the DVD shows in My Computer but cannot be read (for me anyways). You can get to the DVD/CD via the "My Host Computer" option.:guitar:

---

### Post by nixscripter on 2009-02-14
The only thing I can think of is that the virtualization software isn't showing it the DVD drive as a drive for some reason.

See what the HAL daemon thinks. When the DVD is in, run this command: ```
lshal | grep CD
``` and see what the storage model is.

---

