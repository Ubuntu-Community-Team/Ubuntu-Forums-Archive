---
title: "Creating a NTFS Partition on my /root drive."
date: 2008-10-14
forum: General Help
---

### Post by kpmoore on 2008-10-14
I'm running a dual boot system (just officially made the switch to Ubuntu today) and I want to keep most of my hard drive space in a NTFS file system so I can easily share files between Vista and Ubuntu.

Ubuntu is on a 400GB drive. The ext3 filesystem is 20gb, the swap partition is 8gb, and the rest in unallocated. When I try and make a new partition in the unallocated space using GParted, I see the option to make an NTFS filesystem but it is grayed-out. I realize that I can probably do it within Windows, but if Windows somehow erases my Ubuntu partition (that I have worked all day on) then I will cry.

Is there a way to do it with GParted, or should I brave the Vista Disk Management tool?

Thanks.

---

### Post by GuitarRocker2562 on 2008-10-14
why don't you make it ext3 and use ext2IFS to use it with windows?

---

### Post by schauerlich on 2008-10-14
Make sure you have ntfsprogs installed.

```
sudo apt-get install ntfsprogs
```

That should give gParted the ability to make an ntfs partition.

---

### Post by sstecken on 2008-10-14
Why is your swap 8gb?  That seems just a tad over kill.

---

