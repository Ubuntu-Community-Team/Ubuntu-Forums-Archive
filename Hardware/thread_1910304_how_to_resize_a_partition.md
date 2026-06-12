---
title: "how to resize a partition"
date: 2012-01-16
forum: Hardware
---

### Post by new to linux help needed on 2012-01-16
how would i resize a partition for another OS. do i need to run a program from a live cd/usb??? please explain. and thank you in advance! also i only have one partition at this moment

---

### Post by Xgen on 2012-01-17
Tons of information....google 'gparted live'. Even videos:

[http://www.youtube.com/watch?v=-sq3PBzplYg]("http://www.youtube.com/watch?v=-sq3PBzplYg")

As you might know, you can't partition a drive within the partition (has to be unmounted) so a dvd/cd/flashdrive is necessary. The video should include the necessary steps (through windows I believe) but the gparted iso file can be imaged with unetbootin if in linux(sudo apt-get install unetbootin). Can take a while to resize a partition with data on it.

Best to browse and learn a bit so you don't accidentally format your data.

---

### Post by Mark Phelps on 2012-01-17
> **new to linux help needed said:**
> how would i resize a partition for another OS. 

IF this "other OS" is Vista or Win7, and the partition is the one containing the OS, do NOT use any Linux utilities to resize it.   Vista/Win7 are very finicky about their OS filesystems and do not do well when those are tampered with from "outside".  This can result in filesystem corruption, rendering the Windows OS unbootable.

If it's a Vista/Win7 box, use the Windows Disk Management utility to resize the OS partition.  That is primitive and clumsy to use, but it won't damage the filesystem.

---

