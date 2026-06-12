---
title: "GParted cannot resize linux partition"
date: 2012-03-08
forum: Hardware
---

### Post by several ingredients on 2012-03-08
System specs: Acer Aspire 5738Z, Ubuntu 11.10 with GParted. 320GB hard-drive. (GParted is confused, the total of all partitions is 426GB, but the manufacturer's sticker clearly says "320GB HDD".)

I had allocated 10GB to Ubuntu during the installation a year and a bit ago. I thought that I could have a copy of any file on my windows partition, so I wouldn't need it on the Ubuntu one. But that recently has been too much of a hassle, so I've decided that I'd extend my linux partition, I'm supposed to have 320GB and I've hardly used any of it!

But, with hard drive partitions, there are always roadblocks and safety features etc. So of course, it won't be as simple as resizing the Windows partition, extending the linux one... *sigh*

I've attached a screenshot of Gparted. 
PQSERVICE is Acer's built-in factory restore partition, I don't want to touch that.
System Reserved is reserved for something... Probably for bootloading so I definitely don't want to touch that.
The first ACER is my Windows 7 partition.
Now it gets confusing, I distinctly remember setting up 10GB for the ubuntu partition. Yet I have an "extended" file system of 128GB and an "ext4" partition of 19GB
The unallocated space (44.5GB) is how much I want to add to the Ubuntu partition of 10GB (or however much there is).
The second ACER is my Windows 8 consumer preview (Tri-booting ftw!)
The last unallocated is a meaningless 2.5MB, and cannot be touched in any way.

The "ext4" partition, which I assume contains Ubuntu, is right next to the unallocated space on the hard drive. Doesn't this mean I can join the two together because of that? But when I right click on "ext4" no options come up. So how do I extend the ext4 partition to have that extra 44.5GB of space?

---

### Post by sikander3786 on 2012-03-08
Welcome to the forums! :)

For resizing a partition, you first need to un-mount it. And you can't un-mount the Ubuntu system partition obviously. So, you need to boot an Ubuntu Live CD or a USB and then GParted will happily resize it for you. ;)

---

### Post by several ingredients on 2012-03-08
Oh, I see. But then I thought there were tools for windows partition editors to read .ext4 formatted drives, but EASUS Manager doesn't seem to let me do that to Ubuntu, even though it recognises the space it takes up. I'll try a live USB then. Thanks!

---

### Post by several ingredients on 2012-03-08
Oh, I see. But then I thought there were tools for windows partition editors to read .ext4 formatted drives, but EASUS Manager doesn't seem to let me do that to Ubuntu, even though it recognises the space it takes up. I'll try a live USB then. Thanks!

---

### Post by several ingredients on 2012-03-08
Oh, I see. But then I thought there were tools for windows partition editors to read .ext4 formatted drives, but EASUS Manager doesn't seem to let me do that to Ubuntu, even though it recognises the space it takes up. I'll try a live USB then. Thanks!

---

### Post by several ingredients on 2012-03-08
Oh, I see. But then I thought there were tools for windows partition editors to read .ext4 formatted drives, but EASUS Manager doesn't seem to let me do that to Ubuntu, even though it recognises the space it takes up. I'll try a live USB then. Thanks!

---

### Post by bohemian9485 on 2012-03-09
Use _[Gparted Live CD]("http://gparted.sourceforge.net/livecd.php")_. Created a USB boot drive using_ [Unetbootin]("http://unetbootin.sourceforge.net/")_with the live cd[URL="http://unetbootin.sourceforge.net/"].
[/URL]

---

