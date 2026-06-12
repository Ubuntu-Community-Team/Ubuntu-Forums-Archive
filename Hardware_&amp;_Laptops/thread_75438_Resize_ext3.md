---
title: "Resize ext3"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by a monkey on 2005-10-13
How can I resize my ext3 filesystem partition so that I can test out another distro? I don't want to wipe out poor ubuntu just yet... I'm on a Mac, by the way, if that matters.

---

### Post by John.Michael.Kane on 2005-10-13
When you start the install it will give you the option to resize it for you.

---

### Post by iramhernandez on 2005-10-13
You can also look into this:

umount the filesystem (or boot from a rescue type disk)
use ext2resize to resize the filesystem

On fedora (this might work on ubuntu) you can resize while the filesystem is mounted by using ext2online.

You still have to resize the underlying partition.

I think you can do all of this using parted.  To do this safely, you will have to boot off a rescue disk or a live cd.

Warning... there's a good chance to screw things up.  Make sure you have backups.  By the way, in case you are wondering the ext2 commands work on ext3 filesystem.

Also,  I have used the listed commands to resize a system using LVM.  Your mileage may vary if you are using a regular partition.

---

### Post by meijing on 2006-05-03
On Breezy the command resize2fs worked for me. It was allready installed. 

Please note, this does not resize the partition but only the filesystem. If an ext2/3 filesystem for some reason is smaller than its partition, let's say hda1, you can grow it to occupy the complete partition by resize2fs /dev/hda1. Shrinking is also possible.

---

