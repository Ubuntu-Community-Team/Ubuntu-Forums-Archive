---
title: "Mounting second hard drive"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by konnorrigby on 2009-06-26
I am running ubuntu 9.04 on a 40 gb hard drive. i put a 20 gb hard drive on it and now ubuntu see that its there but when i click on it to open it is says
 
unable to mount location
cant mount file.
 
so my question is how do i mount it or format it? ao i can use it as storrage.

---

### Post by starcraft.man on 2009-06-26
> **konnorrigby said:**
> I am running ubuntu 9.04 on a 40 gb hard drive. i put a 20 gb hard drive on it and now ubuntu see that its there but when i click on it to open it is says
 
unable to mount location
cant mount file.
 
so my question is how do i mount it or format it? ao i can use it as storrage.

Hmmm, what Filesystem is on there? Do you know? That's a real antique, I'd hold onto it. An IBM Desktar maybe? Anyway...

If there's no data on there your interested in recuperating then ya, I guess I'd just format it to some more modern FS (I assume it was an ol' drive from the 90's) like Ext3 or 4 and off you go writing to it.

Go to synaptic or the terminal, and install gparted. A quick search for synaptic from menu (System >Administration > Synaptic) or from the terminal (applications > Accessories > Terminal) with :

```
sudo aptitude install gparted 
```

Once installed, open it up with root power (alt + F2, then type "gksudo gparted") and then your free to format and partition as you like. A drive that size, I'd just leave one contiguous block with EXT3 or 4. If you want Windows compatibility use NTFS.

If there's data you want to preserve, I'll need more info, especially what FS is on there.

---

