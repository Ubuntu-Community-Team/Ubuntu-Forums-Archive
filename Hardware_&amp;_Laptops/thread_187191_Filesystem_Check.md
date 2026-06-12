---
title: "Filesystem Check"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by leetcharmer on 2006-06-02
When booting up Dapper after installation, it keeps complaining when it gets to the part about checking filesystems.  It states that the boot sector didn't match up with the backup FAT32, or something similar to that -- and then says it will not automatically fix it.  The only FAT32 filesystem on the machine is the external Firewire HDD.  Can anyone tell me how to check the filesystem for errors?

---

### Post by rumli on 2006-06-02
I had the same problem.  It turned out that Dapper was not mounting my FAT32 partition correctly.  To fix this, run:

sudo gedit /etc/fstab

Then replace the following line:
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
with:
/dev/hda1       /media/hda1     vfat    iocharset=utf8,umask=000 0       0

Note that you might need to replace the occurences of "hda1" above with something else (e.g., "hdb2", etc.) depending on the disk and partition number of your FAT32 partition.

---

### Post by gray-squirrel on 2006-06-08
[QUOTE=rumli]I had the same problem.  It turned out that Dapper was not mounting my FAT32 partition correctly.  To fix this, run:

sudo gedit /etc/fstab

Then replace the following line:
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
with:
/dev/hda1       /media/hda1     vfat    iocharset=utf8,umask=000 0       0

[/QUOTE]

Thanks.  Dapper no longer complains about my FAT32 partitions when booting up.  It appears to boot faster than previous editions of Kubuntu.

I had no idea that [Windows ME used Unicode for file names]("http://www.linuxplanet.com/linuxplanet/tutorials/4232/2/").  I thought the file names were all in ASCII, just like back in the days of MS-DOS.

I checked my [FONT="Courier New"]/etc/fstab[/FONT] entries from my previous Kubuntu installation (Hedgehog), and the [FONT="Courier New"]iocharset=utf8[/FONT] was missing.  Actually, it was never there to begin with.  I'm surprised that I was able to get away with not including the utf8 part for more than a year.  For the past two weeks when [FONT="Courier New"]dosfsck[/FONT] was running, it encounter problems with long file names.  Hopefully, I can run [FONT="Courier New"]dosfsck[/FONT] on the Windows partitions later and it will not pick up any errors.

---

