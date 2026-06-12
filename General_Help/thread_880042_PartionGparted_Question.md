---
title: "Partion/Gparted Question"
date: 2008-08-04
forum: General Help
---

### Post by phimur on 2008-08-04
I am trying to set up a multiple boot system. I have a 250GB hard disk. I wanted to set it up with approx 100GB Ubuntu partition, 25GB vista, 25GB XP and then 100GB shared storage. When I went to format the 100GB shared storage(in gparted) I got a message saying that I had too many primary partitions. Is it possible to create the setup I described? If yes how? If not are there any recommendations?

---

### Post by Elfy on 2008-08-04
You need to use an extended partition -then use logicals for the buntu partitions (you need 2 - one for the install and one for the swap) and the shared, make the xp a primary partition.

Maximum of 4 primary - but lots of logicals in an extended.

---

### Post by coffeecat on 2008-08-04
Just to add to what forestpixie said - Windows XP **must** be on a primary partition with the boot flag set, otherwise it cannot boot up. XP cannot boot from a logical partition. I guess that would be true of Vista as well, but I have no experience of Vista.

Linux can boot from either a primary or a logical partition, which is why forestpixie suggested putting Ubuntu root in a logical partition.

My preference if I was setting your layout up would be XP and Vista in primaries, then one extended filling the whole of the rest of the HD, and three logicals inside the one extended, Ubuntu root, Ubuntu swap and the shared storage. Windows is OK with logical partitions for data.

One question? 100GB Ubuntu root partition? :shock: That's one helluva size. Are you sure?

---

### Post by ajgreeny on 2008-08-04
> One question? 100GB Ubuntu root partition? :shock: That's one helluva size. Are you sure? 	No problem if you don't have a separate /home partition.  My root partition is 120GB and includes my /home.  I personally find it much easier to keep everything on the same partition instead of having a separate /home.  It is so quick and easy to backup, which I do anyway on an external drive, and also quicker to install/reinstall on the single partition.  I realise that I'm probably in the minority here, but that's just the way I see it for my situation.

Incidentally, I have tried the separate /home way as well, but I found it much more difficult to work out the path to /home/username when moving files etc etc, as it was no longer what I expected and ~/path/to/file/or/folder did not always work for me; it does for most things, but occasionally I have seemed to need the full path, which then became /media/disk/path/to/file and was not nearly as intuitive, not to me, at any rate.  Perhaps I was not aware of some method or other to do all this.

---

### Post by coffeecat on 2008-08-04
> **ajgreeny said:**
> No problem if you don't have a separate /home partition.

Yes, but the OP is going to have a 100GB shared data storage partition as well. I just wanted to give him/her a chance to rethink it before committing.

I don't use a separate /home either, but for slightly different reasons. I multiboot and although I know how to deal with potential UID permission problems, I want to avoid the issues you might get when the config files in /home for apps work differently in different distros because of different versions. Like the OP, I've gone down the data partition route with symlinks from /home to the data partition, and I've never managed to fill a 15GB root partition, let alone a 100 GB one. :)

---

