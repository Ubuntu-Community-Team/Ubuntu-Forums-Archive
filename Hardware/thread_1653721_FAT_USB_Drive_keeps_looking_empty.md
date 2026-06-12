---
title: "FAT USB Drive keeps looking empty"
date: 2010-12-27
forum: Hardware
---

### Post by woodsby on 2010-12-27
I've had an issue with a 2TB fat usb hard drive for a couple releases now.  After a while of idle time, the hard drive starts appearing empty.  If I navigate to it through nautilus, CLI, or http, it looks like there is nothing on the drive, although the available free space is listed accurately.
When this happens, I have to umount then mount it again, and all goes back to normal.  This is really annoying as I am trying to use this as a web directory, but everytime I try to pull it up on the web, I have to ssh in and umount/mount.  Anyone else seen this problem and know how to fix it?  I've searched everywhere.

---

### Post by vanadium on 2010-12-27
You should never have a file system as large as 2 TB formatted as vfat.

---

### Post by mcduck on 2010-12-27
> **woodsby said:**
> I've had an issue with a 2TB fat usb hard drive for a couple releases now.  After a while of idle time, the hard drive starts appearing empty.  If I navigate to it through nautilus, CLI, or http, it looks like there is nothing on the drive, although the available free space is listed accurately.
When this happens, I have to umount then mount it again, and all goes back to normal.  This is really annoying as I am trying to use this as a web directory, but everytime I try to pull it up on the web, I have to ssh in and umount/mount.  Anyone else seen this problem and know how to fix it?  I've searched everywhere.

That sounds like your hard drive might have some built-in power save feature.

I know how annoying that can be, I have a 1TB Western Digital drive with similar feature, which can't be turned off, and I simply can't keep it connected all the time as the drive will power off after a while, and has to restart every time I open a file browser, file section dialog or anything like that. And it takes a good couple of seconds to spin up...

---

### Post by nerdy_kid on 2010-12-27
> **vanadium said:**
> You should never have a file system as large as 2 TB formatted as vfat.

+100

use ntfs or ext!!

---

### Post by mcduck on 2010-12-27
> **nerdy_kid said:**
> +100

use ntfs or ext!!

...unless you actually need to be able to access the drive using some other device than a computer, in which case FAT is often the only option. ;)

---

### Post by woodsby on 2010-12-27
This did the same thing when it was an NTFS partition.  I changed it to fat because i occasionally plug the drive into my mac, and the only free ntfs drivers I could find for mac handled large copies very slowly.  Regardless, I thought vfat(fat32) has capability of handling much larger than 2TB partitions???
I thought it might be a power save functionality of the disk as mcduck mentioned.  If this is the case, does anyone know how to wake up the drive, or keep it awake?

---

### Post by mcduck on 2010-12-27
I don't know any smooth way to do it, but perhaps a small script that would read a very small file from the drive every now and then. Anything that accesses the drive without actually causing much input/output should work for keeping the drive awake.

..if that works then at least you'd know that the problem is caused by some built-in power save feature that kicks in when the drive is idle too long. :)

---

### Post by woodsby on 2010-12-27
For that matter, i could add to that script that if the file is not found, umount then mount.

---

### Post by Yellow Pasque on 2010-12-27
What kind of drive is it? It may be possible to disable this "feature" via the manufacturer's software tools.

---

