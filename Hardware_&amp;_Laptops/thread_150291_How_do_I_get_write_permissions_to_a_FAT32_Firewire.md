---
title: "How do I get write permissions to a FAT32 Firewire external?"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by Twilight Lamentation on 2006-03-25
Hi,
I managed to get write permissions to the FAT32 partition of my internal harddrive by editing fstab, but the same thing won't work for my (300GB) FAT32 external. It'll mount and give me read permission, but no write permission.

Here's what I've got in fstab:
/dev/sda1       /media/EXTERNAL vfat  iocharset=utf8,umask=000 0       0

That's pretty much the same thing I did for my internal FAT32 partition, and it worked for that partition.

I'm pretty sure something's wrong w/ the hardware somewhere between my external drive, the enclosure, and my computer, because it will sometimes just spontaneously unmount itself (it did this in Windows too), so could this have something to do with why I can't get write permission even while it is mounted?

And does Ubuntu have a drive scan it can run to determine if it's a bad harddrive (as opposed to a bad enclosure)?

thanks

Edited to add: At some point or another when I tried to mount and it failed, here's what I got:
FAT: filesystem panic (/dev/sda1)
fat_get_cluster: invalid cluster chain (i_pos 0)
file system has been set read-only
ls: system volume information: Input/Output error

---

