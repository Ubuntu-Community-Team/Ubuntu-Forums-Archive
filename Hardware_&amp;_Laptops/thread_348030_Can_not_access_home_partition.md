---
title: "Can not access home partition"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by pirast on 2007-01-28
Hi!
I have a big problem:

I tried to create a LVM volume with lvcreate /dev/hda1 (/dev/hda1 is my home partition).

Since I was not able to mount my hard disk anymore, I executed lvremove /dev/hda1 and hoped that eveything would be like it was before.

But still, I can't mount my home partition:

> cramfs: wrong magic
VFS: Can't find ext3 filesystem on dev hda1
FAT: bogus number of reserved sectors
mount: you must specify the filesystem type


Fdisk says this:

> /dev/hda1 1 19457 156288321 83 Linux

/dev/hdb2 1 9535 76589856 83 Linux

As lv* did not work for a long time, my data should still be physically there.

But the questions is, how can I mount my home directory again?


Thanks for your help,
Martin

---

### Post by pirast on 2007-01-28
Yay! I love Linux! Without hope, I run e2fsck /dev/hda1..

Now it works (again)

*dance*

Martin

---

### Post by wxnker on 2007-01-30
I think I love you! 

I had lost access to my home partition and I was seconds away from re-installing when I saw this post.

Now I can access ubuntu again and everything is still there. I get a couple of weird errors though so now I have to fix them. Better than doing a clean install though :) 

I hope I can fix the rest with the help of this forum.

Ironically I lost contact to "home" while trying to setup another harddrive for backup lol :mad:

---

### Post by pirast on 2007-01-31
Nice :guitar:

---

