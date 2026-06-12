---
title: "[SOLVED] Free space available on new hard disk."
date: 2008-06-18
forum: Hardware
---

### Post by FooAtari on 2008-06-18
I just installed a new 1TB hard disk. I plan on copying over the contents of a 1TB external disk.

The actual usable size is 924Gb which is fair enough.  However upon formatting the disk with ext2 file system I find that 6% is used so I only have 877Gb available meaning I cant copy over the contents of the nearly full external disk as its 890Gb at the moment.

Where does the 6% get used which is free on the external disk...

---

### Post by FooAtari on 2008-06-18
Ok so I figured it out.  It was space reserved by the system.  As it's just a storage disk I don't really need it so using the -m switch on mkfs I was able to format the disk with all space available.

---

