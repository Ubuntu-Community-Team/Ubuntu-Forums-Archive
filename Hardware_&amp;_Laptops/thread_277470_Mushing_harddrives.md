---
title: "Mushing harddrives?"
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by Valencik on 2006-10-14
I'm curious if it would be possible to combine to partitions on one harddrive together without loosing any data. Upon installing Ubuntu I partitioned my 80gb harddrive into a 37 and a 43 with dual booting XP in mind. However, I now see no need to dual boot and would like to enlarge my main partition (the one Ubuntu is on, the filesystem) to the full 80gb.
Is this possible? It seems like it would be.

Thanks for your time.

---

### Post by kidders on 2006-10-14
Hi there,

The only (sensible) way of doing this is to copy the contents of one filesystem into the other, delete, and resize. Of course, this will cause you all kinds of grief if you don't have lots and lots of free space :-(

One option you might not have considered is making your old Windoze partition into a /home, or a /usr/local, etc ... or splitting it up even further, rather than trying to merge things together.

---

### Post by Valencik on 2006-10-15
Thanks a lot. I think I'll just leave it the way it is for now and eventually if I get fed up I'll just back everything up and reinstall. Thanks! :)

---

### Post by kidders on 2006-10-15
No need to reinstall, just to reorganise your filesystems! If you're going to do a backup anyway, you might as well use it to put *all* your files back.

---

