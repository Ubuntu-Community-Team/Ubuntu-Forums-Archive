---
title: "newbie problem with filesystem, out of space, make it bigger?"
date: 2008-09-24
forum: Hardware
---

### Post by samuraitor on 2008-09-24
hi!

I just figured out that my file system drive has runt out of space. Now I have a harddrive of 320 gb, with vista installed as well.

I would like to know if there is any possible way to make my current filesystem partition in Ubuntu bigger without the need of formating and stuff?

---

### Post by justsomedude on 2008-09-25
If there is free, unallocated space next to your Ubuntu partition, you can grow it.

If not, you'd probably have to shrink your Vista partition first.

You can do this with gparted from a live CD.

**Be careful! This is risky, so a full backup of all your data is a must!!!**

Before you shrink your Vista partition, be sure to set the size of it's pagefile to zero (temporarily) and defrag two times. 

Also, you might want to read up on how to reinstall GRUB from a live CD first, as it can happen that your system won't boot afterwards.

If you post the output of 

```
sudo fdisk -l
```

we can have a look at your current partition table.
Good luck...

---

