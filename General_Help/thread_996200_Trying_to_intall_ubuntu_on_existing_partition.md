---
title: "Trying to intall ubuntu on existing partition?"
date: 2008-11-28
forum: General Help
---

### Post by nevercroft on 2008-11-28
I have been trying to install Intrepid Ibex On an existing partition I have created. I have one small xp recovery partition,
one large xp partition, and a 10 gig partition I have set aside for ubuntu. It's ntfs and was created from shrinking my large xp partition (if that should affect anything). 

In the install menu I click manual, on the next screen I click my existing 10 gig ntfs partition but it says "no root filesystem detected." 

I am very new at partitioning and ubuntu in general, so if I am doing something blatantly wrong here, and I probably am, don't get to frustrated at me.

---

### Post by albandy on 2008-11-28
If you want to install Ubuntu in a NTFS partition you should use wubi.
Or you can delete the partition from the Ubuntu installer using manual partitioning and creating it again.

---

### Post by nevercroft on 2008-11-28
If I reformat the 10 gig partition to ext3 will I be able use it?

---

### Post by louieb on 2008-11-28
After you select the manual option click on the partition and chose edit. Make its mount point / (root) and check the format box. That should format it with the ext3 file system and install Ubuntu on it.

---

### Post by ugm6hr on 2008-11-28
> **louieb said:**
> After you select the manual option click on the partition and chose edit. Make its mount point / (root) and check the format box. That should format it with the ext3 file system and install Ubuntu on it.

You may have to shrink this 10GB partition a little more, to allow a swap partition too (approx 1.5 x RAM, up to about 700MB is reasonable if not using suspend to disk).

But yes - just select the "/" as its mountpoint, and you're good to go.

---

### Post by louieb on 2008-11-28
Thought about mentioning a swap partition. Decided to go with the KISS principle. as **ugm6hr** pointed out you will need a swap partition if you plan to hibernate.  

I'm a little stinger with swap space. 1/4 to 1/2GB is plenty. That is unless you plan to hibernate the computer, then swap needs to be a little large that the amount ram.    

> [FONT=georgia, bookman old style, palatino linotype, book antiqua, palatino, trebuchet ms, helvetica, garamond, sans-serif, arial, verdana, avante garde, century gothic, comic sans ms, times, times new roman, serif]Never be afraid to try something new.  Remember, amateurs built the ark; professionals built the Titanic.  ~Author Unknown
[/FONT]

---

### Post by ugm6hr on 2008-11-29
> **nevercroft said:**
> I am very new at partitioning and ubuntu in general, so if I am doing something blatantly wrong here, and I probably am, don't get to frustrated at me.

The simplest way to do this is actually to use Partition Editor (System -> Administration -> Partition Editor), select and delete the 10GB partition.

Then run the Install feature, and select the "Guided - Use **largest free space**" option.

Ubuntu will then create a new ext3 partition and a swap partition for you.

Nevertheless, it is useful to understand partitions if you are planning to dual-boot.

---

