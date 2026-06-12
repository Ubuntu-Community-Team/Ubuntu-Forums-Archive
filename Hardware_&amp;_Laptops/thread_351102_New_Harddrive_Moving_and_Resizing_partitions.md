---
title: "New Harddrive: Moving and Resizing partitions"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by click4851 on 2007-02-01
okay so I'm upgrading from an 80 gig to 160 gig hard drive, my 80 gig is /dev/hda and the 160 gig is /dev/hdd. I dd the 80 to the 160, but now I'm stuck with the partiton layout from the 80:

a   74    gig     hdd1   ext3           /boot
   2.89   gig     hdd2   extended      lba
    2.89   gig     hdd5   unknown
 and about 75 gig of unallocated space

I believe the hdd5 inside the hdd2 is my swap partition, and in the 80 gig it is at the very end of the drive, but on the 160 of course its in the middle. My original idea was to move it to the end of the 160 gig and resize the /boot partition to the remaining size. I tried gparted and parted and partimage and none will move the hdd2/hdd5 partition.  Partimage indicates that "the file system of (/dev/hdd2) is unknown and is not supported. I don't think I can just blow out the partition and resize the /boot partition to what I want and remake the hdd2/hdd5 partition where I want, can I? Is it too late to consider a different partition layout, Iknow one big partition is asking for trouble, or am I way past that at this point?

---

### Post by click4851 on 2007-02-01
ok once I told gparted hdd5 was linux swap space, I could move it. dragged it one side at a time down to the end. So now hdd2/hdd5 is down at the end of the drive. Now to resize hdd1, when I attempt to resize I get a ef2fcsk error. I might try a live cd and boot from that and try again.

---

### Post by click4851 on 2007-02-02
ok now thats what I'm talking about, downloaded the Gparted LiveCD and booted that, bingo, all moves possible and complete, and that LiveCD very good look, obvious gnome tilt of course, but very intuitive tool, and help docs as well. Writing this, after I physically swapped drives, and have the 160gig as master. gotta love stuff that works.

---

