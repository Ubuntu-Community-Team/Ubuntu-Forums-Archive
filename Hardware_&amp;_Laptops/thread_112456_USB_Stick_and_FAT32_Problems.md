---
title: "USB Stick and FAT32 Problems?"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by Avicus on 2006-01-04
I've noticed when I tried to copy data from a newly FAT32 formatted USB 1GB Stick in Ubuntu that the data is not able to copy to the local hard drive (I assume it is because the automounter program is assuming FAT16 for USB Drives?). Due to lack of time, I just reformatted the drive as FAT16 (in Windows) and went back on Ubuntu and the drive is then perfectly fine. I did not try to mount the drive manually.

Has anyone else noticed this anomoly using a FAT32 USB drive?

Please tell me!

---

### Post by hod139 on 2006-01-04
Not a solution, but I have been using a 512MB usb stick formatted fat32 without any problems.  I never had to mount the drive manually.  So, no, I have not encountered this anomoly.

---

### Post by psusi on 2006-01-04
Sounds like the memory stick was corrupted.  There is a bug in breezy where when you eject/unmount memory sticks  ( or other removable media ) from the desktop, the icon vanishes right away, but data is still being flushed to the disk.  Some devices have an led on them to indicate when they are active.  If yours does, make sure not to unplug it untill that light goes off, or you can corrupt the disk.

---

### Post by Avicus on 2006-01-05
It seems unlikely the drive got corrupt. I was able to mount in Windows fine and copy my data over and reformat and then copy back to it. The bug is good to note though, as my device does have an LED.

It seems more likely the automounter is loading my drive as FAT rather than FAT32. Is this possible? Where can I look up info regarding the automount thing, like what is the program called?

I'll do some testing when I get bored later :D

---

### Post by Amon_Re on 2006-01-05
[QUOTE=Avicus]It seems unlikely the drive got corrupt. I was able to mount in Windows fine and copy my data over and reformat and then copy back to it. The bug is good to note though, as my device does have an LED.

It seems more likely the automounter is loading my drive as FAT rather than FAT32. Is this possible? Where can I look up info regarding the automount thing, like what is the program called?

I'll do some testing when I get bored later :D[/QUOTE]

Plug it in, go to the console, and type mount
You should see a line for the stick & what FS is used

---

