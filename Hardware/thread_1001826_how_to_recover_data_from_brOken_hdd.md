---
title: "how to recover data from brOken hdd?"
date: 2008-12-04
forum: Hardware
---

### Post by -random on 2008-12-04
I have a hdd that reads EXTREMELY slow.

Regardless of filesystem, operating system or even a live-cd.

When the disk is in use it keeps speeding up, makes a clicking sound and is quiet again.

I'd just like to at least recover the data from my ext3 partitions before I throw it away, but how would I go about doing this?

When I use nautilus to copy 8Gb, it says 1144 hours remaining, which is loooooooooong.

Any ideas?
[
Thanks a MIL!):P):P

---

### Post by linux_tech on 2008-12-04
I would give Testdisk a try
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by -random on 2008-12-05
thnkx will dooo asap and report my results!:popcorn:

---

### Post by cariboo on 2008-12-05
You haven't really lost any data as of yet, so I don't think you want to use testdisk. I use a program called mc that is a text based file manager and more. If you used one of the text based file manager instead of nautilus, files wil be transfer a lot faster. MC is available in the repositories, you can install it from the command line:

```
sudo apt-get install mc
```

Sometimes a you have to do what it takes to backup your data.

Jim

---

