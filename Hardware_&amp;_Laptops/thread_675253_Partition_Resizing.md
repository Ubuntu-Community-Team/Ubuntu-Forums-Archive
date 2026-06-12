---
title: "Partition Resizing"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by elky10 on 2008-01-22
Hello.  I'm dual-booting Ubuntu 7.10 and Vista off of my laptop.  Specifically, my laptop's internal hard drive has Vista on it, and I have a 500GB external drive split in half.  I've realized that I really don't need almost 250GB for Ubuntu, so I was hoping to find a way to shrink the Ubuntu partition and enlarge the other partition to make it bigger.  Here's my current setup:

/dev/sdb1 -- fat32 -- 232GB
/dev/sdb2 -- ext3 -- 227GB
/dev/sdb3 -- extended -- 5.79GB
--> /dev/sdb5 -- linux-swap -- 5.79GB

Basically, I want to shrink the ext3 partition down to about 50GB, and add the other 177GB or so to the fat32 partition.  The problem is, there doesn't seem to be any way to do this.  With gparted, all the partitions show up with lock symbols next to their names.  If I run the live cd and use parted, it says that I have an invalid option or something like that on /dev/sdb2.  I get a similar response trying to use partman.  I read somewhere that GNU parted can't resize an ext3 partition by changing the start point (which is what I want to do here), so I was hoping someone here could offer some advice.  Thank you!

---

### Post by logos34 on 2008-01-22
> **elky10 said:**
>  If I run the live cd and use parted, it says that I have an invalid option or something like that on /dev/sdb2.  I get a similar response trying to use partman.  I read somewhere that GNU parted can't resize an ext3 partition by changing the start point (which is what I want to do here)...

The Gparted Live CD can handle it.  Download the latest version (0.3.4).  ~53 MB.

It will take a while to resize the left boundary.

---

### Post by elky10 on 2008-01-23
Thanks for the help, you're right -- that worked.  I guess it didn't occur to me that since I was using the 7.04 Ubuntu LiveCD to run parted, it might not be updated.  Thank you!

---

### Post by logos34 on 2008-01-23
My pleasure!  

I think even the Gutsy disc is still using gparted 0.2.6 or whatever.  Way behind the curve.  

Enjoy.

---

