---
title: "Move from External HDD to Internal HDD"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by Xcmd on 2009-05-30
Currently I run Jaunty on an external USB-connected hard drive. This is nice, but I can feel a certain amount of throttling occuring due to the throughput issues that my internal HDD does not experience. At current my internal HDD has Vista. Much as I loathe Vista, I need to have Vista on my box to test software for myself and others (although not often). What I'd like to do is resize Vista's partition into 3 parts, MOVE my Jaunty installation over to the external partition and install Windows 7 on it as well.

Right now GRUB boot loader won't even respond to me if the external HDD isn't turned on, so I somehow also need to fix my MBR so that it reads this all from the internal drive. There's over 30 GIGs of data I don't want to have to replace and a bunch of settings I'd rather not have to go over again (it takes me about two days to get an Ubuntu installation working the way I want). Is there any way to resize Vista's partition, move Ubuntu to a new partition and install Windows 7 so it doesn't over-write anyone?

I'm thinking:

Resize Partitions
Install Windows 7
Use LiveCD to format 3rd partition ext3
Use LiveCD to move Ubuntu
Use my special CD for editing MBRs to point back to Internal HDD
Use external HD as storage as it was meant to be used

But at this point I'm not even sure what I need to be changing and where and whether or not I've even got the right idea. Anyone?

---

### Post by Mark Phelps on 2009-05-31
In terms of resizing the Vista OS partition, strongly suggest you do NOT use Ubuntu or a GParted LiveCD, or any other Linux utility, to resize it.  The safest way is to use the Vista Disk Management tool.  If you have problems shrinking the partition, see the following link for some tips:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

Also, before you start, make sure you have a Vista DVD lying around -- that's a retail or OEM DVD, not a vendor-supplied "recovery disk".  If you don't have one, you can use torrent to download an image from the NeoSoft forums.

If you can't get a Vista CD or DVD made, you're running the risk of not being able to recovery from a corrupted partition if anything goes wrong during the shrinking or installation.

At the very least, I would be sure to back off all your files and settings to an external drive before you start.

---

### Post by Xcmd on 2009-06-01
Sounds like a serious under-taking. Thank you, though, for the reply. I'll consider my next move carefully.

---

