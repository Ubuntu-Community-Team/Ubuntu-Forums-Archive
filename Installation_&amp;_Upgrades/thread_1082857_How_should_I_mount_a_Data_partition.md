---
title: "How should I mount a Data partition?"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by glo on 2009-02-28
Hi there,

On every Windows system I set up, I leave one partition out. Drive C: is where I install Windows and drive D: is where I keep data files (songs, movies, backup images, etc). The reason behind this is that if and whenever the system should fail, I won't have to go through hell to restore it - only extract the backup image into place.

How should I go about doing it on Ubuntu?
I could set one partition to be mounted as root, but where do I mount my data partition?

One thing though - my data partition must be shared, so if I choose to install another operating system I should be able to access the data.

Thanks!

---

### Post by peakpc on 2009-02-28
In Ubuntu as with all unix/linux partitions are treated as folders and can be mounted (or unmounted) very simply.

 If your data partition is a segment of the same drive as your ubuntu is on then (assuming it's formated ext3,fat,or Ntfs) it should show as what ever name you gave it.

You must unlearn windows preconceptions and then Linux is so easy.

---

### Post by lordharsha on 2009-02-28
You can choose to mount it in any empty directory. A good choice would be to mount it under a directory in /media or /mnt. For example, if the data partition is sda2, you could choose the mount point to be something like /media/sda2 or /media/data. It's been a while since I've had to install ubuntu, so I'm not sure where this option is during the installation, although it shouldn't be too hard to find though. Just make sure that the partition is _not_ being formatted during the installation.

If ubuntu is already installed, simply add an entry to /etc/fstab

> /dev/sda2    /media/sda2    vfat    users    0    0

You might have to play around with the options (users) to get it to mount with the right permissions.

---

### Post by glo on 2009-02-28
Oh that's exactly what I am afraid of.
Having mounted the data partition, how will I make sure my permissions are really permissive and let me share the data with other users / operating systems?

---

### Post by lordharsha on 2009-02-28
First, accessing the drive from other operating systems will depend on that operating system, not ubuntu. If you have windows installed, the drive will be accessible from it irrespective of the permissions in ubuntu (as long as it is a compatible filesystem, like ntfs or fat).

That said, I think rw,users,auto should do the trick. That way, it'll be mounted with read/write permissions for all users during boot up.

If that doesn't work, add [umask]("http://en.wikipedia.org/wiki/Umask")=0111. That should give all users on the system read and write access to the drives. If you must have execute privileges on the drive, make it 0000.
If you're the only user, 0137 is probably a better option. R/W for you, R for users in your group, and no access for anyone else. Again, if you need execute privileges, 0037 will do the trick.

---

### Post by glo on 2009-02-28
Ok, thanks!
That should do.

---

