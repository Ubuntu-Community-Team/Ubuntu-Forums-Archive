---
title: "ssd drives"
date: 2009-02-24
forum: Hardware
---

### Post by bobmatino17 on 2009-02-24
I was browsing around looking at the prices of ssd drives and on the description it had something to the effect of...
      DO NOT defragment this drive as it will shorten the life of the       product

Now I know i wouldnt have to worry about defragmenting because ubuntu isnt stupid enough to put a file required by another on the other side of a drive, but i was reading an issue of Linux Format and it said not to format a flash-drive with a journaling file system (like ext3/4 rfs, xfs etc.) because a flash drive cant support as many writes to one location as a hd so i formatted mine with ext2. So would this mean that it would be bad to format as ssd drive with a journaling fs?

---

### Post by ddrichardson on 2009-02-25
Journaling writes to the disk more often and SSD has a much lower number of writes than a platter drive.

The other side of the coin is that SSD has very, very good read access times but quite poor write times - so it makes sense to minimize the amount of time spent writing to disk.

---

### Post by QwUo173Hy on 2009-03-01
I've been wondering about SSD drives too lately. Would I be correct in thinking that SSD would be ideal for the kernel and maybe operating system. And use my other internal platter drives for my home folder?

---

### Post by ddrichardson on 2009-03-02
I haven't measured it to be honest and I've a SSD only system but I would say that if it is to be read but not often written too then that would be one thing.  I have seen diskless systems running from compact flash where the system is stored on CF and restored to RAM disk on boot.

The IDE/SATA drives as /home and everything else on / would probably work quite well.

---

### Post by QwUo173Hy on 2009-03-03
That sounds about right. I think I'll order a drive before the summer. I saw a nice one [here]("http://www.komplett.ie/k/ki.aspx?sku=367355"). I have a good feeling about it. :)

---

