---
title: "Formatting a Hard Drive with Partitions"
date: 2008-10-05
forum: Hardware
---

### Post by Sebastian12 on 2008-10-05
Hi,

I want to format an internal hard drive that has Ubuntu installed on it.  It's one of two hard drives (the other with Vista).  How should I go about doing this so it'll just be an empty hard drive accessible from Vista's browser? (Don't worry - I'm installing Ubuntu on another external hard drive later)

Thanks in advance! (Even though I'll probably have to answer a bunch of other questions before this is resolved) :)

---

### Post by Sebastian12 on 2008-10-06
Bump

---

### Post by jameswhite on 2008-10-06
Now a days it is not a very hard task to format a hard disk and as well as its partitions. Simply there are many formatting softwares are easily available for this purpose. So try one of them.

[Crystal Meth](http://www.crystalrecovery.com)

James White

---

### Post by WileyHunter on 2008-10-11
Well gee JW it's so nice of you to point that out...  However, some of us don't use those functions everyday and when searching the forums for an answer to a legitimate question, it would be nice if someone making the kind of statement you made, would also post the names of such softwares or show the commands that complete the task asked about.

Now we continue the search...

WH

---

### Post by sokopok on 2008-10-11
I would use **gparted**. It has a nice easy to use interface.
Or via the terminal (**BE VERY CAREFULL** to partition the right disk!!!)
```
cfdisk /dev/device
```where /dev/device is the the disk to partition (eg. /dev/sda1)

---

### Post by Sebastian12 on 2008-10-14
One problem: I'm assuming it's not OK to format a hard drive whilst currently using the OS I'm deleting.  So I would need to enter Vista on my other hard drive... the problem is I can't see this hard drive in it's browser.

How can I access my second hard drive from Vista?

---

### Post by sokopok on 2008-10-14
If you have a bootable Ubuntu CD you can boot into the live CD and do it from there.

---

