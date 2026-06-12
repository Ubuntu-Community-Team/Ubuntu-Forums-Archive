---
title: "Partition permissions"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by bellaterror on 2006-06-20
Well Ubuntu is picking up the hard drive and in drives area I can see my main drive and the 2nd drive but I can't delete or create partition on either of them, any clue on why this is?

---

### Post by tonyr on 2006-06-20
Give some specifics, please.  Is this during installation? After installation? New drives?
Old drives with existing partitions? Using LiveCD or Alternate CD?

---

### Post by bellaterror on 2006-06-20
it's already installed not live cd and well I believe there is a windows partition on  this newly put in 2nd drive and 2 linux partitions on the first one.

---

### Post by tonyr on 2006-06-20
In a terminal (**Applications->Accessories->Terminal**) type this
```

fdisk -l

```
(that's ELL not EYE) and post the results here.

---

