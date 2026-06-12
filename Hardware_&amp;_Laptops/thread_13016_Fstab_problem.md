---
title: "Fstab problem"
date: 2005-01-28
forum: Hardware &amp; Laptops
---

### Post by steffen on 2005-01-28
I have an external (hotswap) disk for my laptop. I actually cold-swap it, but that's another matter.

I have the following line in my /etc/fstab: > /dev/hdc1       /home/steffen/Media     reiserfs        uid=1000,gid=1000,rw,defaults,umask=0002,noauto 0       1  for this disk. My *sudo fdisk -l* returns */dev/hdc1* as the location for this disk.

However, when I go to /home/steffen/Media I can't find any disk on it. When I copy files to Media, it takes up space on my hda1, instead of my hdc1, as it should.

When I *sudo mount -a* it returns no error. Why isn't this disk mounted on the correct place?

Moreover, my *computer:///* doesn't show any hdc1 disk.

The disk is parted in hdc1 and hdc2. I have the same problem for hdc2.

---

### Post by ba747heavy on 2005-01-28
Are you mounting the disk?  The disk will not automatically mount at boot time (the noauto option in your fstab line), so mount it with mount /home/steffen/Media

Also, I think that you will have to remove the UID and GID lines, as I think they don't do anything for a reiserfs partition (although I could be wrong).

---

### Post by steffen on 2005-01-31
Thanks!

Still doesn't work, though. I have removed the gid and uid, and also experimented with both noauto and mounting manually, and auto and just defaults.

The reason why I formatted the disk as reiserfs (I always opt for ext3, usually) is that qt_parted was not able to format the disk as ext3 - for some reason.

Usually - before - I've fixed the bad superblock...whatever problem with some value of umount=. After having tried a lot of them now, it doesn't seem to be working :(

---

