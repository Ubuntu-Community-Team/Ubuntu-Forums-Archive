---
title: "Ubuntu 18.04 not support 4tb(as 3.6tb) hdd with gpt table"
date: 2019-08-29
forum: Hardware
---

### Post by volodymyr-oliinyk-name on 2019-08-29
Hi 
I have Ubuntu 18.04 whitch dont recognize 4tb hdd (gpt ntfs external in usb dock station) , recognize it only as 2tb unformated drive. Ubuntu support other ntfs drives.
And at the same time Windows 10(installed  at this laptop too) recognize this hdd as 3.6tb normally formated drive ready for using.
What I need do with ubuntu for supporting of this drive?

Hardware:
One laptop(ubuntu 18,windows 10)
One usb dock station + internal 4tb hdd (gpt ntfs)

Thank you

---

### Post by TheFu on 2019-08-29
If Windows doesn't close the NTFS file system between reboots, then Linux will refuse to open it.  Fast Startup or Fast boot is a Windows setting to check. [https://www.howtogeek.com/243901/the-pros-and-cons-of-windows-10s-fast-startup-mode/](https://www.howtogeek.com/243901/the-pros-and-cons-of-windows-10s-fast-startup-mode/)

Some older external docks don't support larger disks. I've never seen one that worked in Windows and didn't work in Linux too.

If the partition will be for Unix-only use, best to format it using a Linux filesystem.  In Linux, drives and partitions are NOT used interchangeably.  Partitions have file systems, not drives.

---

