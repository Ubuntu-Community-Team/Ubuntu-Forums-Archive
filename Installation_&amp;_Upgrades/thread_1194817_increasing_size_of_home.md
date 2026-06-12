---
title: "increasing size of /home"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by gallaharsha on 2009-06-23
Hi,

I would like to increase the size of /home folder.How do i do it? The gParteed screen shot looks like this. This is the view of the hard disk on which i have ubuntu installed. I could forgo the Movies partition . Kindly provide me with the instructions as to how to go about merging movies partition to /home as im running short of space on home 

thanks in advance

---

### Post by merlinus on 2009-06-23
You can reduce the size of /, and add that space to /home.  If you want to use sdb5's space, then a few things are required, because the space to be added has to be adjacent to the partition you are wanting to grow.

You would first have to delete /swap (it can be recreated later), delete what is now sdb5,  shrink the extended partition, format what then would be unallocated space as ext2, and add it to sdb3.  

Leave enough space in extended so you can recreate swap.

Tricky, and I would do it one step at a time, instead of all at once.

---

### Post by gallaharsha on 2009-06-23
Hi,
So i need create a gparted live cd and do the changes as you have mentioned since i cant do it running gparted within ubuntu itself. or can it be done using partition magic which i have in my windows partition.

Thanks,

---

### Post by merlinus on 2009-06-23
Use gparted live for anything linux.  THe other is commercial software made mostly for windows.

Post back if you run into difficulties.

---

### Post by gallaharsha on 2009-06-23
Hi,

I meant if the solution you have mentioned earlier(i.e merging part of root with home or the other solution of swap removal etc.) could be done from partition magic which i already have on my windows partition present in the other hard disk (As i dont have a empty cd right away to create a live cd of GParted).

Thanks.

---

### Post by merlinus on 2009-06-23
As I said, using PM can be dicey, as it was not made to work with linux.  Support for a few of the ext filesystems was added as a marketing afterthought.

Of course, you can always try it, but I would definitely back up critical data!

IIRC there is an option to burn gparted live to a usb stick, if your machine can boot from it.

---

### Post by Mark Phelps on 2009-06-23
> **gallaharsha said:**
> Hi,

I meant if the solution you have mentioned earlier(i.e merging part of root with home or the other solution of swap removal etc.) could be done from partition magic which i already have on my windows partition present in the other hard disk (As i dont have a empty cd right away to create a live cd of GParted).

Thanks.

Speaking from experience (all BAD), I can say first-hand that it's a bad idea to use MS Windows disk utilities on Linux partitions.  I've even used the very latest version of one of them and, despite it saying it worked, the ext3 partition would not boot after the operation.

What I've found ALWAYS works is using MS Windows utilities for MS Windows partitions, and using Linux utilities for Linux partitions.  Yeah, I know that may sound silly, but it's amazing how many folks come here whining about trashing their Vista partitions after running GParted against it.

---

