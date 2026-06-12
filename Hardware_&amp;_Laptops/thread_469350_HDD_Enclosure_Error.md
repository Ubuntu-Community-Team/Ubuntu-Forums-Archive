---
title: "HDD Enclosure Error"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by pavpan on 2007-06-09
I have an enclosure on which Dad keeps all his files. His CPU started overheating lately, and so his computer is down. However, he is a WinXP user and I have Ubuntu FF 7.04. When I plug in his NTFS formated enclosure into my computer (I know, I know, stupid M$ with their stupid NTFS) I get an error saying that I can't mount the drive named Enclosure. I can still, however, read other NTFS drives perfectly. The drive works perfectly within Windows (Vista). And before you ask, I have no information whatsoever about the drive other than that it connects through USB 2.0. I've tried enabling/disabling write support for external devices in NTFS Configuration tool, but to no avail. Any ideas?

---

### Post by gotmonkey on 2007-06-10
It sounds like a permissions problem. If you run in terminal $sudo nautilus can you access the drive? I have had issues with mount points in the past, I might have something to do with the naming of the drive. The easiest way I can think of rename the drive in windows environment and then try to connect to the linux system. Another this to make sure you check, do you have "enable write support for external devices" checked in ntfs-config? 

If you used automatrix to install the ntfs support, uninstall the ntfs portion of the program. I had problems with it working properly. If you are using feisty, enable universe in the repos and install ntfs-config that way. 

hope this helps.

---

### Post by pavpan on 2007-06-24
Actually, none of that helped but booting with the enclosure inserted fixed all the problems. I can now unplug it and replug it whenever I want.

---

### Post by gotmonkey on 2007-06-26
glad that it is working for you, sorry that I wasn't much help

---

### Post by pavpan on 2007-06-27
Just needed a bit of trickery with ntfs-3g...;)

---

