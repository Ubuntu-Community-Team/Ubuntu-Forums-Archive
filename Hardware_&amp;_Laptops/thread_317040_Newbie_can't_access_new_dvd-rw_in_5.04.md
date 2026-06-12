---
title: "Newbie can't access new dvd-rw in 5.04?"
date: 2006-12-11
forum: Hardware &amp; Laptops
---

### Post by Odyssey1942 on 2006-12-11
I just put a new dvd-rw in my computer (as slave) along side the LG CD-ROM already installed (as master). In Places/Computer I can see the CD-ROM (which opens properly if I put a CD in it) but cannot see the DVD-RW. (FWIW, a floppy also shows, but this computer doesn't have a floppy?)

In Device Manager I can't find either of them. 

In /dev I find links to both the cdrom (as well as a cdrom1 and cdrw - but not sure what these might be) and a "dvdrw" (as well as a dvd). Properties (for the dvdrw) shows the link target as 

/dev/hdd

so I assume that the dvdrw is assigned as hdd since the cdrom link target is shown to be /dev/hdc. (FWIW, the link target for each of CDROM1,CDRW, and DVD is also /dev/hdd so I also assume that each of those functions is all part of the new DVD-RW drive. am I on the right track here?

From similar experience with a USB memory device, I now assume that I need to mount it, but am unsure how to go about this and my googling isn't turning up anything useful. Any guidance appreciated. TIA

---

### Post by Odyssey1942 on 2006-12-12
If I have posted this in the wrong forum, will someone please advise?

Perhaps I should have said is that what I am having trouble with is actually finding the dvdrw. If I knew where it is, I think I can get it mounted.

---

### Post by Odyssey1942 on 2006-12-12
Also here is contents of fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Should the dvdrw show up in fstab? Or if so, will it show only after it is mounted?

---

### Post by dancavs on 2006-12-14
hi

i too am having issues mounting a cd burner.

from what ive gathered so far is that your fstab file must have an entry for your dvd drive if you want it to mount automatically on bootup - something like

```
/dev/hdd /media/dvdrw auto rw,user,noauto 0 0
```

hope this helps

---

### Post by PriceChild on 2006-12-14
I would just like to point out that 5.04 has reached the end of its life and is no longer supported.

---

### Post by Odyssey1942 on 2006-12-29
Dancavs, I too understand that the clue is in fstab, Finding anything in there is a daunting task however, and I have not yet figured out how to limit the search to just hd* related. 

I assume that the new DVDRW will be set up as a hd?, but if this is not the case, please sort me out.

PC, Yes, because of this and the new features, I want to upgrade to 6.06, or maybe by the time that I am ready 6.10 will be stabilized. The thing is that I need to get /home backed up to a DVD so that I can partition the new Ubuntu install to include one for /home. That way I can just do a new install without worrying about my /home folder. But the DVDRW doesn't show up on the desktop or the device manager, so I need to find it so I can mount it and then figure out how to use it. Hence this post.

Or maybe there is a quicker way. Can I use fdisk to repartition the existing hdd to add one partition, and will it do the repartition with free space, so nothing is lost? If not, what is the simplest way to create a new partition so that I can just copy the existing /home directory over to the new partition?

---

