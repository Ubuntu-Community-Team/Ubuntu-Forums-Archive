---
title: "Happy joy how I hate windows"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by Maupertus on 2009-06-27
Hi everyone,

guess what I got from XP this morning? The reader_s virut trojan.
Basically after scouring google, everyone tells you to reinstall windows xp and format everything including partitions.

Now I want to have the same setup as I had before Uncle Bill's creation gave me this gift (although I was a bit ignorant when I opened the installer that had it) 

What's the best way to accomplish this, I've installed a couple of Linux variants, but I have to be honest, this is going to be my first XP re-install (on an eeepc to make things just a tiny bit more complicated) 

Will XP 'see' the swap and ext4 partition and can I format those, or do I need to boot into Ubuntu first, format the windows partition, boot XP from stick and install in the free NTFS partition?

I'm a bit stressed out because of the bug, so any help would be great!

Thanks in advance.

---

### Post by Michael.Godawski on 2009-06-27
Moved to Installation and Upgrades.

---

### Post by Maupertus on 2009-06-27
Sorry Michael, I thought Installation and Upgrades only applied to *nix

---

### Post by Blood//Stain//Child on 2009-06-27
XP will erase your Linux partition. You should install XP first, and then reinstall Ubuntu.

---

### Post by Maupertus on 2009-06-27
So I can just reinstall xp, all partitions will be removed (and thus the data formatted) and start from scratch without a problem?

---

### Post by merlinus on 2009-06-27
YMMV, but I do not think that xp will destroy your linux partitions.  Use gparted to make sure that you format the old xp partition as ntfs, and that it is a primary.

Then upon installing xp, do not allow it to use the entire hdd, but use the ntfs partition you have created.

---

### Post by Maupertus on 2009-06-27
> **merlinus said:**
> YMMV, but I do not think that xp will destroy your linux partitions.  Use gparted to make sure that you format the old xp partition as ntfs, and that it is a primary.

Then upon installing xp, do not allow it to use the entire hdd, but use the ntfs partition you have created.

Mmm, can XP servicepack 3 install to partitions? I always thought it was incapable of doing so. Again, forgive my ignorance, I've never had to install windows.

---

### Post by HappyFeet on 2009-06-27
> **Maupertus said:**
> Mmm, can XP servicepack 3 install to partitions? I always thought it was incapable of doing so. Again, forgive my ignorance, I've never had to install windows.

Yes, it can. You will have the option to choose which partition to use. Unless it is a restore disk. In that case, it wipes out the whole drive, thus you will lose your linux install.

---

