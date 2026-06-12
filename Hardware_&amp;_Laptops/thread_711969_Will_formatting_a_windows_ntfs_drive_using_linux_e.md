---
title: "Will formatting a windows ntfs drive using linux erase all the info permanently?"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by tmcarson1 on 2008-03-01
If I format a windows storage drive (ntfs) using ubuntu and format it to ext3 will this make all the old windows information unrecoverable?

I am considering selling an old hard drive and was curious if this would be a way to make all my old information windows had put on the hard drive unrecoverable.

Thanks

---

### Post by sryth on 2008-03-01
For most intents and purposes.  I'm honestly not certain if dedicated data recovery professionals could get it back.  But Joe User won't.

---

### Post by justsomedude on 2008-03-01
You can use the shred command:

```
shred -v /path/to/your/storage/device
```

This will make your data unrecoverable, even for professionals.

If it is a flash device, do it several times.

---

### Post by jjordan on 2008-03-01
Nothing is ever completely non recoverable if the NSA wants it, they will get it.  But you are safe from the average Joe!

---

