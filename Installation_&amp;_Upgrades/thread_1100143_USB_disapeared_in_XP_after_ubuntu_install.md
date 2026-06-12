---
title: "USB disapeared in XP after ubuntu install"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by zephoid on 2009-03-18
I just installed ubuntu on my 16gb flash drive thinking it would be a convent thing to have to carry around files and also have an OS on it. The problem is now XP will not assign a drive letter to the USB. under the hard drive management, the USB shows up, but it does not give me the option to assign it a letter. Is there a way to get XP to see the USB file structure?


Also, when i boot to the USB it will not allow me to access the USB under computer. it shows up as a disk, but will not allow me to mount it. Im guessing its because its already in use as the boot drive, but this also complicates things as now i cant see the file structure on the USB. any work-around?

---

### Post by cariboo on 2009-03-19
Windows doesn't play well with other operating systems. You won't see the USB drive unless you use a third party driver like [this]("http://www.fs-driver.org/index.html").

Jim

---

### Post by zephoid on 2009-03-19
ah, thank you. that was what i was looking for. too bad it conflicts with my driver that makes windows think USB drives are local drives instead (and easily partitionable). looks like i'll have to go rescript that... fun....

---

### Post by zephoid on 2009-03-19
edit: er.. now that i have drive letters, it is requiring me to format the drive in order to access it. even after i removed my other usb driver. any suggestions?

---

### Post by dandnsmith on 2009-03-19
It occurs to me that the reason you couldn't assign a drive letter was because the filesystem on the usb wasn't either NTFS or FAT.
Another possibility is that you have it partitioned using a partition format which Windows doesn't understand.

I did have a problem with a 4G stick which worked fine as a single filesystem device, but Windows lost track as soon as I partitioned it (standard, Windows compatible stuff).

I don't have a real solution - still feeling my way with this sort of compatibility problem.

By the way, the fact that it's the boot drive shouldn't stop you seeing the files - you won't be able to mount it, as it is already mounted.

---

