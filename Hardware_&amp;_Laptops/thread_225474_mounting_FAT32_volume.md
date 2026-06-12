---
title: "mounting FAT32 volume"
date: 2006-07-29
forum: Hardware &amp; Laptops
---

### Post by thatcoolrushguy on 2006-07-29
I have two hard drives; one of them, the master drive is 20 GB and has a 15 GB windows partition and a 5 GB Ubuntu partition. The other, the slave drive, is 120 GB; it has one FAT32 partition which I am trying to mount in Ubuntu so I can use it for storage in both Windows and Ubuntu (I need to be able to both read and write to it). I (unsuccessfully) followed the guide at:

[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

When I type 'mount /dev/hdb1' I get this message:

mount: unknown filesystem type 'fat32'

In the guide I followed, it showed how to mount an Ext3 volume; when I followed the guide, I just replaced Ext3 with FAT32. Is it necessary to format this drive as Ext3? 

Any help would be greatly appreciated. :D

---

### Post by stobor on 2006-07-29
'fat32' doesn't look like the label mount refers to for fat volumes.

if you run 'man mount,' and scroll down to the part where it describes the -t option, it lists the labels to use for the option.  'msdos' looked like the best option to me, and it worked on a fat volume I have.

 To be honest, I rarely use the -t option, it is pretty smart about choosing the right fs type.  have you tried it without the -t or with '-t auto' ?

---

### Post by stobor on 2006-07-29
whoops, i should have read your post closer before posting.  most of what i said probably doesn't help you much.  in any case, try changing 'fat32' to 'msdos' in your /etc/fstab file.  'auto' might work as well.

sorry for any confusion

---

### Post by dean.s.wood on 2006-07-29
Hi,

I do this too. I use the command 

mount -t vfat /dev/hda7 /mnt/shared

where obviously for me /dev/hda1 refers to the hard drive and /mnt/shared is a directory I have created on /mnt. Make sure that directory is created first or the drive will not mount.

Hope it is useful.

Dean

---

### Post by stobor on 2006-07-29
ah - vfat is the choice here.  vfat supports the long filenames and stuff, so its more compatible with win95+

---

### Post by thatcoolrushguy on 2006-07-29
> **dean.s.wood said:**
> Hi,

I do this too. I use the command 

mount -t vfat /dev/hda7 /mnt/shared

where obviously for me /dev/hda1 refers to the hard drive and /mnt/shared is a directory I have created on /mnt. Make sure that directory is created first or the drive will not mount.

Hope it is useful.

Dean

That fixed it, but it makes the drive read-only. How can I change the permissions to read/write? Thanks :D

---

